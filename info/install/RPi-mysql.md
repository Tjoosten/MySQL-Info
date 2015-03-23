Raspberry Pi MySQL.
===================

### Installing MySQL

If you want MySQL also do the following:

```bash
sudo apt-get install mysql-server
sudo apt-get install php5-mysql
```

The php5-mysql install adds the mysql libraries to allow PHP to access the MySQL database.

### Accessing MySQL form the command line.

First connect to the database and specify a user:

```bash
mysql -p -u root
```

Then enter the users password when prompted? You should now have a `mysql>` prompt.

### Exiting MySQL / command line login.

You can simple quit a `MySQL` prompt with the command: `quit`.

### Start / Stop / Restart mysql.

```bash
sudo service mysql start   # Start
sudo service mysql stop    # Stop
sudo service mysql restart # Restart
```

### Creating a database.

First connect to the database using `mysql -p -u root`. To create a database, type the follewing command.

```sql
CREATE DATABASE MY_DATABASE_NAME;
```
### Adding a user:

Login to mysql using `mysql -p -u root` and then create a new user to avoid using root:

```sql
CREATE USER 'MY_USERNAME'@'localhost' IDENTIFIED BY 'MY_PASSWORD';
```

## Accessing a database.

### Local Access

For security reasons, by default access to the MySQL server via the main IP address
is disabled in the MySQL config. You can connect locally using;

- `localhost`
- `127.0.0.1`
- Or the internal socket connection on `/var/run/mysqld/mysqld.sock`

### Remote access

First we need to edit the MySQL config:

```sql
sudo nano /etc/mysql/my.cnf
```

Find the configuration line called `bind-address`. By default this is set to `127.0.0.1`.

This is the local addess(es) / network adaptors that MySQl will listen for connections on. the RPi
default is `127.0.0.1` for localhost only. To allow connection on all interfaces set it to `0.0.0.0`.

Set it to `0.0.0.0` and save the file, and restart MySQL with the following command.

```bash
sudo service mysql restart
```

To grant access for a remote connection, login to mysql using `mysql -p -u root` and then create a new user to avoid using root:

```sql
CREATE USER 'MY_USERNAME'@'localhost' IDENTIFIED BY 'MY_PASSWORD';
```

To allow access from any IP address.  

```sql
GRANT ALL PRIVILEGES ON MY_DB.* TO 'MY_USERNAME'@'%' IDENTIFIED BY 'USER_PASS';
FLUSH PRIVILEGES;
```

To Allow access from a fixed IP Address:

```sql
GRANT ALL PRIVILEGES ON MY_DB.* TO 'MY_USERNAME'@'12.34.56.78' IDENTIFIED BY 'USER_PASS';
FLUSH PRIVILEGES;
```

## Further read:

 - [Recover a forgotten root password.](/blabla)
