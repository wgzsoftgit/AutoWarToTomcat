#1、在将项目发布到远程Tomcat时需要启动远程Tomcat管理控制台账号
     
       开启tomcat管理控制台账号地址为：Tomcat安装目录/conf/tomcat-users.xml文件
```
<tomcat-users>
<role rolename="admin-gui"/>
<role rolename="admin-script"/>
<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<role rolename="manager-jmx"/>
<role rolename="manager-status"/>
<user username="admin" password="admin" roles="manager-gui,manager-script,manager-jmx,manager-status,admin-script,admin-gui"/>
</tomcat-users>
``` 
　解释：给账号admin配置manager-script及manager-gui权限

#pom.xml
```
<plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <configuration>
        <source>1.8</source>
        <target>1.8</target>
      </configuration>
    </plugin>

    <plugin>
      <groupId>org.apache.tomcat.maven</groupId>
      <artifactId>tomcat7-maven-plugin</artifactId>
      <version>2.2</version>
      <configuration>
        <url>http://localhost:8080/manager/text</url> <!-- 远程tomcat下manager路径 -->
        <username>admin</username>    <!-- tomcat控制台账号 -->
		<password>admin</password>     <!-- tomcat控制台密码-->
		<path>/muckCarJar</path> <!-- 此处的名字是项目发布的工程名-->
        <uriEncoding>UTF-8</uriEncoding><!--编码-->
        <charset>UTF-8</charset>
        <encoding>UTF-8</encoding>
        <!-- <ignorePackaging>true</ignorePackaging>   Skipping non-war projec -->
      </configuration>
    </plugin>

  </plugins>
   <!--  <finalName>muckCarJar</finalName>    指定打包的名字-->
</build>
```
