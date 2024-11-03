#### How to Install & Configuration ISPConfig 3 on Ubuntu

In this article,I will show you how to install ISPConfig 3 on Ubuntu as well as go through the initial configuration.

ISPConfig is a fast reliable control panel for managing a Linux Virtual Private Server (VPS). It is an open-source program allow you to manage services through a web browser. ISPConfig allows hosting multiple domains in a single server with the Apache and Nginx web server. You can manage websites, email addresses, FTP accounts, DNS records, databases and much more featured.


#### Requirement:

1. Ubuntu And Debian Vps
2. Memory – 2GB, recommended 4 GB.
3. CPU – 2-core CPU or 2 vCPUs.
4. Storage space – 10 GB of free hard disk space.
5. DNS Records – FQDN with MX and A DNS-records

#### Chnage hostname:
    nano /etc/hostname

#### Configure the hostname and hosts
    nano /etc/hosts


#### Need Reboot
    systemctl reboot

#### Check hostname with fqdn
    hostname -f

#### Update your system packages before installations
    apt update && apt upgrade

#### Reboot Again

    systemctl reboot

#### Install screen for terminal multiplexer
```
apt install screen
screen --version
screen -S ispconfig
screen -ls
```
#### Restore the terminal screen
    screen -r 
or
    screen -r 10835 or session name
#### Exit from terminal screen
    exit

#### Run the ISPConfig autoinstaller

    wget -O - https://get.ispconfig.org | sh -s -- --help

#### When get error for php-mbstring
    sudo apt install php-mbstring
    wget -O - https://get.ispconfig.org | sh -s -- --use-ftp-ports=40110-40210 --unattended-upgrades


#### Type 'yes' if you really want to continue: yes

#### Take some times:

#### When the installer is finished it will show you the ISPConfig admin and MySQL root password. The this genarated automatically. 

#[INFO] Your ISPConfig admin password is: ubuntu

#[INFO] Your MySQL root password is: ubuntu

#ISPConfig 3 Installation Is Done.


#### ISPConfig Login:-

https://server_IP_address:8080/

User = admin

pass = ubuntu

#### After first login to Setting up the firewall

#### Log in to the ISPConfig UI, and go to System -> Firewall. Then click "Add new firewall record".

TCP:

20,21,22,25,80,443,40110:40210,110,143,465,587,993,995,53,8080,8081

UDP:

53

#
#### Troubleshooting
#### How to reset the administrator password in ISPConfig

#### Login to the mysql database.

    mysql -u root -p

#### Then enter the password of the mysql root user. To switch to the ISPConfig database, run this command:

    use dbispconfig;

#### And execute the SQL command:

    UPDATE sys_user SET passwort = md5('admin') WHERE username = 'admin';

#### Finally close the mysql shell:

    quit;

End Troubleshooting
#
#### Reference: 
1. https://vkttech.com/how-to-install-ispconfig-3-on-debian-10-11-and-ubuntu-20-04/ (Following)
2. https://www.howtoforge.com/ispconfig-autoinstall-debian-ubuntu/ (official)
3. https://computingforgeeks.com/install-configure-ispconfig-control-panel-on-ubuntu/ (following)
4. https://www.youtube.com/watch?v=euFFSuX9-VY&list=PLT59sMA4iPM9Kdc_lwvY633L-CPTE8zsA (following)
#
