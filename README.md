# Deployment
Deploy to your portfolio site.

## Preparation
Obtain a domain from a reputable source: [Google Domain](https://domains.google/); [Name Cheap](https://www.namecheap.com/). Google Domains provides free private registration.

Obtain a [Digital Ocean](https://www.digitalocean.com/) account.

Create a Digital Ocean droplet.

For a basic site, choose a $5 droplet and a datacenter closest to you. Under add SSH keys, click 'New SSH Key'. Acquire your key:
```cd ~/.ssh```

Check local files
```ls ```

Copy ssh key to clipboard:
```cat id_rsa.pub | pbcopy```
Read the file and pipe it to `pbcopy`, which is the clipboard.

Name your ssh key.
Choose a hostname (no spaces). Make it readily identifiable.

## Configure Server

Copy your IP address from Digital Ocean.

###### Create Admin User
Never run as root! Except the first time, so that we can create an 'admin' user. In the terminal, access the 'root' user. SSH into the droplet with the following command:
```SSH root@999.999.999.999``` 

In order to create 'admin' user:
```useradd -m -s /bin/bash -g users -G sudo admin```
Set login shell of new account set to `/bin/bash`, set primary group of new account to `users`, and added 'admin' user to supplementary group `sudo`.

Set password for 'admin':

```passwd admin```

Recommendation: use a passphrase, don't forget it.

Check your ssh key is on the server:

```cd ~/.ssh```

```cat authorized_keys```

Your ssh key should be logged in the terminal.



###### Install Web Server (nginx)


###### Install Run-time Environment (node.js)


