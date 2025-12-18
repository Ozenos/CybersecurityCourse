# PortSwigger
<img width="1136" height="963" alt="Capture d’écran 2025-12-18 153356" src="https://github.com/user-attachments/assets/ee5bf451-94bd-4d40-87d6-831d04d0379b" />

From https://github.com/Ozenos/CybersecurityCourse/blob/main/LabsReflection.md:
1. Username enumeration via different responses - Authentication
2. Password reset broken logic - Authentication
3. SQL injection vulnerability in WHERE clause allowing retrieval of hidden data - SQL injection
4. SQL injection vulnerability allowing login bypass - SQL injection
5. Unprotected admin functionality - Access control
6. User role can be modified in user profile - Access control
7. Unprotected admin functionality with unpredictable URL - Access control
8. User role controlled by request parameter - Access control
9. 2FA simple bypass - Authentication
10. File path traversal, simple case - Path traversal
11. File path traversal, traversal sequences blocked with absolute path bypass - Path traversal
12. File path traversal, traversal sequences stripped non-recursively - Path traversal
13. File path traversal, traversal sequences stripped with superfluous URL-decode - Path traversal
14. File path traversal, validation of start of path -  Path traversal
15. File path traversal, validation of file extension with null byte bypass - Path traversal
16. Username enumeration via subtly different responses - Authentication
17. Broken brute-force protection, IP block - Authentication
18. OS command injection, simple case - Command Injection

---

# The Booking system project

## Phase1
### Part1
was a starting tutorial, making me just familiar with Docker and ZAP. We learn how to create a penetration testing environment and watch through vulnerabilities.
During this phase, the overall system was setup, but only the logging was in fact somewhat functional, and this only thing contained already numerous flaws and protections to work on.
What took me most of the time was to understand what to do first, then what I was doing, then writing the report.

### Part2
Here we would have to take our last report and check whether or not the flaws noted on have been corrected. At this time I also started the PortSwigger labs, making me more familiar with the Burp Suite for
this labs and for searching precedent flaws in HTML documents. I learned more about how to recognize some technologies on web pages.
During this part not very lot of functionnalities changed on the web page, it was more of a security patch.
This part did not took me a lot of time because I feeled "familiar" with what to do, so it was writing the discussion post that was the most time-consuming, adding the fact that I did that on the wrong place
(GitHub instead of ItsLearning).

## Phase2
Here we had to try to get passwords from preconfigured users in the system. Using tools like hashcat to match a password structure with a MD5 hash, we used dictionnary or brute-force attacks to obtain the
good one. Notice that this was out of the system as we have get the hash beforehand from the database, and using some clues just run matching algorithm on our own machines.
Here we did not really evolved in the application, or it wasn't the work with had to deal with.
What took me most of time was to understand what to do as I was clueless watching the commands and instructions, as I needed to understand that we had to run something on my machines outside of the web page
(and see the video beforehand also).

## Phase3
It was tests on authorization procedures, role-based access of the application. We had to try if the roles were matching their rights inside the app, and if we could gain access to unauthorized zones.
The application was finally functionnal, we were able to do all what the app was supposed to do, i.e. create an account, login, logout, create a resource, make a reservation, modify reservations.
But still lack of security and, related to the subject of authorization, of role-bases permissions configuration.
What took me the most of time was obviously to go through all possibilies (pages and actions) with each user, and organize that procedure. It was hard as I was discovering new pages during the work.

## Phase4
Here, we come to legal issues, the application is supposed fine in function and security, so let's work on GDPR and legal documents. We have to go through a GDPR checklist, to note if the app was compliant to it.
And then write a Privacy policy, Terms of Service and a Cookie policy for the app (using AI to help the process).
I took most of the time to get through the checklist, some points were difficult to deal with for me, and I read pretty well, so after ChatGPT generated the documents, I did not took long time to go through and
make corrections on the three documents.


This topic what the main, the guideline of the course. I learned how we make a web app (and just apps in general) through iteration, not by doing all at once and looking for problems (in both senses of the term).
Obviously we saw some tools to find vulnerabilities, and enlarged the vision, the possibilities to try for before we say it's good. Because the true flaw is the one you don't expect.
Finally, what was more difficult to me to follow was the legal issues, learning some of the GDPR, what we have to do in regard of law. It felt, to me, more boring that the other things, but I understand how
important it is.

---

# Logbook

https://github.com/Ozenos/CybersecurityCourse/blob/main/logbook.md

| Topic  | Used hours |
| :--- | :---: |
| CCNA course | 6 |
| PortSwigger labs | 8 |
| Booking System | 22 |
| Lectures | 5 |
| This report | 1 |

Total hours spent: 42
