# PortSwigger Labs: Reflection

## Lab 1: Username enumeration via different responses
In this lab, I have been redirected to a sample website of blogs. Following the replay session of 4.11.2025 lecture with Mr Ville, I used the Burp Suite to spam requests on the web server, using a sample connection try POST request. Modifying the clear text of username and password of the request, the attack was pretty simple, and a lot of request have been send with a lot of "candidate" usernames. Finally, one of the response was different from the others, hilighting the fact that this username was the valid one. And I did that type of spam request again with password info modified, still with a "candidate" list of passwords. Again, the only response different was the one to use, and I have been able to login in the website using the username and password found.

If I have understand easily what to do, I do not understand that easily how to do it. This kind of brute-force technique is pretty common and well-known, but using the Burp Suite was a different story. I did not understand what we were initiating with the first manipulations, but I understand a lot better when I saw the POST request with the username and password in clear text. After using the payload generator with the list, I understod what was coming next. I struggled a bit to see how to know what was the good response to select, but the solution showed by Ville was pretty logic to me. I'll remember for next times. The password payload was mechanical to do for me, and quickly I have been able to find what I needed and completed the lab by logging on my browser.

However if here we got a candidate lists of usernames and passwords to use, in real application it will not be the case. Thus I wonder how to get this kind of lists, and if the password list would not be too much large. Moreover, I know that to prevent this issue, a lot of websites use a count before ban (or kind of) to see how many times a request have been send, from IP or for wich user, and that this attack will never be really possible, at least in this conditions.

## Lab 2: XXX

## Lab 3: XXX

## Lab 4: XXX

## Lab 5: XXX

## Lab 6: XXX
