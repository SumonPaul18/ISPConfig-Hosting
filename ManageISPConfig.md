#### ISPConfig Credential:

ISPConfig admin password is: Ubuntu@1234

ISPConfig MySQL root password is: shzd7rK1skzvCw2ZewUA

#
#### How to reset the administrator password in ISPConfig

#### Login to the mysql database.

    mysql -u root -p

#### Then enter the password of the mysql root user. To switch to the ISPConfig database, run this command:

    use dbispconfig;

#### And execute the SQL command:

    UPDATE sys_user SET passwort = md5('admin') WHERE username = 'admin';

#### Finally close the mysql shell:

    quit;

#
