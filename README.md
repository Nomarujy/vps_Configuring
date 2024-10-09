# Guide for configuring vps server for nginx web server

## First initial
1. coonect to ssh by command and login.
   ```
   ssh root@VPS_IP
   ```
  
2. Update and install packages
   ```
   sudo apt-get update ; sudo apt-get upgrade
   ```
   ```
   sudo apt-get install git nginx certbot python3-certbot-nginx && sudo systemctl enable nginx
   ```
3. Creating "www' user and give permisions
  * creating "www" user 
   ```
   sudo adduser www
   ```
  * give permision to use sudo and docker witout sudo
   ```
   sudo usermod -aG sudo www ; sudo groupadd docker ; sudo usermod -aG docker www
   ```
  * and login to "www" user
   ```
   su www
   ```

4. Configuring ssh
  * Generating ssh key in lical machine:
     ```
     ssh-keygen
     ```
  * Create dir for ssh keys and create authorized_keys
     ```
     sudo mkdir -p ~/.ssh ; sudo nano ~/.ssh/authorized_keys
     ```
  * Write pub ssh key to file and save file

  * Open ssh config file
     ```
     sudo nano /etc/ssh/sshd_config
     ```
  * Change default ssh settings to
     `Port 49152 - 65535`
     `PermitRootLogin no`
     `PasswordAuthentication no`
  * After changes save file
  * Before reload check all configuration files in "/etc/ssh/sshd_config.d/"
  * Cause in this configiratuin may overide values
     ```
     sudo nano /etc/ssh/sshd_config ; li
     ```
  * reload ssh
     ```
     sudo service ssh restart
     ```
5. Configuring nginx
     ```
     sudo nano /etc/nginx/nginx.conf
     ```
     ```
     sudo nano /etc/nginx/nginx.conf/sites-avalible/default
     ```
    * after get certificates from certbot
       ```
       sudo certbot --nginx
       ```
