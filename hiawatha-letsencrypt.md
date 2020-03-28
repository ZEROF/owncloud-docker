**Hiawatha web server with Letsencrypt**

Hugo, developer of Hiawatha wrote script to help us to use letsencrypt with Hiawatha. This script is PHP7 based, and because of that we need to install PHP7 (in period of writing this documentation on Debian 10, we have PHP7.3).

On just installed Debian 10 server we need to install PHP7 and few modules.

```sudo apt install php7 php7.3-cli php7.3-common php7.3-curl php7.3-gd php7.3-json php7.3-mbstring php7.3-mysql php7.3-xml```

Then move to super user session and get last script version from repository:

```sudo su && sudo -s```
```wget https://www.hiawatha-webserver.org/files/letsencrypt-2.1.tar.gz```

After this setting Letsecrypt must be done from root directory and reading INSTALL file well and follow instructions.

As well we need to create tls folder where all certificates we create will be send, to do that:

```mkdir /etc/hiawatha/tls```

**Auto renew certificates**

This is work in progress, because we didn't found a lot information about it. What we will try to use script made by Hugo and set crone job to renew certificates before their experience.

As super user (sudo -s), we need to set crone job:

```crontab -e```

  and we add this line

```@weekly pidof hiawatha && /usr/local/letsencrypt/letsencrypt renew restart >> /var/log/weekly.log 2>&1```
