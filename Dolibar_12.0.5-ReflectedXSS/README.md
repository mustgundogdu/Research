## Dolibar 12.0.5 Cross-Site-Scripting Via Sql Error Page - CVE-2022-30875
### Path: http://localhost/user/list.php?sortfield=1=14&sortorder=25
### Sql paylaod : 1=14
### Xss Paylaod :  <svg/onload=alert(1)>

First of all sending That sortfield parameter sql payload To list.php file and later returned sql error page  from web application. Unfortunately, not enjectiable The sql payload Because valid only alpha numeric entry. This situation php code is shown below in the screenshot.

![](https://github.com/mustgundogdu/Research/blob/main/Dolibar_12.0.5-ReflectedXSS/alphanumeric.PNG)


But, I noticed to not process the user agent xss filter when return sql error page.Then I enjectiabled The ' <svg/onload=alert(1)>' xss payload.
This situation Burp Suite Http Request and Response is shown below in the screenshot.

![](https://github.com/mustgundogdu/Research/blob/main/Dolibar_12.0.5-ReflectedXSS/dolibarxssviasqlerror.PNG)

 
The Browser display is as follows.


![](https://github.com/mustgundogdu/Research/blob/main/Dolibar_12.0.5-ReflectedXSS/dolibarxss2.PNG)
