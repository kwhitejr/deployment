# Deployment
Deploy to your portfolio site.

## Preparation
Obtain a domain from a reputable source: [Google Domain](https://domains.google/); [Name Cheap](https://www.namecheap.com/). Google Domains provides free private registration.

Obtain a [Digital Ocean](https://www.digitalocean.com/) account.

Create a Digital Ocean droplet.

For a basic site, choose a $5 droplet and a datacenter closest to you. Under add SSH keys, click 'New SSH Key'. Acquire your key:
```cd ~/.ssh```

View local files
```ls```

Copy ssh key to clipboard
```cat id_rsa.pub | pbcopy```

Name your ssh key.
Choose a hostname (no spaces). Make it readily identifiable.

## Configure Server

###### Create Admin User


###### Install Web Server (nginx)


###### Install Run-time Environment (node.js)


