
_CDN:_ Content Delivery Networks stores copies of your website's content on different servers, so when you try to reach it, it looks it from the nearest server. 

CDNs also act as a protective layer between users and the origin. 
Via:
- **IP masking:** which hides the origin server's IP address
- **DDoS Protection:** Absorbs large traffic spikes
- **HTTPS enforced:** Encrypts everything with TLS
- **Built-in WAF:** Blocks common web attacks
---



_WAF:_ Web Application Firewalls adds an extra layer of security for websites and web apps by inspecting the requests. Blocks or logs malicious traffic based on it's rules. 

WAF Types are:
- **Cloud-based (Reverse Proxy):** Sits in front of the webserver
- **Host-based:** Installed directly on the web server. Offers per-application control
- **Network-based:** Physical or virtual appliance at the network edge; common in enterprises


WAF examples for behavior:
- **Signature-based detection:** Blocks known patterns (e.g sqlmap user agents)
- **Heuristic detection:** Flags suspicious requests (e.g script-like queries)
- **Behavioral analysis:** Detects unusual activity (e.g repeated login attempts)
- **IP & location filtering:** Blocks traffic from risky/unexpected regions


**Request Methods To Be Aware Of**:

|                    |                                         |                                                |
| ------------------ | --------------------------------------- | ---------------------------------------------- |
| **Request Method** | **Normal Usage**                        | **Possible abuse**                             |
| **GET**            | Retrieve a resource                     | Used for recon or interacting with a web shell |
| **POST**           | Submit data to the server               | Upload or interact with a web shell            |
| **PUT**            | Upload or replace a file on the server  | Upload a web shell                             |
| **DELETE**         | Remove a resource from the server       | Cleanup methods                                |
| **OPTIONS**        | Requests methods that are supported     | Reconaissance                                  |
| **HEAD**           | Similar to GET but only returns headers | To detect files                                |