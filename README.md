# docker-cakephp3-template

By using Docker-Compose, you can build CakePHP3 environment easily.

# Environment

* Docker 18.06.1-ce
* Docker Compose 1.22.0
* Docker Machine 0.15.0

## Initialization (Build CakePHP3 Project)
Since CakePHP3 has an execution environment for each project, so create a project. To create another project, follow the same procedure.

### Create Docker Images
It will take about two or three minutes.

```
$ docker-compose build
```

### Run Containers 

```
$ docker-compose up -d
```

### Enter PHP-FPM Container

```
$ docker exec -it docker-cakephp_phpfpm_1 /bin/sh
```


### Get Composer Installer

```
/var/www/html # curl -s https://getcomposer.org/installer | php
```

### Make Project
Here, create a `sample` project

```
/var/www/html # php composer.phar create-project --prefer-dist cakephp/app sample

```

### Exit Container

```
/var/www/html # exit
```

### Fix Configuration about db
Update `data/htdocs/sample/config/app.php` at line 251

```data/htdocs/sample/config/app.php
-   'host' => 'localhost',
+   'host' => 'mysql',
```

### Fix Configuration about app name
Update `docker-compose.yml` at line 43
```
-      PRJ: "sample"
+      PRJ: "<your app name>"
```

## Build Up

```
$ docker-compose up -d
```

You can check at http://localhost:8765


## Remove Containers

```
$ docker-compose down 
```


