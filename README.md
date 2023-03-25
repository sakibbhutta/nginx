# nginx
1.  Create a directory `/nginx`
2.  Create a `Dockerfile` in newly created directory with following content:
```console
FROM nginx
COPY ./static-html-directory/* /usr/share/nginx/html
EXPOSE 80
```
Craete a new volume `my_volume` with follwoing command:
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
3.  Now, Run the following command to generate a container on port 8080 and attach the newly craeted volume `my_volume` to the container's
directory `/usr/share/nginx/html`.
```console
$ docker run -d --name nginxweb -p 8080:80 -v my_volume:/usr/share/nginx/html nginxweb
ONTAINER ID   IMAGE      COMMAND                  CREATED         STATUS         PORTS                                   NAMES
b95133e50bc6   nginxweb   "/docker-entrypoint.…"   7 minutes ago   Up 7 minutes   0.0.0.0:8080->80/tcp, :::8080->80/tcp   nginxweb
```
4.  Now, ngnix can be browsed on  `http://localhost:8080`
5. Created a new file named "index.html" with following command, added some text and saved it:
```console
$ touch index.html
```
