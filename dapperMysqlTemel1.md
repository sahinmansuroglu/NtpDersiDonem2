## Dapper ile Mysql İşlemleri ##

### Kullanılacak Olan Veritabanı sql kodları ve workbench'deki tasarım  penceresi ###

```sql
CREATE TABLE `eokul`.`tblnot` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `ogrenciAdSoyad` VARCHAR(45) NOT NULL,
  `puan1` TINYINT(3) NOT NULL,
  `puan2` TINYINT(3) NOT NULL,
  `ortalama` DOUBLE NOT NULL,
  PRIMARY KEY (`id`));
```

![image](https://user-images.githubusercontent.com/28144917/166909704-b41ab263-4a34-4110-860d-a1694173e9ef.png)

### Root kullanıcısının Kimlik Doğrulama tipini  (authentication type) standart olarak ayarlamak ###
```
cd "C:\Program Files\MySQL\MySQL Server 8.0\bin"

C:\Program Files\MySQL\MySQL Server 8.0\bin> mysql -u root -p
Enter password: *********

mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'yeni Şifre';

```
