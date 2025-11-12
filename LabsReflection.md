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

Here, first lab in SQL injection, we had to break the SQL request of the browser page in order to display more information than needed. For that, we got a sample of what a resquet looked like in the instructions, when a user select a category of products to display. Trying some things in the URL, we would end up by breaking the format of SQL to do what we wanted. And finally we would end up by ignoring the "released" condition of the SQL request, displaying either released and non-released products on the site.

Arriving on this lab I thought the SQL would be in the HTTP exchange somewhere, and that the line type of the instructions would be printed somewhere in. Obviously, I struggled for nothing as what I searched for wasn't accessible to me. The SQL line written was in the server, where I ain't, so my search yielded nothing. It's only after the lab that I remembered what I did on SQL, and how ridiculous my search was. But in my defense, I did not worked a lot on SQL, and not on this aspect (SQL filtering was my comrade's part during the Practical Work). So because I was struggling to know what to search for, I watched the first video. It gived me the solution to the lab, but I did not understand why it was a solution. So I watched Rana's video, that explained a lot better. I understood on the job how was working the SQL format and that this requests where vulnerable. Maybe because I am tired, but I struggled for nothing much to understand the logic break. But I have been able to see what was doing our request and I ended up today's cybersecurity session on this completed lab.

## Lab 4: SQL injection vulnerability allowing login bypass
**Topic:** SQL injection

This lab wanted a user to login as "administrator" username, using SQL vulnerability. To get into this account, we just have to get on the page of the login and set our username to "administrator", just adding the special "--'" characters after it to make the request enter a format in SQL that will ignore the other parameter: the password. No matter what we enter as the password, we would login as administrator.

It seems I have difficulties with this kind of logic. I tried to modify the HTTP request containing the username and password in clear text, but the token wasn't accepted and it wasn't identified as on my browser. The solution was pretty simple, too much simple to me it seems, because I do understand easily that this would work easily, but it would probably not come to my mind as easily. I need more practive to see this possibilies. I would probably do more SQL labs later.

## Lab 5: Unprotected admin functionality
**Topic:** Access control

For this lab, we had to delete a user accessing administrator panel. To access it, we had to search some objects on the web server by typing different URLs and try to see if something was accessible. The /robots.txt gave us the path to administrator panel, which give us the opportunity to delete carlos, the target user, with a simple click.

What I would have to do was pretty clear to me. I've read the documentation on this topic, and the goal was pretty obvious. So I searched a little on HTTP request history for anything useful, but no, and I tried type some keys in the URL. At that time, I began by entering things like "administrator" or "panel" but nothing worked. As I didn't have the information needed, I read the solution, revealing the presence of the robots.txt. I don't understand why this name and what is the purpose of this file, but it was what I needed to find. I am satisfied that I knew what to do, but a little frustrated because I do not see how I would have ended up searching this key word (assuming it was not in the documentation of the topic).

## Lab 6: User role can be modified in user profile
**Topic:** Access control

In this situation, we were requested again to delete the user carlos by accessing admin panel. This time, we knew where was the panel but since our user do not have the admin permissions, it cannot access it. Through some HTTP history exploration and features uses, we would end up seeing that we send a JSON format to change our mail address, and that the server respond also with JSON, showing in clear that roleid, where we want to have the number 2 for admin access, is in the same range than username and mail address. So by adding '"roleid":2' in the POST, we would end up with modified roleid and be able to access admin panel to delete carlos (poor carlos every time).

I struggled a moment because I did not try to see the HTTP history using email address edit, and I am feeling bad about that, it's the first thing I should have done, there is not a lot a functionnalities on this webpage. I also struggled a moment because my modified JSON did not worked and return many errors, before realising that I forgot to place the comma... Thanks to Rana for explanations.

## Lab 7: Unprotected admin functionality with unpredictable URL
**Topic:** Access control

Easier, after reading the documentation just above in the topic, I've understand that I would have to look up for the admin page reference in the HTTP requests, and I found what I needed easily.

## Lab 8: User role controlled by request parameter
**Topic:** Access control

Also simple, I logged in with user credentials given, and I looked up for the "cookies" parameter. In plain text a boolean parameter for admin was written, and so I turned it on "true" on every operation I did on admin page by using the interceptor of the Burp Suite.
