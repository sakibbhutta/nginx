# Task 3

## nginx
1.  Craete a new volume `my_volume` with follwoing command:
```console
$ docker volume create my_volume
$ docker volume ls
DRIVER    VOLUME NAME
local     lab2_db_data
local     lab2_wp_data
local     lab3_portainer_data
local     lab5_db_data
local     lab5_nc_data
local     my_volume
```
2.  Create a file `index.html` in newly created `my_volume` in directory `/var/lib/docker/volume/my_volume` with following content:
```console
<!doctype html>
<html lang="en">
<head>

<p>Nginx with Docker Compose</p>


</head>
<body>

<h2>this is my customised docker file</h2>
<p>This content is being served by an Nginx Docker container.</p>
</body>
</html>
```
3.  Now, create a directory `/nginx1`
4.  Create a `docker-compose.yml` in newly created directory with following content:
```yml
version: '3'
services:
  web:
   image: nginx:latest
   ports:
   - "8080:80"
   volumes:
   - /var/lib/docker/volumes/my_volume:/usr/share/nginx/html
```

5.  Now, Run the following command to run yml file`.
```console
$ docker-compose up -d
```
6.  Now, ngnix can be browsed on  `http://localhost:8080`
____________________________________________________________________________________________
____________________________________________________________________________________________
7. Create a file `index.html` in home directory with following content
```console
  GNU nano 6.2                                                      index.html                                                               
<!doctype html>
<html lang="en">
<head>

<p>Nginx with Docker Compose</p>


</head>
<body>

<h2>this is my customised docker file</h2>
<p>This is newly created file which is copied.</p>
</body>
</html>
```
8.  now. copy the newly created file to `my_volume` with is attaced with running container with following command:
```console
$ sudo cp -p . /var/lib/docker/volumes/my_named_volume/_data/
```
9. Refresh the page on `localhost:8080`
(showing the content of updated/copied file)
