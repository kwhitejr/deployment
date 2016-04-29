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

## Configure Server

Copy your IP address from Digital Ocean.

###### Create Admin User
Never run as root! Except the first time, so that we can create an 'admin' user. In the terminal, access the 'root' user. SSH into the droplet with the following command:
```
SSH root@999.999.999.999
``` 
<br>

In order to create 'admin' user:
```
useradd -m -s /bin/bash -g users -G sudo admin
```
Set login shell of new account set to `/bin/bash`, set primary group of new account to `users`, and added 'admin' user to supplementary group `sudo`.
<br>

Set password for 'admin':
```
passwd admin
```
Recommendation: use a passphrase, don't forget it.
<br>

Check your ssh key is on the server:
```
cd ~/.ssh
cat authorized_keys
```
Your ssh key should be logged in the terminal.
<br>

Change (recursively) file permissions on folder `~/.ssh` in order to secure that directory. Set the owner to `admin` and the group to `root`:
```
chown -R admin:root ~/.ssh
```
<br>

Log out of `root` user and restart as `admin`.
```
exit
SSH admin@999.999.999.999
```
<br>

Create back-up password for user `root`. You will first need to enter admin's password.
```
sudo passwd root
```
Use another passphrase. Like a boss.
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
The command `vi` opens your Virtual Inspector. Hopefully your ssh key is still saved to the clipboard! If not, open another terminal and copy it again. In order to copy into `authorized_keys` file, enter these commands:
`i` for Insert mode.
Cmd-V to paste.
`esc` to exit Insert mode.
`:wq` to write and quit.
<br>

Check whether your write-to-file worked:
```
cat ~/.ssh/authorized_keys
```
Nooice! (I hope...)
<br>


###### Install Web Server (nginx)


###### Install Run-time Environment (node.js)


