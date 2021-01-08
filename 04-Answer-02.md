**Problem**
- Some users have the incorrect state (users array from server)(should be "PA")

**Checklist**
- [ ] In then block make a conditional statement:
  - [ ] Assign id to user_id, I'll need this for related objects
  - [ ] Map through the users, 
    - [ ] looking at user_id.state in particular
  - [ ] If the user_id's state isn't "PA", then updateUsers.user_id.state: "PA"
  - [ ] Return the results of saving this to the server (consider saving this 'til the end)
  - [ ] In next then block, display success message
  - [ ] In catch block, display error message

**Problem**
- Some users hobby records are missing experience level

**Checklist**
- [ ] Map through the hobbies, sorted by user_id
  - [ ] For each hobby, if experience_level is missing
    - [ ] If years_played = 1, then experience_level = 'beginner'
    - [ ] If years_played = 2, then experience_level = 'advanced'
    - [ ] If years_played = 3, then experience_level = 'expert'
- UPDATE hobbies.user_id.experience_level: experience_level
