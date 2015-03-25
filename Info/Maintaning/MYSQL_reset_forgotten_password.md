Resetting a lost MySQL root password.
=========================================

The MySQL root password allows full access to the MySQL database and allows for all actions to be undertaken including creating
new users, new databases, setting access rules and so on.

Losing one can be a difficult issue to encouter. Luckily, resetting the root password is easy as long as you have `sudo` access to the server.

### Not the Server root user.

A common issue is confusing: the Server root user with the MySQL root user.

The Server root user is the server's main user. The MySQL root user has complete control over MySQL only.
The two `root` users are not connected in any way.

### Stop the MySQL server.

The first thing to do is stop MySQL.

```bash
sudo /etc/init.d/mysql stop   # Computer: Ubuntu, Debian.
sudo /etc/init.d/mysqld stop  # Computer: CentOS, Fedura, RHEL.
sudo service mysql stop       # RPi: Debian.
```

### Safe mode.

Next we need to start MySQL in safe mode - that is to say, we will start MySQL but skip the user privileges table.
Again, note that you will need to have `sudo` access for those commands so you don't need to worry about any user being able to reset
the MySQL root password:

```bash
sudo mysqld_safe --skip-grant-tables &
```

**NOTE:** The ampersand (`&`) at the end of the command is required.

### Login

All we need to do now is to log into MySQL and set the password.

```bash
mysql -u root
```

**NOTE:** No password is required at this stage as when we started MySQL we skipped the user privileges table.

Newt, instruct MySQL which table database to user:

```sql
use mysql;
```

### Reset password.

Enter the new password for the root user as follows:

```sql
update user set password=PASSWORD("mynewpassword") where User='root';
```

And finally fliush the privileges;

```sql
flush privileges;
``` 
