# Project 8 - Pentesting Live Targets

Time spent: 10 hours spent in total

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

Vulnerability #1: SQLI - Hacker can use the following code: %27%20OR%20SLEEP(10)=0--%27 to make
the webpage take 10 seconds, or however long you want, to reload.

Vulnerability #2: Session Hijacking - Hacker can change the PHP session of a non-admin
to that of an admin.


## Green

Vulnerability #1: User Enumeration - The login uses different styles for when a user that
exists logs in and a user that does not exist logs in.

Vulnerability #2: XSS - Hacker can inject XSS when to the contact us form.  


## Red

Vulnerability #1: IDOR - Salespeople have ids in which a hacker could change to access information
that was not meant to be seen.

Vulnerability #2: CSRF - Hacker can change CSRF value when updating Salespeople information to 
cause the request to fail from a user on a different site.

## Notes

Describe any challenges encountered while doing the work

