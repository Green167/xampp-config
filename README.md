# xampp-config NEW
- Download xampp 7.4.xx.
- Copy folder php.
- Uninstall
- Download xampp newest.
- Rename the current PHP folder to php8xx
- Copy folder php to current xampp.
- Change httpd-xampp.conf:
 ```
 LoadFile "D:/xampp/php/php7ts.dll"
LoadFile "D:/xampp/php/libpq.dll"
LoadFile "D:/xampp/php/libsqlite3.dll"
LoadModule php7_module "D:/xampp/php/php7apache2_4.dll"

...

<IfModule php7_module>
    PHPINIDir "D:/xampp/php"
</IfModule>
```

# xampp-config OLD

**mysqli undefined:**
- Change php.ini:
        extension_dir = "D:\xampp\php7429\ext"

**https://serverfault.com/questions/66347/why-is-the-response-on-localhost-so-slow/607536#607536**

1. Load PHP as an Apache MODULE INSTEAD OF cgi

- insert following lines into httpd.conf

        LoadModule php5_module "c:/php/php5apache2.dll"

        AddHandler application/x-httpd-php .php

        (p.s. change C:/php to your path. Also, change php5apache**.dll to your existing file name)

- To limit PHP execution only for .php files, add this in httpd.conf:

        <FilesMatch \.php$>
                SetHandler application/x-httpd-php 
        </FilesMatch>

- set path of php.ini in httpd.conf (if after restart you get error, then remove this line again)

        PHPIniDir "C:/php"

- Disable #LoadModule cgi_module modules/mod_cgi.so in httpd.conf
