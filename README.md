Guacamole-mysql
====

Guacamole configured with mysql authentication.

default username: guacadmin
default password: guacadmin

Mysql database stored in a persistant data container.

---
Author
===

Randy Hall <randy.hall@open-source.guru>

---
Building
===

Build from docker file:

```
git clone git@github.com:hall757/guacamole.git
cd guacamole-mysql/datavolume
docker build -t guacamole-data .
docker run -i -t --name guacamole-data guacamole-data /bin/true
cd ..
docker build -t guacamole-mysql . 
```

---
Running
===

Launch a mysql container attached to your datavolume.

```
docker run -d --name guacamole-mysqldb --volumes-from guacamole-data -e MYSQL_ROOT_PASSWORD=guacamole stackbrew/mysql
```

Now you can launch guacamole-mysql

```
docker run -d --volumes-from guacamole-data --link guacamole-mysqldb:mysql -p 8080:8080 guacamole-mysql
```

Browse to ```http://your-host-ip:8080```
Username: guacadmin
Password: guacadmin
