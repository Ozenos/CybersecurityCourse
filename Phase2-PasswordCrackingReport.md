## whatsupdoc@looneytunes.tv - reserver
### Password: carrots123
Followed video steps, copying exact commands and so on.

## darkknight@gothamwatch.org - reserver
### Password: iamvengeance
Followed video steps, copying exact commands and so on.

## doh@springfieldpower.net - administrator
### Password: donuts4life
`hashcat -O -m 0 -a 0 "d730fc82effd704296b5bbcff45f323e" rockyou.txt --force --potfile-disable`, command used in the same way we did for *whatsupdoc@looneytunes.tv*, because the hints are the same and only suggest a regular dictionnary attack.
<img width="462" height="255" alt="image" src="https://github.com/user-attachments/assets/b0fbbb5f-bb2f-4e6d-8276-c204fc9bf2c7" />

## chimichanga@fourthwall.com - administrator
### Password: breaking4thwall
`hashcat -m 0 -a 3 "7cb56c2b86150b797cff32eaef97f338" breaking?1?1?1?1?1ll --custom-charset1=?l?d --potfile-disable`, I made this one in respect of the hint, saying beginning with "breaking", finishing with "ll" and including 1 digit and 14 lowercase letters. Copilot gave me `--custom-charset1=?l?d` to allow me search using both lowercase letters and digits in a same position, as the hint did not indicate were was the digit.
<img width="461" height="157" alt="image" src="https://github.com/user-attachments/assets/7dcdadf1-913f-4508-9fa5-c0fb865a5f30" />

## iamyourfather@deathstar.gov - reserver
### Password: darkside42
`hashcat -O -m 0 -a 0 "706ab9fc256efabf4cb4cf9d31ddc8eb" rockyou.txt --force --potfile-disable`, as always with hint only saying "found with a dictionnary attack", I copy-pasted the original command and just replaced the hash with the one I was working on.
<img width="462" height="236" alt="image" src="https://github.com/user-attachments/assets/ae8b8345-d8f2-439a-be7c-298877b12683" />

## elementary@221bbaker.uk - administrator
### Password: deduction221B
`hashcat -m 0 -a 3 "12c9cef0bfb6b91c42b363b4cf02d8bb" deduction?1?1?1?1 --custom-charset1=?l?d?u --potfile-disable`, I resumed the command I used for Deadpool, just modifying the character searched to match the hint: beginning with "deduction", 3 digits, 10 letters (so upper/lower).
<img width="463" height="158" alt="image" src="https://github.com/user-attachments/assets/f44b212c-10cc-4f53-839d-913f04137b5a" />

## genius@starkindustries.com - reserver
### Password: iamironman
`hashcat -O -m 0 -a 0 "d50ba4dd3fe42e17e9faa9ec29f89708" rockyou.txt --force --potfile-disable` again, did the same than before for "found with a dictionnary attack".
<img width="461" height="237" alt="image" src="https://github.com/user-attachments/assets/c7bc3f1c-1c71-479a-afdd-07a7faf14fa4" />

## whysoserious@gothamchaos.net - administrator
### Password: chaos123!
`hashcat -m 0 -a 3 "f158d479ee181aac68b000a60e7a3d7a" chaos?a?a?a! --potfile-disable` because the hint said "mixed characters", I just placed ?a mask, meaning letters, digits and symbols. Hint also said 9 character, beginning with "chaos", finishing with "!", so I placed them were they belong.
<img width="466" height="117" alt="image" src="https://github.com/user-attachments/assets/266ab464-0b6f-4eb6-8cd6-b5492f1d88ff" />

## quackattack@duckburg.org - reserver
### Password: mickeyisjealous
`hashcat -m 0 -a 3 "ea261222d4867b3ebdfadbe2b35e19d5" ?l?l?l?l?l?lisjealous --potfile-disable`, nothing new here, the hint said 15 lowercase, so ?l mask, and finishing with "isjealous".
<img width="462" height="155" alt="image" src="https://github.com/user-attachments/assets/54dd8f9a-91e4-4666-b3ba-8b705259135d" />

## ruhroh@mysterymachine.com - reserver
### Password: 
`hashcat -m 0 -a 3 "ad17fbd845000b11678ccbf94e135b56" ?l?l?l?l?l?l?dscooby --potfile-disable` as indicated by the hint, it contains 6 lowercase, then 1 digit, then "scooby".
<img width="462" height="148" alt="image" src="https://github.com/user-attachments/assets/fb35924e-6826-4908-af9e-ae9ce6ebb92f" />

## What is the main difference between Dictionary and Non-Dictionary attacks?
Non-dictionnary attacks build all the possibilities by making each combination possible, where dictionnary attacks use a prepared set of words, of combination to test, making the task less costly.

## What advantage does an attacker gain by having access to the system’s database that reveals the users and the password hashes?
With users roles, he have better informations to target a user, helping him to gather infos on him. And with the hashes, he can try password combinations on his own machine before trying to log in the system and maybe triggering intruder detections by numerous login tries.

## What concrete security benefits are achieved by using longer passwords instead of shorter ones?
With size, combinations to test for cracking goes exponential, making the attacker spend lot more time on password cracking.
