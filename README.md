# Project 8 - Pentesting Live Targets

Time spent: **4** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: **Session highjacking** -When using the script provided to get the session ID from the logged in user, it can be passed to the attacker which then can use the same tool to set their session ID to the same thing and when they go back to the page they will be logged in using the other users session.
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/session1.png" /> 
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/session2.png" /> 
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/session3.png" /> 
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/session4.png" /> 
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/session5.png" /> 


Vulnerability #2: **SQL injection.** -When on the SalesPerson page, you can jump from salesperson to salesperson using their IDs. When putting in a ' after the id we get a Database request error. this seems to indicate we can do an injecton here. When trying to sleep the database using ' OR SLEEP(10)=0--' the database is delayed getting the response. I tried getting the database to return some values to me, but I could not get this to work. 
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/SQLI1.png" /> 
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/SQLI2.png" /> 

## Green

Vulnerability #1: **Username Enumeration** -When I created a user with the name tester, and tried to log in to this page using that username and a bad password, the unsuccessful login text was in bold letters. When I tried logging in with a username I knew wassnt in the database, I got an unsuccessful login text with no bold letters. In this way one can find out what valid usernames are. 
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/UsEnum1.png" />
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/UsEnum2.png" />

Vulnerability #2: **Cross-Site Scripting (XSS)** -When filling out the Feedback form you're allowed to enter html tags ingto the feedback field. when one goes to the feedback page as a logged in user, the script is run and the XSS is executed. 
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/XSS1.png" /> 
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/XSS2.png" />



## Red

Vulnerability #1: **Insecure Direct Object Reference (IDOR)** -When a user of the site looks at the sales person tab and tries changing the ID of the sales person in the URL they are able to access sales people that are not public. ID=10 and ID=11 gives us a user that is not public yet and one that is fired for stealing. The other pages redirect back to another page if an illegal id request is made.

<img src="https://github.com/ThoMot/CodePathLab9/blob/master/IDOR1.png" />
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/IDOR2.png" />

Vulnerability #2: **Cross-Site Request Forgery (CSRF)** - 

<img src="https://github.com/ThoMot/CodePathLab9/blob/master/CSRF1.png" />
<img src="https://github.com/ThoMot/CodePathLab9/blob/master/CSRF2.png" />


## Notes

Describe any challenges encountered while doing the work
