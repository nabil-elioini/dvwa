## Exercise 1 - SQL Injection

SQL injection is the ability of an attacker to execute arbitrary SQL into an insecurely created query. They might do this to attempt to gain access to the system, cause destruction by deleting rows, or list vital information that they should not have access to.

The way SQL injections are constructed is by the use of escape characters such as `'` which allows an attacker to escape out of the intended query with their own input and execute another query directly against the database.

For example, let's say we had some logic such as the following (in pseudocode):

```
username := user input from HTML form
password := user input from HTML form
hashedPassword := md5(password)

sql := "select * from admins where username = '" + username "' and password = '" + hashedPassword + "' limit 1"
executeQuery(sql)
```

This is a valid SQL string that is taking user input for username and password, hashing the password and comparing the hashed password to that in the database. This is a very common way to authenticate users to a platform, but is also easily able to be abused.

Let's say we are an attacker and want to execute some arbitrary SQL into this.

1. Which field would we exploit?
2. What string would we place into that field?
3. Who would this log us in as?

# Lab

Try to exploit the endpoint `/login` using a SQL injection. A valid, but unauthorized request looks like this:

```
curl -XPOST -H 'Content-Type: application/json' -d '{"username":"rick", "password":"password"}' 'http://localhost:8080/login'
```

Try to gain access as the user `rick`.

