##本Demo基于 Yii 2 Basic Application Template 制作

###准备工作
在制作、运行本demo前需要做一些准备工作。

1. 前往www.maxleap.cn, 申请账号,并创建应用
2. 在应用设置部分，打开mysql
3. 记下host连接，dbname,username以及password
4. 打开管理我的数据连接，进入phpmyadmin
5. 创建country表并插入数据，如下：

```
CREATE TABLE `country` (
  `code` CHAR(2) NOT NULL PRIMARY KEY,
  `name` CHAR(52) NOT NULL,
  `population` INT(11) NOT NULL DEFAULT '0'
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `country` VALUES ('AU','Australia',18886000);
INSERT INTO `country` VALUES ('BR','Brazil',170115000);
INSERT INTO `country` VALUES ('CA','Canada',1147000);
INSERT INTO `country` VALUES ('CN','China',1277558000);
INSERT INTO `country` VALUES ('DE','Germany',82164700);
INSERT INTO `country` VALUES ('FR','France',59225700);
INSERT INTO `country` VALUES ('GB','United Kingdom',59623400);
INSERT INTO `country` VALUES ('IN','India',1013662000);
INSERT INTO `country` VALUES ('RU','Russia',146934000);
INSERT INTO `country` VALUES ('US','United States',278357000);
```

###制作过程
* 注， 改制作过程只做一般性描述，不具指导性，仅作参考，具体使用请参看  部署过程。

1. 下载yii包
2. 修改modles,controllers以及views目录的属性为www-data:www-data
3. 修改config/web.php, 打开gii
4. 修改config/db.php, 修改数据库相关数据，host连接，dbname,username以及password都可以从maxleap上关联的应用获得。配置如下：

```
'dsn' => 'mysql:host=circev1.uat.maxleap.cn:3307/5742a9ea70c67600015bede4;dbname=5742a9ea70c67600015bede4',
'username' => '5742a9ea70c67600015bede4',
'password' => '5742a9ea70c67600015bede4',
```

6. 按照指示，部署改代码到cloudcontainer上，具体步骤参考https://github.com/MaxLeap/Docs/blob/master/zh/UserManual/Guide/CloudContainer.md 中的php部分
4. 访问 http://xxxx.xxxxx.xxx/web/index.php?r=gii
5. 按照官方教程创建country的model,CRUD.
7. 浏览器访问 http://xxxx.xxxx.xxxx/web/index.php?r=country, 即可提供一个标准的CRUD应用。

###部署过程
1. git clone 本代码
2. 修改config/db.php, 修改数据库相关数据，host连接，dbname,username以及password都可以从maxleap上关联的应用获得。配置如下：

```
'dsn' => 'mysql:host=circev1.uat.maxleap.cn:3307/xxxxxxxxxxxxx;dbname=xxxxxxxxxxxxxxx',
'username' => 'xxxxxxxxxxxx',
'password' => 'xxxxxxxxxxxx',
```
3. 按照指示，部署改代码到cloudcontainer上，具体步骤参考https://github.com/MaxLeap/Docs/blob/master/zh/UserManual/Guide/CloudContainer.md 中的php部分
4. 由于安全问题，gii 功能不能访问。
5. 浏览器访问 http://xxxx.xxxx.xxxx/web/index.php?r=country, 即可提供一个标准的CRUD应用。


