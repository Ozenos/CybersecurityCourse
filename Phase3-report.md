### 🧑‍🦲 **Guest**

## Main page
Display regular interface showing logging zone, ressource and reservation adding, and list of booked ressources. Do not display reserver's names on reserved ressources.
✅

## Logging zone
Login and register buttons leads to appropriate pages and functions. Can create account and use it again after logout.
✅

## Invalid URL
Accessing unknow pages like `/asdaf` return error page. Notice that the error page name is "Staus", probably a mispell of "Status".
✅ Correct common behavior to avoir users to find unauthorized pages.

## Unauthorized page
Accessing unauthorized pages like `/admin/users` or `/admin/users:id` return the error page.
Works as well for `/reservations` and `/ressources`.
✅ Correct common behavior to avoid users to find unauthorized pages.

---

### 🧑‍💼 **Reserver**

## Main page
Display same interface as **Guest**. List reservations with ressource names, starting and ending time, and the reserver.

## Add a new ressource
User can acces the `/ressource` using the **Add a new ressource** on the main page. It opens a form that request a title and a description.
Submitting form sends us back to the main page.
`/api/ressources` print a dark page with `{"error":"Not Found"}`.
❌ This behavior is not specified in specs description, and so is not supposed to be possible.

## Add a new reservation
User can acces the `/reservation` using the **Add a new reservation** on the main page. It opens a form that request username, the ressource, hours and minutes.
Submitting form sends us back to the main page. And now display the reserved ressource in the list.
There is no error detected by doing an overlap.
✅ Reservation is possible, as intended.
❌ Overlap is not detected and multiple reservation at the same time are possible
❌ It is possible to specify minutes on reservation, but "7. Resources can be booked on an hourly basis.", and so not on minutes should be possible.

## Log out
Clocking `Log Out` button leads us to the main page without account. Clicking button, changing from pages does not log us again in previous account.
✅

## Invalid URL
Accessing unknow pages like `/asdaf` return error page. Notice that the error page name is "Staus", probably a mispell of "Status".
✅ Correct common behavior to avoir users to find unauthorized pages.

## Unauthorized page
Accessing unauthorized pages like `/admin/users` or `/admin/users:id` return the error page.
✅ Correct common behavior to avoid users to find unauthorized pages.

---

### 🧑‍💼🛡️ **Administrator**

## Main page
Display same interface as **Guest**. List reservations with ressource names, starting and ending time, and the reserver.
✅

## Add a new ressource / Add a new reservation / Log out
Same as reserver.

## Admin pages
Not any of the links `/admin/resources/new`, `/admin/users/delete/:id`, `/admin/reservations` leads to a usable page.
❌ no admin utilities

---

### Recap
