# Externalized Query Example

This project employs Spring Boot and Spring Data JPA to demonstrate how to successfully read and execute a SQL statement by key from a properties file.

## Prerequisites

* Java JDK 1.8u141
* Gradle 4.1

## How to compile and run unit tests

```
gradle test
```

## Details

This project employs [Lombok](https://projectlombok.org/features/all) so we can annotate instead of writing what amounts to boilerplate code.

We annotate `CourseQueries` with [ConfigurationProperties](https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-external-config.html#boot-features-external-config-loading-yaml) to encapsulate a namespace of `sql.course` queries found in `application.yml`

We define `CourseRepository` and have it extend the [CrudRepository](https://docs.spring.io/spring-data/data-commons/docs/1.6.1.RELEASE/reference/html/repositories.html#repositories.core-concepts) interface. We also define an additional query method using [conventions](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#repositories.query-methods.query-creation).

We implement `CourseService` to demonstrate how to employ a [JdbcTemplate](https://docs.spring.io/spring/docs/current/javadoc-api/org/springframework/jdbc/core/JdbcTemplate.html#query-java.lang.String-java.lang.Object:A-org.springframework.jdbc.core.ResultSetExtractor-) to execute a query 

Finally we author a unit test for the aformentioned service. (Spring Boot Test is [helpful](https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-testing.html)).

An [in-memory](http://www.h2database.com/html/main.html) database is [initialized](https://docs.spring.io/spring-boot/docs/current/reference/html/howto-database-initialization.html#howto-initialize-a-database-using-hibernate) on startup.

## Credits

* Sayem Ahmed for [AttributeConverter](https://www.javacodegeeks.com/2017/03/dealing-javas-localdatetime-jpa.html) used to convert [LocalDateTime](https://docs.oracle.com/javase/8/docs/api/java/time/LocalDateTime.html)
