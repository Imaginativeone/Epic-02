One issue that needs to be worked on is the ability to solve a complex problem by breaking it down into parts.  It is very easy to get overwhelmed if we try to create solutions for everything all at once.  The better path is often to solve small portions of the whole task as if they are the **only** thing that matters.  Once we have these smaller parts working, we can then go back and refactor what we need to integrate it all together. Over time, it can become easier to know how to write these parts such that minimal refactoring is needed, but that just comes with time and experience.  Towards that end, you will be working on a complex task to practice this.

**Overview**

This task will simulate gathering data from a remote location, working with that data, returning it to the server to save, and finally displaying the results of the save.  "Endpoints" which will act as the server calls will be provided.

During development of a complex user management system, it was discovered that a number of details about many users are incorrect.  This needs to be corrected.

**Overall task**

Get all data from server, correct the data, and save data to server.  Print out all data for each user in order.  That is, print user 1's data, their hobbies, then their favorites, then move on to user 2, and so on.

---

**API Endpoints**

- All update endpoints
  - on success, returns the record with last_modified updated
  - on failure, returns an error

---

- users
  - returns basic information about the users
  - fields: id, name, age, city, state, last_modified
- hobbies
  - user hobbies
  - fields: id, user_id, name, experience_level, years_played, last_modified
    - experience_level limited to: beginner, advanced, expert
- favorites
  - user favorites (foods, games, tv, movies, whatever)
  - fields: id, user_id, name, type, last_modified
    - types limited to: movie, game, tv, books, other
- updateUsers
  - payload
    - an array of user objects
      - The user objects do not need to include all fields.  Any field/value pair passed will replace the existing values
- updateHobbies
  - payload
    - an array of hobby objects
      - The hobby objects do not need to include all fields.  Any field/value pair passed will replace the existing values
- updateFavorites
  - payload
    - an array of favorite objects
      - The favorite objects do not need to include all fields.  Any field/value pair passed will replace the existing values

**Data problems to correct**

- Some user records are missing the user's state.  Currently the system is only working in Pennsylvania, so any missing states should be set to 'PA'.
- Some user hobby records are missing experience_level. This should be set using the years_played field as follows:
  - 1 year: beginner
  - 2 years: advanced
  - 3 years: expert
- Some favorites are missing types. If missing, this should be set to 'other'.

**FINAL NOTE** The details of this Epic will be updated as we move along.  Much like real assignments, information which is needed may or may not be present at all times.
