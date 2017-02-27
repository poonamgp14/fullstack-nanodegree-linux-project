rdb-fullstack
=============

Complete URL: http://54.84.151.66
SSH port: 2200
IP address: 54.84.151.66

### Update all currently installed packages
- sudo apt-get update
- sudo apt-get upgrade
- sudo apt-get autoremove

### changed the port using following commands:
- sudo nano /etc/ssh/sshd_config
- Changed the port number here from 22 to 2200
# What ports, IPs and protocols we listen for
Port 50683
- Restated ssh
sudo /etc/init.d/ssh restart

### Configuring firewalls
- Blocks every incoming request - sudo ufw default deny incoming
- Allow every outgoing call from server - sudo ufw default allow outgoing
- Allow ssh request - sudo ufw ssh
- Allow http request - sudo ufw allow www
- Allow NTP on port 123 - sudo ufw allow ntp
- Now enable firewll using sudo ufw enable
- Disallowed SSH login for root user by
sudo nano /etc/ssh/sshd_config and change from
PermitRootLogin yes to
PermitRootLogin no


### Add user grader
- sudo adduser grader
- Using ssh-key gen, generated public and private key on terminal locally
- Copied public key from local folder to the /home/ubuntu/authorized_keys using scp command
- Made .ssh directory using sudo -u grader mkdir /home/grader/.ssh
- Copied to .ssh dir using sudo -u grader cp /home/ubuntu/authorized_keys /home/grader/.ssh/
- Local time zone is by default is UTC


###Few points to remember:
- Followed the link to Install and configure Apache to serve a Python mod_wsgi application: https://www.digitalocean.com/community/tutorials/installing-mod_wsgi-on-ubuntu-12-04
- Followed link to Install and configure PostgreSQL:
https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-16-04 and

https://help.ubuntu.com/community/PostgreSQL#Basic_Server_Setup

- Cloned and setup your Item Catalog project from the Github repository

###Installed following puthon modules:
sudo pip install Flask-SQLAlchemy

sudo apt-get install libpq-dev
sudo pip install psycopg2
sudo sudo pip install requests
sudo pip install --upgrade google-api-python-client

###Disabled the directory listing with webserver apache2 by editing /etc/apache2/apache2.conf from

<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>

to

<Directory /var/www/>
        Options FollowSymLinks
        AllowOverride None
        Require all granted
</Directory>
then restart apache by:

sudo service apache2 restart

