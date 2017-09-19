# sofar.com.ar

1. obtener los contenedores de docker hub:
```
sudo docker pull diegohsanabria/wordpress:sofar
sudo docker pull diegohsanabria/mysql:sofar
```

2. crear una red de ips para docker:
```
docker network create --subnet=172.18.0.0/16 mynet
```

3. correr docker apache-ubuntu:
```
docker run -v /var/www/Sofar/sofar:/var/www/html --net mynet --ip 172.18.0.4 -it diegohsanabria/wordpress:sofar
```

4. correr docker mysql:
```
docker run --net mynet --ip 172.18.0.5 -it diegohsanabria/mysql:sofar
```

5. crear la base de datos dentro del contenedor de mysql:
```
mysql -uroot -proot -h 172.18.0.5 < /var/www/Sofar/dumps/default/Dump20170919.sql
