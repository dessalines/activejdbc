tchoulihan's no-instrument ActiveJDBC - &mdash; ActiveRecord for Java
==========

This is a fork of the ActiveJDBC for java, that doesn't require any instrumentation, and is usable with a simple maven dependency.

```xml
<dependency>
	<groupId>com.github.tchoulihan</groupId>
	<artifactId>activejdbc</artifactId>
	<version>1.4.20</version>
	<exclusions>
		<exclusion>
			<groupId>opensymphony</groupId>
			<artifactId>oscache</artifactId>
		</exclusion>
	</exclusions>
</dependency>
```

Setup a sample table(its best to put all the tables in a class called Tables.java)
```java
@Table("User")
public static class User extends Model {}
public static final User USER = new User();
```
Use JDBC for that table:
```java
import static com....Tables.*;
User user = USER.findFirst("id = ?", userId);
```

And use the constant `USER` for all activities, including .find, or .createit ...
