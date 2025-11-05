# PortSwigger Labs: Reflection

## Lab 1: Username enumeration via different responses
**Topic:** Authentication

In this lab, I have been redirected to a sample website of blogs. Following the replay session of 4.11.2025 lecture with Mr Ville, I used the Burp Suite to spam requests on the web server, using a sample connection try POST request. Modifying the clear text of username and password of the request, the attack was pretty simple, and a lot of request have been send with a lot of "candidate" usernames. Finally, one of the response was different from the others, hilighting the fact that this username was the valid one. And I did that type of spam request again with password info modified, still with a "candidate" list of passwords. Again, the only response different was the one to use, and I have been able to login in the website using the username and password found.

If I have understand easily what to do, I do not understand that easily how to do it. This kind of brute-force technique is pretty common and well-known, but using the Burp Suite was a different story. I did not understand what we were initiating with the first manipulations, but I understand a lot better when I saw the POST request with the username and password in clear text. After using the payload generator with the list, I understod what was coming next. I struggled a bit to see how to know what was the good response to select, but the solution showed by Ville was pretty logic to me. I'll remember for next times. The password payload was mechanical to do for me, and quickly I have been able to find what I needed and completed the lab by logging on my browser.

However if here we got a candidate lists of usernames and passwords to use, in real application it will not be the case. Thus I wonder how to get this kind of lists, and if the password list would not be too much large. Moreover, I know that to prevent this issue, a lot of websites use a count before ban (or kind of) to see how many times a request have been send, from IP or for wich user, and that this attack will never be really possible, at least in this conditions.

## Lab 2: Password reset broken logic
**Topic:** Authentication

During this lab, we had to reset the password of another user, using as the only infos our credentials to the site and the victim's ones. To do this, We had to first reset our password in order to get the HTTP exchange between my browser and server, and using the POST request with my own credentials, modify a vulnerability in request authentification, using two tokens in the same page, verifying that they are same to allow the modifications of a user's password. So by simply replacing the token by whatever I wanted (on both places) and the username to the victim's one, his password have been changed to the one I sent, so I have been able to login.

Honestly, I did not understand why this was possible. I think that this verification process is very ridiculous, and is why I have not been able to exploit it. But as Rana in the video explained, we just have to try some things, like modify the token. And surprise, it worked. Because if something seems stupid to me it will be to others. Never exclude possiblities for that reason, or I would be the stupidest one.

## Lab 3: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data
**Topic:** SQL injection


## Lab 4: SQL injection vulnerability allowing login bypass
**Topic:** SQL injection


## Lab 5: Unprotected admin functionality
**Topic:** Access control


## Lab 6: User role can be modified in user profile
**Topic:** Access control

