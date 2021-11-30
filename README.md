# Vulnado - Intentionally Vulnerable Java Application

This application and exercises will take you through some of the OWASP top 10 Vulnerabilities and how to prevent them.

## Up and running

1. Install Docker for [MacOS](https://hub.docker.com/editions/community/docker-ce-desktop-mac) or [Windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows). You'll need to create a Docker account if you don't already have one.
2. `git clone git://github.com/ScaleSec/vulnado`
3. `cd vulnado`
4. `docker-compose up`
5. Open a browser and navigate to the client to make sure it's working: [http://localhost:1337](http://localhost:1337)
6. Then back in your terminal verify you have connection to your API server: `nc -vz localhost 8080`

## Architecture

The docker network created by `docker-compose` maps pretty well to a multi-tier architecture where a web server is publicly available and there are other network resources like a database and internal site that are not publicly available.

![](exercises/assets/arch.png)

## Goal of the assignment

During the previous labs, many activities were related to input testing and validation. In the assigment, we want to focus on the security impact of user input and how a potential attacker can control and tak advantage of the user input. The assignment has been devided into two parts:

### 1- Attack serface and pen-testing

It consists of identifying the entry points of the system, then run a set of pen-testing payloads to observe how the application behaves. The goal of this activity is to identify any information leak or behaviour that grans access to the maliciouse user.

For this task we can make use of two tools.
- dirsearch: web path discovery [Github page](https://github.com/maurosoria/dirsearch).
- Burp Suite: penetration testing and vulnerability finder tool [Link](https://portswigger.net/burp).

### 2- Code review (follow user input)
Since we have the source code of the application, we can perform more in depth analysis of the code. This activity consists of following user-controlled inputs and find how thoese input are managed by the application.

Exmaples include query parameters or cookie values as well as external calls
```
POST / GET 
COOKIE / SERVER
Data coming from the database (for stored XSS and second-order injections for example)
Data read from a file or a cache
```

## Exercises

* [SQL Injection](exercises/01-sql-injection.md)
* [XSS - Cross Site Scripting](exercises/02-xss.md)
* [SSRF - Server Side Request Forgery](exercises/03-ssrf.md)
* [RCE - Remote Code Execution & Reverse Shell](exercises/04-rce-reverse-shell.md)

## Questions

- What is the basic design of the application?
- Who are the likely attackers?
- What would an attacker hope to achieve?
- How are the developers trying to protect the application?
- What areas of the application will likely attract the attention of an attacker?
- What sorts of techniques might an attacker use to subvert the application?
- What risks would a successful attack pose to the application?
