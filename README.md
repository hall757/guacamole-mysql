Guacamole-mysql
====

Guacamole configured with mysql authentication.

default username: guacadmin

default password: guacadmin

guacd runs from a separate container.

Mysql database stored in a persistant data container.  Be sure to protect it from being erased.

---
Author
===

Randy Hall <randy.hall@open-source.guru>

---
Building
===

Build from docker file:

```
git clone git@github.com:hall757/guacamole-mysql.git
cd guacamole-mysql/datavolume
docker build -t hall/guacamole-data .
docker run -i -t --name guacamole-data hall/guacamole-data /bin/true
cd ..
docker build -t hall/guacamole-mysql . 
```

---
Running
===

Launch a mysql container attached to your datavolume and the guacamole daemon.

```
docker run -d --name guacamole-mysqldb --volumes-from guacamole-data -e MYSQL_ROOT_PASSWORD=guacamole stackbrew/mysql
docker run -d --name guacamole-guacd hall/guacamole-guacd
```

Now you can launch guacamole-mysql

```
docker run -d --link guacamole-mysqldb:mysql --link guacamole-guacd:guacd -p 8080:8080 hall/guacamole-mysql
```

Browse to ```http://your-host-ip:8080```

Username: guacadmin

Password: guacadmin
