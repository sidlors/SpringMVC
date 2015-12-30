# SpringMVC

Los desarrolladores de Java a menudo se basan en ejemplos para aprender el framework Spring. Ejemplos sencillos son a menudo un recurso clave de aprendizaje. Hay muchas aplicaciones Spring MVC HelloWorld. Sin embargo, la mayoría de ellos son anticuadas (no integrar Maven, utilice versión antiguas, etc) o no completa (falta pasos clave o vista de jerarquía de archivos). 

Vamos a mostrar los pasos para crear una aplicación Spring MVC HelloWorld usando Maven en Eclipse. Contenido y ubicaciones de de todos los archivos se ilustran.

1.- Create tu proyecto maven

![](http://www.programcreek.com/wp-content/uploads/2014/02/spring-helloworld-maven-1.jpg)
![](http://www.programcreek.com/wp-content/uploads/2014/02/spring-helloworld-maven-2.jpg)

2.- Selecciona "webapp".

![](http://www.programcreek.com/wp-content/uploads/2014/02/spring-helloworld-maven-3.jpg)
![](http://www.programcreek.com/wp-content/uploads/2014/02/spring-helloworld-maven-4.jpg)


Una vez creado el proyecto Maven, el proyecto en la vista del navegador debe ser similar a la siguiente:
![](http://www.programcreek.com/wp-content/uploads/2014/02/spring-mvc-helloworld-navigator-view1.jpg)

###pom.xml

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>mx.com.sidlors.spring.mvc</groupId>
	<artifactId>HelloWorld</artifactId>
	<packaging>war</packaging>
	<version>0.0.1-SNAPSHOT</version>

	<properties>
		<spring.version>4.0.1.RELEASE</spring.version>
	</properties>
	<dependencies>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>3.8.1</version>
			<scope>test</scope>
		</dependency>
		<!-- Spring dependencies -->
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-core</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
	<groupId>commons-fileupload</groupId>
	<artifactId>commons-fileupload</artifactId>
	<version>1.2</version>
</dependency>
		
		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-web</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>javax.validation</groupId>
			<artifactId>validation-api</artifactId>
			<version>1.0.0.GA</version>
		</dependency>
		<dependency>
			<groupId>org.hibernate</groupId>
			<artifactId>hibernate-validator</artifactId>
			<version>4.3.0.Final</version>
		</dependency>

		<dependency>
			<groupId>org.springframework</groupId>
			<artifactId>spring-webmvc</artifactId>
			<version>${spring.version}</version>
		</dependency>
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>javax.servlet-api</artifactId>
			<version>3.1.0</version>
		</dependency>
		<dependency>
			<groupId>javax.servlet</groupId>
			<artifactId>jsp-api</artifactId>
			<version>2.0</version>
		</dependency>
		<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
    <version>1.2</version>
</dependency>

	</dependencies>


	<build>
		<finalName>HelloWorld</finalName>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.1</version>
				<configuration>
					<source>1.7</source>
					<target>1.7</target>
				</configuration>
			</plugin>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-war-plugin</artifactId>
				<version>2.2</version>
				<configuration>
					<failOnMissingWebXml>false</failOnMissingWebXml>
				</configuration>
			</plugin>
		</plugins>
	</build>
</project>
```

###web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
xmlns="http://java.sun.com/xml/ns/javaee" 
xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd" 
id="WebApp_ID" version="3.0">
  
 
	<display-name>Archetype Created Web Application</display-name>
	<servlet>
		<servlet-name>dispatcher</servlet-name>
		<servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
		<load-on-startup>1</load-on-startup>
	</servlet>
	<servlet-mapping>
		<servlet-name>dispatcher</servlet-name>
		<url-pattern>/forms/*</url-pattern>
	</servlet-mapping>

	<context-param>
		<param-name>contextConfigLocation</param-name>
		<param-value>/WEB-INF/dispatcher-servlet.xml</param-value>
	</context-param>

	<listener>
		<listener-class>
			org.springframework.web.context.ContextLoaderListener
		</listener-class>
	</listener>
</web-app>
```




