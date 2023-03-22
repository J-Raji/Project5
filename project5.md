#IMPLEMENTATION OF CLIENT SERVER ARCHITECTURE USING MYSQL DATABASE MANAGEMENT SYSTEM (PROJECT 5)

1.a Create MySql Server

(http://ec2-54-89-205-122.compute-1.amazonaws.com)

![MySql Server Instance](./Images/msqr.png)

`sudo apt install apache2`

b Create MySql Client

(http://ec2-18-234-102-46.compute-1.amazonaws.com)

![MySql Client Instance](./Images/mclt.png)

`sudo apt install apache2`

2. In 1.a install Mysql Server

`sudo apt install mysql-server`

![Installed apache2 and mysql server](./Images/ms.png)

3. In 1.b install Mysql Client

`sudo apt install mysql-client`

![Installed apache2 and mysql client](./Images/mc.png)

4. Create Inbound rule security Group with TCP port 3306 in Mysql Server

b connect mysql client on mysql server

![Inbound rule addedd for TCP Port 3306](./Images/port.png)

-`sudo mysql_secure_installation`
OPEN MYSQL utility
`sudo mysql`
CREATE USER 'remote_user'@'% IDENTIFIED WITH mysql_native_passowrd BY 'password';

![User Created](./Images/user.png)

CREATE DATABASE test-db;

![Db Created](./Images/db.png)

GRANT ALL ON test_db.* To 'remot_user'@'%'WITH GRANT OPTION;

![Grant all to db](./Images/grant.png)

FLUSH PRIVILEGEs;

![Flush privileges](./Images/flush.png)
exit;

5. Configure MySQL server to allow connections from remote hosts

`sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf`

![/mysqld.cnf](./Images/blocker.png)

- Replace '127.0.0.1' to '0.0.0.0'
bind-address    =0.0.0.0

![Modify Bind Address](./Images/bind.png)

`sudo systemctl restart mysql`

6. On MySql client, connect remotely to Mysql Server without using ssh.Use mysql utility

-Inbound Role for Mysql/Aurora added

`sudo mysql -u remote_user -h 172.31.95.177 -p`

![Client connected](./Images/client.png)

7. Confirm connection
`show databases;`

![Databases](./Images/show.png)
