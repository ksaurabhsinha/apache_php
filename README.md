# Docker Apache with PHP

This is the Docker file for running PHP Applications on Apache, PHP & MySQL.
This installs all the pre-requisites required for running a PHP Application full-fleged.

### Using It
To use this docker file you would need to tdo the following
* Install Docker on your machine (https://www.docker.com/products/overview#)
* Clone this Repo
```sh
$ git clone https://github.com/ksaurabhsinha/apache_php.git
```
* Use the following to setup the infrastructure
```sh
$ cd apache_php
$ docker-compose up
```

### Structure
* The folder ``` 'app/' ``` will hold all the source code in php which has to be executed.
* You can change the ``` mysql ``` credentials before compsing the docker image in the file ``` docker-compose.yml ```. Consider editing these 2 lines as per your needs.
```sh
- MYSQL_ROOT_PASSWORD=root
- MYSQL_DATABASE=dbname
```
* If you tend to change the mysql configuration after running ``` docker-compose up ```, you can use the following to reflect the changes
```sh
$ docker-compose build
$ docker-compose up
```
* To ignore the cached stuff while composing
```sh
$ docker-compose up --no-cache
```
