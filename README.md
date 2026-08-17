# On-path-attack
Hands-on lab notes on path traversal vulnerabilities — setting up Burp Suite as an intercepting proxy to analyze traffic against OWASP Juice Shop.
Overview
Hands-on lab exploring how to set up and use an intercepting proxy to analyze web
application traffic as a foundation for identifying path traversal (directory
traversal) vulnerabilities. Performed against OWASP Juice Shop, a deliberately
vulnerable web application used widely for security training, in a two-machine
lab environment (Kali Linux attacker box + Windows target machine).
Objective
Path traversal vulnerabilities occur when an application uses unsanitized
user input to construct file paths, allowing an attacker to escape the intended
directory (e.g. using ../ sequences) and access files elsewhere on the server.
Before this kind of manipulation is possible, an attacker needs full visibility
into the HTTP requests a client sends — which is what this lab focused on
building.

Environment
	•	Attacker machine: Kali Linux (running Burp Suite Community Edition)
	•	Target machine: Windows 10 (browsing OWASP Juice Shop at juiceshop.local)
	•	Proxy tool: Burp Suite Community Edition v2022.12.5
  
Steps Performed
	1.	Configured Burp Suite as an intercepting proxy
Set up a proxy listener in Burp, first on loopback (127.0.0.1:8080), then
bound to a specific network interface (10.1.16.66:8080) so it could accept
traffic from the separate Windows target machine.
	2.	Redirected target machine traffic through the proxy
Used a PowerShell/batch script (newproxy.bat, served from
http://10.1.16.66/newproxy.bat) to modify the Windows registry proxy
settings (ProxyServer, ProxyEnable under
HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings),
routing all browser HTTP traffic through the Kali Burp instance.
	3.	Tuned Burp’s intercept rules
Reviewed and adjusted the request-matching rules (file extension, HTTP
method, target scope) so Burp captured relevant application traffic while
filtering out noise like images, CSS, and JS.
	4.	Generated traffic against OWASP Juice Shop
Logged into juiceshop.local from the target browser to produce real
authentication traffic for Burp to intercept.
	5.	Reviewed captured requests in Burp’s HTTP History
Confirmed successful interception of requests such as:
	•	POST /rest/user/login → 401 (failed login attempt)
	•	GET /rest/user/whoami → 200
This validated that the proxy chain was working end-to-end — traffic from
the target browser was visible and inspectable in Burp.

Key Takeaway
Traffic interception is the essential first step in testing for path traversal
(and most other web app vulnerabilities). Without the ability to see and modify
raw HTTP requests — including parameters that reference file paths or names —
it’s not possible to test whether a server improperly resolves manipulated
paths like ../../etc/passwd. This lab built that foundation: proxy setup,
client redirection, and traffic capture/analysis in Burp Suite.

Next Steps
	•	Identify endpoints in Juice Shop that accept file names/paths as parameters
	•	Use Burp’s Repeater to inject ../ sequences into those parameters
	•	Observe server responses to confirm whether directory traversal is possible
	•	Document any successful traversal and the underlying cause (lack of input
sanitization, missing path normalization, etc.)
