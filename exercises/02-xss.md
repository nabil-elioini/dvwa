# XSS - Cross Site Scripting

XSS or Cross site scripting is one of the most common vulnerabilities and also one that plagues developers of client side applications in JavaScript. With so many frameworks out there, it becomes challenging to determine what is being rendered and how. A stored XSS attack is one in which an attacker is able to inject arbitrary JavaScript onto a page and have that JavaScript be rendered by another user.

This is especially dangerous on pages that have some type of authentication since authentication tokens can easily be sent to another site via JavaScript.

The best ways to prevent XSS are all cataloged here:
https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.md

**TL;DR: Sanitize all values just before you render them.**

Example:
You have an HTML template you would like to render with a username value as a `data` attribute such as this:

```
<div data-username="<%= @username %>">
...
</div>
```

If the user is able to update their username value, which is stored on the server, they could adjust the HTML to run their own scripts on others' computers on your site:

```
"><script>alert('pwned!')</script><div class="
```


# Lab

Navigate to http://localhost:1337 and you'll be presented with a login page. Now that we have `rick`'s password, let's use that to log into the site. Let's try adding some comments and see what we can do.

