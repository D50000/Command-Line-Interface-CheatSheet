# =============== Ｍaven Command ===============

Detail:  
https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html

## General Commands

- Check mvn version.

```shell
mvn --version
```

- Ｍaven compile `java code` (src/main/java)into `.class` file.

```shell
mvn compile
```

- It include `mvn compile` the code first and install in `local maven repository`. Provide for other local repositories or project to use.

```shell
mvn install
```

- It include `mvn compile` the code first and install in `remote maven repository`. Provide for other repositories or project which can access the remote server.

```shell
mvn deploy
```

- It will compile and wrap the code into a package.And the package can be deploy or host on a server.  
ex:   
`jar: Spring Boot can package web application jar file.`  
`war: Java web application support Java Servlet that host on Apache Tomcat.`  

```shell
mvn package
```

- It will clean the compiled file. Include `.class, .jar, .war, /target/*` files. Use for clean the cache in old project compile result.

```shell
mvn clean
```
