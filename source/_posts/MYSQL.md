---
title: MYSQL-存储过程定时删除前7天数据实例
categories: MYSQL
tags: [MYSQL]
---
在实际开发中，可以利用存储过程，定时删除表里面没有用的数据，从而减少对在业务代码去写定时器去删除数据了，提高性能，减少代码维护等等

#### 1.查看数据库是否开启事件
- 命令：
``` 
	select @@event_scheduler;
	 如果查出为OFF标识，可以看出已经关闭事件
```
#### 2.设置事件开启 这样设置 会在重新启动情况 还原默认关闭状态
- 命令：
```
	set global event_scheduler = 'on';
	#可以物理修改数据库配置
	#skip-grant-tables
	 加上:
	event_scheduler=ON
```
#### 3.存储过程 删除前7天的数据
- 命令：
```
	DROP PROCEDURE
	IF EXISTS del_film_login;

	CREATE PROCEDURE del_film_login()
	BEGIN
		DELETE
	FROM
		film_login
	WHERE
		DATE(film_login.login_time) <= DATE(
			DATE_SUB(NOW(), INTERVAL 7 DAY)
		);
	END
	说明：del_film_login 存储过程名，film_login表名 film_login.login_time为时间
```
#### 4.定时每天去删除前7天的数据
- 命令：
```
	CREATE EVENT
	IF NOT EXISTS event_time_clear 
	ON SCHEDULE EVERY 1 DAY
	STARTS '2019-03-14  17:35:00' 
	ON COMPLETION PRESERVE DO
	CALL del_film_login();
	说明：event_time_clear 事件名  del_film_login：存储过程名
```
#### 5.开启某个定时事件
- 命令：
```
ALTER EVENT event_time_clear ON COMPLETION PRESERVE ENABLE
说明：event_time_clear 事件名
```
#### 6.关闭某个事件
- 命令：
```
ALTER EVENT event_time_clear ON COMPLETION PRESERVE DISABLE;
说明：event_time_clear 事件名
```
### END