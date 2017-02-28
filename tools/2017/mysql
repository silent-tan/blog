## Install MySQL on macOS Sierra (转)
This procedure explains how to install [MySQL](https://www.mysql.com) using [Homebrew](http://brew.sh) on macOS Sierra 10.12

### Install Homebrew
* Installing Homebrew is effortless, open Terminal and enter :  
 `$  /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
* **Note:** Homebrew will download and install Command Line Tools for Xcode 8.0 as part of the installation process.

### Install MySQL
At this time of writing, Homebrew has MySQL version **5.7.15** as default formulae in its main repository :

* Enter the following command : `$ brew info mysql`  
* Expected output: **mysql: stable 5.7.15 (bottled)**

To install MySQL enter : `$ brew install mysql`
  

## Additional configuration
### Homebrew

* Install **brew services** first : `$ brew tap homebrew/services`
* Load and start the MySQL service : `$ brew services start mysql`.   
Expected output : **Successfully started `mysql` (label: homebrew.mxcl.mysql)** 	  

* Check of the MySQL service has been loaded : `$ brew services list` <sup>[1](#1)</sup>

* Verify the installed MySQL instance : `$ mysql -V`.   
Expected output : **Ver 14.14 Distrib 5.7.15, for osx10.12 (x86_64)**  


### MySQL
Open Terminal and execute the following command to set the root password:  
 `mysqladmin -u root password 'yourpassword'`  

> **Important** : Use the single ‘quotes’ to surround the password and make sure to select a strong password! 

###Database Management
To manage your databases, I recommend using [Sequel Pro](http://www.sequelpro.com), a MySQL management tool designed for macOS.   
Current version available: **1.1.2**


#####Comments
<a name="1"><sup>1</sup></a> The `brew services start mysql` - instruction is equal to :   

```
$ ln -sfv /usr/local/opt/mysql/*.plist ~/Library/LaunchAgents
$ launchctl load ~/Library/LaunchAgents/homebrew.mxcl.mysql.plist
```

### Using mysql
