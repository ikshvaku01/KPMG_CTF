## Task: 

Your mission, should you choose to accept it, is to infiltrate a mysterious portal secured by OTP authentication.
`159.65.146.255`

## Points: 200

## Solution:
Given an IP Address : `159.65.146.255`

used ftp anonymous to access it
```bash
ftp 159.65.146.255
Connected to 159.65.146.255.
220 (vsFTPd 3.0.5)
Name (159.65.146.255:yashsingh): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
229 Extended Passive Mode Entered (|||30002|)
150 Here comes the directory listing.
-rw-r--r--    1 0        0            1891 Mar 24 06:54 my_database.sql
226 Directory send OK.
ftp> ls -a
229 Extended Passive Mode Entered (|||30008|)
150 Here comes the directory listing.
dr-xr-xr-x    1 1000     1000         4096 Jul 25 10:54 .
dr-xr-xr-x    1 1000     1000         4096 Jul 25 10:54 ..
-rw-r--r--    1 0        0            1891 Mar 24 06:54 my_database.sql
226 Directory send OK.
ftp> mget .sql
ftp> get my_database.sql my.sql
local: my.sql remote: my_database.sql
229 Extended Passive Mode Entered (|||30004|)
150 Opening BINARY mode data connection for my_database.sql (1891 bytes).
100% |***************************************************************************|  1891       13.25 MiB/s    00:00 ETA
226 Transfer complete.
1891 bytes received in 00:00 (23.02 KiB/s)
ftp> exit
221 Goodbye.
```

Opened the `my.sql` program using cat command:
```sql
-- MariaDB dump 10.19  Distrib 10.4.27-MariaDB, for Linux (x86_64)
--
-- Host: localhost    Database: CTF2
-- ------------------------------------------------------
-- Server version       10.4.27-MariaDB

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `users`
--

DROP TABLE IF EXISTS `users`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `users` (
  `number` varchar(100) NOT NULL, `username` varchar(100) NOT NULL, `password` varchar(100) NOT NULL, `TOTP` varchar(100) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `users`
--

INSERT INTO `users` VALUES ('1', 'admin', 'admin', 'YDTN2JY6CWKSK6PB3HNOAY4APASUVREM');
UNLOCK TABLES;

UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2023-03-24 11:51:06
```

From here we have got `Username` : `admin`  & `Password` : `admin`

FOCUS ON THE WORD TOTP (i.e. Time-based One Time Password)

```
YDTN2JY6CWKSK6PB3HNOAY4APASUVREM
```
Use a TOTP Generator to get a 6 Digit Token & set a time Period of 30 sec

Access the deployed website and get the flag with the above credentials.
```
KPMG_CTF{324b7e52953f62f1624fb64a2e8202e4}
```