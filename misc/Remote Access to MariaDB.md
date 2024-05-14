To install MariaDB, simply run the commands below:

sudo apt update
sudo apt install mariadb-server mariadb-client

After installing MariaDB, the commands below can be used to stop, start, and enable the MariaDB service to always start up when the server boots…

**Run these on Ubuntu 18.04 LTS**

sudo systemctl stop mariadb.service
sudo systemctl start mariadb.service
sudo systemctl enable mariadb.service

Next, run the commands below to secure the database server with a root password if you were not prompted to do so during the installation…

sudo mysql_secure_installation

When prompted, answer the questions below by following the guide.

- Enter current password for root (enter for none): Just press the Enter
- Set root password? [Y/n]: Y
- New password: Enter password
- Re-enter new password: Repeat password
- Remove anonymous users? [Y/n]: Y
- Disallow root login remotely? [Y/n]: Y
- Remove test database and access to it? [Y/n]:  Y
- Reload privilege tables now? [Y/n]:  Y

Now that MariaDB is installed, to test whether the database server was successfully installed, run the commands below…

sudo mysql -u root -p

Type the root password when prompted…

![mariadb welcome](https://i0.wp.com/geekrewind.com/wp-content/uploads/2018/01/mariadb_ubuntu_1604.webp?resize=658%2C240&ssl=1)

If you see a similar screen as shown above, then the server was successfully installed…

#### Configure MariaDB Remote Access

As mentioned above, all remote access to the server is denied by default. To enable remote access, you’ll need to set the bind address to allow for remote access.

For example, to allow all **IPv4** addresses, set the bind address to 0.0.0.0. This will allow the MariaDB server to accept connections on all host IPv4 interfaces. If you have IPv6 configured on your system, use::

On Ubuntu systems with a MariaDB database server installed, its default configuration file is located at**/etc/mysql/mariadb.conf.d/50-server.cnf**

Simply run the commands below to open the MariaDB configuration file.

sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf

Depending on your systems, you may find that same configuration file may be at the location below:

sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

When the file is opened, search for a line that begins with **bind-address,** as shown below. Its default value should be **127.0.0.1**.

# this is read by the standalone daemon and embedded servers
# this is only for the mysqld standalone daemon
**[mysqld]**

#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
lc-messages-dir = /usr/share/mysql
skip-external-locking

# Instead of skip-networking the default is now to listen only on

# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1

#
# * Fine Tuning

What you need to do is change the default value 127.0.0.1 to **0.0.0.0,** as shown below:

# this is read by the standalone daemon and embedded servers

# this is only for the mysqld standalone daemon
**[mysqld]**

#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
lc-messages-dir = /usr/share/mysql
skip-external-locking

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 0.0.0.0

#
# * Fine Tuning

In the same file, you’ll want to comment out the line that begins with skip-networking by putting the # before it. Or delete it together. Then save your changes.

Please add the changes above under the **[mysqld]** section.

After making the change above, save the file and run the commands below to restart the server.

sudo systemctl restart mariadb.service

To verify that the change happens, run the commands below.

sudo apt install net-tools
sudo netstat -anp | grep 3306

, and you should find the result that looks like the one below

tcp       0      0 0.0.0.0:3306          0.0.0.0:*        LISTEN         3213/mysqld

Now, the server is set up to listen to all IP addresses, but individual IP needs to be explicitly configured to connect to a database.

You must grant access to the remote server to enable a client to connect to a database.

#### Access from Remote Clients

Now that the server is configured. Use the steps below to allow remote clients to access the database.

For example, if you wish for a client computer with IP address **192.168.1.2** to connect to a database called **database_name** as user **database_user**, run the commands below after logging onto the database server.

GRANT ALL ON **database_name**.* TO '**database_user**@192.168.1.2' IDENTIFIED BY '**database_user_password**';

- **database_name** is the name of the database that the user will connect to.
- **database_user** is the name of the database user.
- **192.168.1.2** is the IP from which the client is connecting.
- database_user_password is the password of the database_user account

After running the commands above, you can access the server from the client computer with that assigned IP.

To connect to the server from the approved IP address, run the commands below

mysql -u **database_user** -p **database_user_password** -h **database_server**

That’s it! You’ve successfully configured remote access to the MariaDB database server.

#### Ubuntu Firewall

If your Ubuntu server has a firewall enabled, you will want to open a connection to the database server. Simply run the commands below to open the firewall to the client from the IP address to the port only.

For example, to open the Ubuntu Firewall, allow the IP address **192.168.1.2** to connect to port 3306.

sudo ufw allow from 192.168.1.2 to any port 3306

To allow all IP addresses (not secure), then run the commands below:

sudo ufw allow 3306/tcp

That’s it!