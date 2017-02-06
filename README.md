# SpringBoot

Spring Boot makes it ways to create stand-clone, production-grade Srping based Applications that you can "just run".

Drawbacks of Spring

1. Huge framework
2. Multiple  setup steps
3. Multiple configuration steps
4. Multiple build and deploy steps

#Learn @

https://www.youtube.com/watch?v=99Nw2smMTLg&index=3&list=PLqq-6Pq4lTTbx8p2oCgcAQGQyqN8XeA1x
https://docs.spring.io/spring-boot/docs/current-SNAPSHOT/reference/htmlsingle/

#Creating Spring Boot Project - create simple maven jar project

1. Add spring-boot-starter-parent as a parent of your pom

<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>1.5.1.RELEASE</version>
</parent>

2. To enable it as a web project add. This downloads comman jars like tomcat,log4j...

<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
</dependency>

3. Run the Application





