## Glassfish Server-Side Request Forgery Vulnerability(SSRF) [Authenticated]

The specified vulnerable parameter (restUrl) causes the SSRF vulnerability. In this way, an attacker can obtain critical and sensitive service information for the system, such as port scanning. Or, he can direct the server information to other resources within the network. 

#### **Vulnerable Path**   
https://[targetexample]:4848/download/log/?contentSourceId=LogViewer&start=56783&instanceName=server&restUrl=https%3A%2F%2Flocalhost%3A4848%2Fmanagement%2Fdomain

#### **OS**
Windows Server 2019, Ubuntu 22.04

#### **Affected Version** 
6.2.5, 7.0.17

### **Vulnerable Code Part**

![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/resourcecode.PNG)


![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/resourcecode1.PNG)


### **Impacts**
  - Port Scan and Network Discovery
 	- Information disclosure
 	- File Discovery

### Vulnerability Detection
**Attacker Listener Ip: 192.168.81.187**

**Glassfish Server Ip: 192.168.81.129(ubuntu), 192.168.81.160(Windows Server 2019)**

![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/detection0.PNG)

![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/detection1.PNG)

The **'gfresttoken'** value used for REST API calls can be obtained by an attacker by listening on a server where they are monitoring traffic. 

## Port Scan 

![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/portscan0.PNG)

### - Intruder Configuration
![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/portscan2.PNG)

### - Local Port Information
![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/portinf.PNG)

### - Result 
![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/portscanresult.PNG)


## File Discovery 
Additionally, the 'restUrl' parameter in the outgoing request allows an attacker to perform file discovery on the target system. For this, it is sufficient for the attacker to use a wordlist to enumerate file names via GlassFish. In other words, the attacker can exploit the SSRF vulnerability in GlassFish for reconnaissance, performing scans either on the local system or across the network from the server where GlassFish is installed (using HTTP '200' and '404' status codes).

![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/existfile.PNG)

![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/dontexistfile.PNG)

![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/filediscovery2.PNG)

![](https://github.com/mustgundogdu/Research/blob/main/glassFish/ScreenShots/filediscovery1.PNG)



## References 
https://portswigger.net/web-security/ssrf

https://www.cobalt.io/blog/from-ssrf-to-port-scanner







