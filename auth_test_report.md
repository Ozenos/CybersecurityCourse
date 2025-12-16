## 🧑‍🦲 **Guest**

### Main page
Display regular interface showing logging zone, ressource and reservation adding, and list of booked ressources. Do not display reserver's names on reserved ressources. Button to add resources and reservations are blocked.

✅

### Logging zone
Login and register buttons leads to appropriate pages and functions. Can create account and use it again after logout.
Cannot register if under 15 years old.

✅

### Invalid URL
Accessing unknow pages like `/asdaf` return error page. Notice that the error page name is "Staus", probably a mispell of "Status".

✅ Correct common behavior to avoir users to find unauthorized pages.

### Unauthorized pages
Accessing unauthorized page like `/reservation` return the error page.
But pages like `/api/users` or `/api/resources` show private content without error message. `/ressources` display regular interactible form page.
Fortunately, trying to access reservation modification page by its address (`/reservation?id=1`) displays the error page.

❌ Guests can access unauthorized content.

✅ `/reservation` return error page.

## Summary of Guest:
Can view application infos except personnal data, and no interaction is possible except for logging. But access control issues allows guests to display and interact with unauthorized content.

---

## 🧑‍💼 **Reserver**

### Main page
Display same interface as **Guest**. List reservations with ressource names, starting and ending time, but have the reserver.

### Add a new ressource
User can acces the `/resources` using the **Add a new ressource** on the main page. It opens a form that request a title and a description.
Submitting form sends us back to the main page and add the resource to the list.

❌ This behavior is not specified in specs description, and so is not supposed to be possible.

### Add a new reservation
User can acces the `/reservation` using the **Add a new reservation** on the main page. It opens a form that request username, the ressource, hours and minutes.
Submitting form sends us back to the main page. And now display the reserved ressource in the list.
There is no error detected by doing an overlap, but doing a reservation that end before starting time return an error on a black screen.
Clicking our reservations leads to an edit of it, allowing to update or delete the reservation.

✅ Reservation is possible, as intended.

❌ Overlap is not detected and multiple reservation at the same time are possible

❌ By submitting reservation that end before start, display an error screen that is not configured.

❌ It is possible to specify minutes on reservation, but "7. Resources can be booked on an hourly basis.", and so not on minutes should be possible.

### Log out
Clocking *Log Out* button or writing /logout in address leads us to the main page without account. Clicking button, changing from pages does not log us again in previous account.

✅

### Invalid URL
Accessing unknow pages like `/asdaf` return error page. Notice that the error page name is "Staus", probably a mispell of "Status".

✅ Correct common behavior to avoir users to find unauthorized pages.

### Unauthorized page
Accessing page like `/reservation` display content of the main page, which could be an issue as it displays informations on database structure.
Unauthorized pages like `/api/users` or `/api/resources` show private content without error message.
It is possible to access reservation modification page by its address (`/reservation?id=1`), bypassing the need to be the reserver of the reservation to access it.

❌ Guests can access unauthorized content.

## Summary of Reserver:
Can view application infos, interactions are functionnal. But access control issues allows guests to display and interact with unauthorized content.

---

## 🧑‍💼🛡️ **Administrator**

### Main page
Display same interface as **Guest**. List reservations with ressource names, starting and ending time, and the reserver.

✅

### Add a new ressource / Add a new reservation / Log out
Same as reserver, but allow to modify any reservation without need to be the reserver.

✅

### Admin pages
Not any of the links `/admin/resources/new`, `/admin/users/delete/:id`, `/admin/reservations` leads to a usable page.
No informations under admin to access admin pages.

❌ no admin page utilities for macro actions

## Summary of Administrator:
Can view application infos, interactions are functionnal, but no macro admin actions can be performed.

---

## Recap on specs

1. The system is accessed via a web browser. ✅
2. Users can register and, after registration, log in to the system. ✅
3. A registered and logged-in user acts as either a resource reserver or an administrator. ✅
4. The administrator can add, remove, and modify resources and reservations. ✅
5. The administrator can delete the reserver. ❌
6. A reserver can book a resource if they are over 15 years old. ✅ cannot create an account if so.
7. Resources can be booked on an hourly basis. ❌ actually a minute basis.
8. The booking system displays booked resources without requiring login, but does not show the reserver's identity. ✅
-> ❌ Access control issues allows access to unauthorized/sensible pages from reserver or guest.

---

## Discovered endpoints

and access from roles.

| Refered in doc | address | Admin | Reserver | Guest | Find with |
| Main page | `http://localhost:8003` | interact | interact | access | N/A |
| Logging zone | /login | N/A | N/A | interact | button on main page |
| Logging zone | /register | N/A | N/A | interact | button on main page |
| Temporary page | /logout | access | access | N/A | button on main page |
| New resource | /resources | interact | interact | access by URL - interact | button on main page |
| New reservation | /reservation | interact | interact | inaccessible | button on main page |
| API | /api/reservations | access by URL | access by URL | access by URL | Gobuster |
| API | /api/resources | access by URL | access by URL | access by URL | Gobuster |
| API | /api/session | access by URL | access by URL | access by URL - error printed | Gobuster |
| API | /api/users | access by URL | access by URL | access by URL | Gobuster |

interact : can access and interact with the page, like submitting form.
access : can gain access to the page normally (if else, specified)
