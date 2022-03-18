
**To Deploy application in Tomcat**

To deploy in tomcat using maven, we added the tomcat7-maven-plugin in pom.xml

```xml
<plugin>
				<groupId>org.apache.tomcat.maven</groupId>
				<artifactId>tomcat7-maven-plugin</artifactId>
				<version>2.2</version>
				<configuration>
					<url>http://localhost:8080/manager/text</url>
					<server>localhost</server>
					<path>/${finalName}</path>
					<username>admin</username>
					<password>admin</password>
					<update>true</update>
				</configuration>
</plugin>
```

```
> mvn clean package
> mvn tomcat7:deploy
```



