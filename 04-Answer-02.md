**Problem**
- Some users have the incorrect state (users array from server)
  - If state is "PA", move on, otherwise make the payload variable "PA".

**Checklist**
- [ ] In then block make a conditional statement:
  - [ ] Assign id to user_id, I'll need this for related objects
  - [ ] If the user_id's state is PA, then move on.
  - [ ] If the user_id's state isn't PA, then updateUsers.users.id.state: "PA"
  - [ ] Return the results of saving this to the server (consider saving this 'til the end)
  - [ ] In next then block, display success message
  - [ ] In catch block, display error message

**Problem**
- Some users hobby records are missing experience level

**Checklist**
- [ ] Filter hobbies where the hobbies' user_id = the users' user_id
