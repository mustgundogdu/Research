                                 KLOG 2.4.1 SERVER COMMAND INJECTION VULNERABILITY
         
![](https://github.com/mustgundogdu/Research/blob/main/KLOG_SERVER/vuln.PNG)

As you can see in the code line above , the user input received without any filtering in the login panel is running on the server.The purpose of code line is fail login user save on ‘log.sh’ file found in the path /klog/www/config/scripts/ .Shown below see log.sh source codes.

![](https://github.com/mustgundogdu/Research/blob/main/KLOG_SERVER/log_sh.PNG)

Where ‘logmsg’ variable holds the user value in here and Var / log / klog / 127.0.0.1 / kaudit.log file is saved as in the code. This situation cause be command injection vulnerability.
                                    
                                      VULNERABILITY DETECTION AND EXPLOITATION
      
In the first step “%26sleep+5%26”  payload’s has been sent and it is provided to run on targert klog server .This situation Burpsuite is shown below in the screenshot.

![](https://github.com/mustgundogdu/Research/blob/main/KLOG_SERVER/sleep5.PNG)

Then, in order to automate the reverse shell connection on the server, the exploit shown in the screenshot below, was run and the shell operation was successfully performed in the listening NC connection.

![](https://github.com/mustgundogdu/Research/blob/main/KLOG_SERVER/exploit_ss.PNG)
