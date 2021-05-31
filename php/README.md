# Table of contents

- [Installation in macOS](#installation-in-macos)
- [pear and pecl](#pear-and-pecl)
- [Auto update](#auto-update)
- [PHP Configuration (php.ini)](#php-configuration-(php.ini))
- [Install Xdebug](#install-xdebug)



### Installation in macOS

PHP can be installed in macOS using **homebrew**. To install php, run:

`brew install php72`

To enable PHP in Apache add the following to httpd.conf and restart Apache:
    LoadModule php7_module /usr/local/opt/php@7.2/lib/httpd/modules/libphp7.so

    <FilesMatch \.php$>
        SetHandler application/x-httpd-php
    </FilesMatch>

Finally, check DirectoryIndex includes index.php
    DirectoryIndex index.php index.html

The php.ini and php-fpm.ini file can be found in:
    /usr/local/etc/php/7.2/

php@7.2 is keg-only, which means it was not symlinked into /usr/local,
because this is an alternate version of another formula.

If you need to have php@7.2 first in your PATH, run:
  echo 'export PATH="/usr/local/opt/php@7.2/bin:$PATH"' >> /Users/username/.bash_profile
  echo 'export PATH="/usr/local/opt/php@7.2/sbin:$PATH"' >> /Users/username/.bash_profile

For compilers to find php@7.2 you may need to set:
  export LDFLAGS="-L/usr/local/opt/php@7.2/lib"
  export CPPFLAGS="-I/usr/local/opt/php@7.2/include"

To have launchd start php@7.2 now and restart at login:
  brew services start php@7.2
Or, if you don't want/need a background service you can just run:
  php-fpm

### pear and pecl

`pecl` and `pear` are provided with Homebrew's version of PHP

### Auto update

By default **homebrew** will auto-update PHP when you run `brew install` command. To disable this behaviour, add this to your **.bash_profile**

`HOMEBREW_NO_AUTO_UPDATE=1`

### PHP Configuration (php.ini)

The **php.ini** file is a special file for PHP. It is where you declare  changes to your PHP settings. The server is already configured with  standard settings for PHP, which your application will use by default. Unless  you need to change one or more settings, there is no need to create or  modify a php.ini file. 

You can find your local **php.ini** file by running this command in terminal:

`php --ini`

The command will return following response:

*Configuration File (php.ini) Path: /usr/local/etc/php/7.2*
***Loaded Configuration File:         /usr/local/etc/php/7.2/php.ini***
*Scan for additional .ini files in: /usr/local/etc/php/7.2/conf.d*
*Additional .ini files parsed:      /usr/local/etc/php/7.2/conf.d/error_log.ini,*
*/usr/local/etc/php/7.2/conf.d/ext-opcache.ini,*
*/usr/local/etc/php/7.2/conf.d/php-memory-limits.ini*

You need to edit **/usr/local/etc/php/7.2/php.ini** in order to modify your settings.

### Install Xdebug

You can install Xdebug through PECL macOS with Homebrew. Run: 

`pecl install xdebug`

Command result:

*Build process completed successfully*
*Installing '/usr/local/Cellar/php@7.2/7.2.34_4/pecl/20170718/xdebug.so'*
*install ok: channel://pecl.php.net/xdebug-3.0.4*
*Extension xdebug enabled in php.ini*

After successfull installation of Xdebug, in order to verify installation, run:

`php -v`

Command result:

*PHP* 7.2.34 (cli) (built: May 14 2021 14:25:49) ( NTS )*
*Copyright (c) 1997-2018 The PHP Group*
*Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies*
    ***with Xdebug v3.0.4, Copyright (c) 2002-2021, by Derick Rethans***
    with Zend OPcache v7.2.34, Copyright (c) 1999-2018, by Zend Technologies*

The command result should include Xdebug.

### Install composer



