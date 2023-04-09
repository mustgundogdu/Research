## PRESTA-SHOP 1.7.7.4 REFLECTED CROSS SITE SCRIPTING

`Vulnerable Parameter: message`

`XSS Payload : %3cimg+src+onerror%3dprompt%288%29%3e`

`<Vendor>` : <https://www.prestashop.com/>

#### Vulnerable Code Part 
 Default File Path
> /modules/contactform/contactform.php
![](https://github.com/mustgundogdu/Research/blob/main/PrestaShop/CodePart.PNG)


### Description 
The PrestaShop web application lead the message value without any sanitization on contact-form .The attacker could be inject xss payload with changes the HTTP 'post' request to Http 'get' request for exploitation. That Exploitation shown belows.

#### Http Request-Response
![](https://github.com/mustgundogdu/Research/blob/main/PrestaShop/HttpRequest.png)


![](https://github.com/mustgundogdu/Research/blob/main/PrestaShop/OnBrowser.png)
