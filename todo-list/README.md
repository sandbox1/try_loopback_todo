# Try Loopback 4 todo-list

[![LoopBack](https://github.com/strongloop/loopback-next/raw/master/docs/site/imgs/branding/Powered-by-LoopBack-Badge-(blue)-@2x.png)](http://loopback.io/)


# Database Setup

Setup postgres for use as the datasource.

```
sudo su - postgres
createdb try_todo
createuser -P try_todo_owner
```

Then start postgres using `psql` and execute the following queries at
the `postgres=#` prompt:

```
GRANT ALL PRIVILEGES ON DATABASE try_todo TO try_todo_owner;
```
```
ALTER USER try_todo_owner CREATEDB;
```


Use `\q `to exit postgres.  

Use `<Ctrl+D>`  or `exit` to get back to the normal user.

You will also need to ensure that the postgresql server is listening
on all IPs, Open (with `sudo nano`, for example)
`/etc/postgresql/*/main/postgresql.conf` and change the line
beginning

```
#listen_addresses = 'localhost'
```

to

```
listen_addresses = '*'
```

You will also need to edit the `/etc/postgresql/*/main/pg_hba.conf` file, adding the following lines:

```
# allow connections from local subnet
host    all             all             10.250.1.0/24            md5
```

The database should be correctly set up on reboot, but if you want, you can restart the service now:

```
sudo service postgresql restart

or

/etc/init.d/postgresql restart
```
