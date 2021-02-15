springboot 项目搭建



- 第一步，直接next
- <img src="C:\Users\wantao\AppData\Roaming\Typora\typora-user-images\image-20210123105528180.png" alt="image-20210123105528180" style="zoom: 50%;" />



- 第二步：group处填写包名路径，一般选择公司域名，artifact处填写项目名，一般格式为单词小写，用"-"分隔。然后勾选如下配置。点击next。
- <img src="C:\Users\wantao\AppData\Roaming\Typora\typora-user-images\image-20210123105710559.png" alt="image-20210123105710559" style="zoom:50%;" />



- 第三步，勾选所需配置。点击next
- <img src="C:\Users\wantao\AppData\Roaming\Typora\typora-user-images\image-20210123110249989.png" alt="image-20210123110249989" style="zoom:50%;" />



- 第四步，配置文件，配置MySQL，mybatis文件，此处是mybatis，需添加Mapper目录。
- <img src="C:\Users\wantao\AppData\Roaming\Typora\typora-user-images\image-20210123110550419.png" alt="image-20210123110550419" style="zoom: 33%;" />



- 启动项目，试跑。
- <img src="C:\Users\wantao\AppData\Roaming\Typora\typora-user-images\image-20210123110900805.png" alt="image-20210123110900805" style="zoom: 33%;" />

- 第六步，构建结构，（具体依项目而定）
- <img src="C:\Users\wantao\AppData\Roaming\Typora\typora-user-images\image-20210123115310254.png" alt="image-20210123115310254" style="zoom:50%;" />

- 第七步，配置好mybatis的xml文件对应关系。

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
  PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.red.dao.LoginMapper">

	<!--由于定义了别名包,所以映射时只需要写类名即可-->
	<select id="findAll" resultType="User">
		select * from user
	</select>

	<!--
		设定驼峰规则
		对象属性  User(userId,userName,userAge)

		表字段	user (user_id,user_name,user_age)

		驼峰规则映射策略:
		字段信息:user_id  ~~~~~ 去除中间下划线~~~~~首字母大写
						  ~~~~userId~~~映射给userId的属性
		注意事项:
			如果开启了驼峰规则映射,则必须满足特定的要求
	-->

</mapper>

```

