**Problem**
- Some users have the incorrect state (users array from server)(should be "PA")

**Checklist**
- [ ] In then block make a conditional statement:
  - [ ] Assign id to user_id, I'll need this for related objects
  - [ ] Map through the users, 
    - [ ] looking at user_id.state in particular
  - [ ] If the user_id's state isn't "PA", then user_id.state: "PA"
  - [ ] user_id.last_modified: Date()
  - [ ] Return the results of saving this to the server (consider saving this 'til the end)
  - [ ] In next then block, display success message
  - [ ] In catch block, display error message

**Problem**
- Some users hobby records are missing experience level

**Checklist**
- [ ] Map through the hobbies, sorted by user_id
  - [ ] For each hobby, if "experience_level" is missing
    - [ ] If years_played = 1, then experience_level = 'beginner'
    - [ ] If years_played = 2, then experience_level = 'advanced'
    - [ ] If years_played = 3, then experience_level = 'expert'
  - [ ] hobbies.user_id.experience_level: experience_level
  - [ ] hobbies.last_modified: Date()
  

**Problem**
- Some favorites are missing types. If missing, this should be set to "other".

**Checklist**
- [ ] Map through the favorites, sorted by the user_id
  - [ ] For each favorite, if "type" is missing:
  - [ ] favorites.user_id.experience_level: "other"
  - [ ] favorites.last_modified: Date()
  
**Problem**
- Update the server with new values

**Checklist**
- [ ] Map through the users
  - [ ] If user_id.last_modified: Now() then:
    - [ ] Place user into update array

**Problem**
- Error Checking

**Checklist**
- [ ] Check for errors

**Problem**
- Print out all data for each user in order

**Checklist**
- [ ] Print
