# Setup Local Development On Windows

Step 1:  
* Install WSL 2
* Set WSL 2 as the default version

Step 2:  
* Install Ubuntu Linux Command Line tool
* Perform initial setup
* `sudo apt update`
* `sudo apt upgrade`

Step 3:  
* Install git
* `sudo apt-get install git-all`

Step 4:  
* Install php
* `sudo apt install php`

Step 5:  
* Install Composer
* Copy script from https://getcomposer.org/download/ and run in Ubuntu
* `sudo mv composer.phar /usr/local/bin/composer`

Step 6:  
* Use NVM to install node and npm
* `wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.0/install.sh | bash`
* `nvm install node`

Step 7:  
* Install MySql
* `sudo apt install mysql-server`
* `sudo service mysql start`
* `sudo mysql`
* `CREATE USER 'someuser'@'localhost' IDENTIFIED WITH mysql_native_password BY 'some_password';`
* `CREATE DATABASE some_database;`
* `GRANT ALL PRIVILEGES ON some_database.* TO 'some_user'@'localhost';`
* `exit;`
* `mysql -u some_user -p`
* `exit;`

Step 8:
* Install additional dependencies
* `sudo apt-get install php-mysql`
* `sudo apt install php-xml`
* `sudo apt install php-curl`

You are now ready to begin local laravel development!  

For a database management tool, use TablesPlus.

You can run Vite alongside the built in PHP artisan serve tool to run your webistes locally. This also allows for quick installation with Laravel breeze for vue and backend support.  

## !! One note about performance on windows: !!  
When using WSL 2, you should to store all development files within the WSL distribution file system. In this case, Ubuntu.  
Storing files in the default windows file system and accessing them via `/mnt/c/development/laravel/blah` will cause the process to be extremely slow.  

Instead serve your files from your home directory within Ubuntu, and viola! Its super quick. Example: `/home/austinb/development/laravel/blah`  

Just remember to track these files in a repository, and make backups often in case you want to get rid of Ubuntu someday. Uninsalling the program will remove this file system, which means we need to be careful.
