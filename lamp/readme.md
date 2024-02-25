# DOCKER LAMP

This directory contains a Docker image for creating a LAMP development environment.

## What is contained in this Docker image??

- All features included in [php:8.1-apache](https://hub.docker.com/layers/library/php/8.1-apache/images/sha256-5d686eaf1235b1c1900dcae1199c3b42857d569a84ce2e304621e3f81a149868) image
- The following PHP modules: ```Core, ctype, curl, date, dom, fileinfo, filter, ftp, gd, hash, iconv, intl, json, libxml, mbstring, mysqli, mysqlnd, openssl, pcre, PDO, pdo_mysql, pdo_sqlite, Phar, posix, readline, Reflection, session, SimpleXML, soap, sodium, SPL, sqlite3, standard, tokenizer, xdebug, xml, xmlreader, xmlrpc, xmlwriter, xsl, Zend OPcache, zip, zlib```
- [Composer](https://getcomposer.org/)
- Virtual host configuration to access to the project through http://test.docker.com URL
- Configuration for PHP ```Xdebug``` module
- Sample PHP project

## How to install

I think you have already cloned the [repository](https://github.com/juanmacivico87/docker) containing the image, so let's go straight to the steps to create your container: 

1. Enter the *lamp* folder in the repository by running ```cd lamp``` command.
2. Replace the contents of *app* directory by the code of your PHP project.
3. Now, run ```docker build . -t lamp:latest``` to build the image you are going to use to build your container.
4. Edit the *hosts* file of your operating system and add the following line:

```
127.0.0.1 test.docker.com
::1 test.docker.com
```

5. The next step is to lift the container. To do this, run ```docker run -d -p 80:80 lamp:latest``` command. This will bind port 80 of your machine to port 80 of your container.
6. If you are in a development environment, the above command can look like this: ```docker run -d -p 80:80 -v /path/to/repository/app:/var/www/html lamp:latest``` This way, you will create a volume inside the container so that you can see the changes you make in real time in the container.

With these simple steps, you now have a LAMP environment ready to work with your PHP project.
