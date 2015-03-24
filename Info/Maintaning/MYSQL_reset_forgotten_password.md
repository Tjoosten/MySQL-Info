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
sudo service mysql stop       # RPi: Debian
```
