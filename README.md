# Deployment
Deploy to your portfolio site.

## Preparation
Obtain a domain from a reputable source: [Google Domain](https://domains.google/); [Name Cheap](https://www.namecheap.com/). Google Domains provides free private registration.

Obtain a [Digital Ocean](https://www.digitalocean.com/) account.

Create a Digital Ocean droplet.

For a basic site, choose a $5 droplet and a datacenter closest to you. Under add SSH keys, click 'New SSH Key'. Acquire your key:
```
cd ~/.ssh
```

Check local files
```
ls
```
<br>

Copy ssh key to clipboard:
```
cat id_rsa.pub | pbcopy
```
Read the file and pipe it to `pbcopy`, which is the clipboard.
<br>

Name your ssh key.
Choose a hostname (no spaces). Make it readily identifiable.
<br>

## Configure Server

Copy your IP address from Digital Ocean.

Never run as root! Except the first time, so that we can create an 'admin' user. In the terminal, access the 'root' user. SSH into the droplet with the following command:
```
SSH root@999.999.999.999
``` 
<br>
<br>
In order to create 'admin' user:
```
useradd -m -s /bin/bash -g users -G sudo admin
```
Set login shell of new account set to `/bin/bash`, set primary group of new account to `users`, and added 'admin' user to supplementary group `sudo`.
<br>
<br>
Set password for 'admin':
```
passwd admin
```
Recommendation: use a passphrase, don't forget it.
<br>
<br>
Check your ssh key is on the server:
```
cd ~/.ssh
cat authorized_keys
```
Your ssh key should be logged in the terminal.
<br>
<br>
Change (recursively) file permissions on folder `~/.ssh` in order to secure that directory. Set the owner to `admin` and the group to `root`:
```
chown -R admin:root ~/.ssh
```
<br>
<br>
Log out of `root` user and restart as `admin`.
```
exit
SSH admin@999.999.999.999
```
<br>
<br>
Create back-up password for user `root`. You will first need to enter admin's password.
```
sudo passwd root
```
Use another passphrase. Like a boss.
<br>
<br>
Look at your admin's `~/.ssh` folder:
```
ls -lah ~/.ssh
```
HA! You don't have one. Let's create it and put your ssh key in it.
```
mkdir ~/.ssh
vi ~/.ssh/authorized_keys
```
<br>
The command `vi` opens your Virtual Inspector. Hopefully your ssh key is still saved to the clipboard! If not, open another terminal and copy it again. In order to copy into `authorized_keys` file, enter these commands:
`i` for Insert mode.
Cmd-V to paste.
`esc` to exit Insert mode.
`:wq` to write and quit.
<br>
<br>
Check whether your write-to-file worked:
```
cat ~/.ssh/authorized_keys
```
Nooice! (I hope...)
<br>
<br>
Set the folder permissions on `~/.ssh` to 700. 700 means read, write and execute for the owner of the file/folder only (zeroes for group and others). Each number represents... Just remember "UGO": user, group, other.
```
chmod 700 ~/.ssh
```
Check the permissions. From the directory containing `.ssh`:
```
ls -lah
```

Exit and check whether you can log in without a password (super haxxor skillz):
```
exit
SSH admin@999.999.999.999
```

## Install Web Server (nginx)
Update server:
```
sudo apt-get update
```

Install nginx:
```
sudo apt-get install nginx
```
Check whether you done did it correctly by opening your IP address in browser.


## Install Run-time Environment (node.js)

Install node.js. This is your server's run-time environment.
```
sudo apt-get install nodejs
```

Install npm
```
sudo apt-get install npm
```

Install nvm (node verson manager) for multiple versions of node or n if you have a single version of node on the server. Let's use n for now. Then get the latest stable version of node.
```
sudo npm i -g n
sudo n stable
```

Install git-core
```
sudo apt-get install git-core
```

## Add Your Project
Cool. From the admin's root directory (`cd ~`), make an `apps` folder to where you can clone projects.
```
mkdir apps
```

Clone down your repo:
```
git clone https-key-here
```

Create a symbolic link from "project-name" to "repo-name".
```
sudo ln -s ~/apps/repo-name/ /srv/project-name
```

Check the link.
```
ls -lah /srv
```




