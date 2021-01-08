** Problem: Some data is bad and needs to be corrected **

- [ ] 01. Acquire data, good and bad
- [ ] 02. Place data into development environment
- [ ] 03. Correct bad data, verify correctness, report the updates
- [ ] 04. Return the corrected data to the server
- [ ] 05. To verify correctness, report the updates to the console
 
**01. Problem: Bad data must be acquired from the server**
  - [ ] fetch() user data from the server
    - [ ] When the JSON data arrives, turn it into an array
    - [ ] Use the GET method for the "users" field
    - [ ] Assign user/id to user_id
      - [ ] GET the user_id
      - [ ] GET the user_id/name
      - [ ] GET the user_id/age
      - [ ] GET the user_id/birthday
      - [ ] GET the user_id/city
      - [ ] GET the user_id/state
      - [ ] GET the user_id/last_modified
     
      - [ ] GET the user_id/hobbies
    - [ ] Each hobby has an id: user_id/hobbies/id
    - [ ] user_id/hobbies/id/name
    - [ ] user_id/hobbies/id/experience_level
        - [ ] user_id/hobbies/id/experience_level/beginner
        - [ ] user_id/hobbies/id/experience_level/advanced
        - [ ] user_id/hobbies/id/experience_level/expert
    - [ ] user_id/hobbies/id/years_played
    - [ ] user_id/hobbies/id/last_modified
   
    - [ ] GET user_id/favorites (foods, games, tv, movies, whatever)
        - [ ] GET user_id/favorites/id/name
        - [ ] GET user_id/favorites/id/type
        - [ ] GET user_id/favorites/id/type/movie
        - [ ] GET user_id/favorites/id/type/game
        - [ ] GET user_id/favorites/id/type/tv
        - [ ] GET user_id/favorites/id/type/books
        - [ ] GET user_id/favorites/id/type/books/title
        - [ ] GET user_id/favorites/id/type/books/author
        - [ ] GET user_id/favorites/id/type/other
   
    - [ ] GET user_id/updateUser/id/[updated_field]
    - [ ] GET user_id/updateUser/id/[updated_field]/updated_from
    - [ ] GET user_id/updateUser/id/[updated_field]/updated_to
   
    - [ ] GET user_id/updateHobby/hobbies/id/name
        - [ ] GET user_id/updateHobby/payload/hobbies/id/name
        - [ ] GET user_id/updateHobby/payload/hobbies/id/experience_level
   
    - [ ] GET user_id/updateFavorite/payload
        - [ ] GET user_id/updateFavorite/payload/id/required
        - [ ] GET user_id/updateFavorite/payload/name
        - [ ] GET user_id/updateFavorite/payload/type
**02. Problem: Acquired data must be placed into a development environment for error correction**
- [ ] Place data in development environment for correction
**03. Problem: Correct bad data**
- [ ] Map through the users users.map((user_id) => { see the users });
- [ ] Drill down to the respective user's state
- [ ] If state is empty, then change "" to PA
- [ ] Update user_id.state.last_modified to current time stamp
- [ ] Drill down to the respective user's hobbies
- [ ] Drill down to the hobbies/id
- [ ] Drill down to the experience level
- [ ] Assign that value to a variable
- [ ] Drill down to the user's years_played
- [ ] Assign that value to a variable
- [ ] If the years_played >= 0 and <= 1 then experience_level = "beginner"
- [ ] If the years_played >  1 and < 5  then experience_level = "advanced"
- [ ] If the years_played >  5          then experience_level = "expert"

The updateHobby data indicates an interest to know what the old values are...
- I would like to record these values, just to be safe (but I won't yet). I'll ask about that.
- Each piece of changed data will be UPDATE(D). However, the payloads will be POST(ED).
- [ ] user_id/updateHobby/hobbies/id/name
- [ ] user_id/updateHobby/payload/hobbies/id/name
- [ ] user_id/updateHobby/payload/hobbies/id/experience_level

- [ ] Update user_id.hobbies.id.experience_level.last_modified to current time stamp

- [ ] GET user_id/updateHobby/hobbies/id/name
- [ ] GET user_id/updateHobby/payload/hobbies/id/name
- [ ] GET user_id/updateHobby/payload/hobbies/id/experience_level

- [ ] Drill down to the respective user's favorites
- [ ] If user.id.favorites.type is empty, then change it to "other"
- [ ] Update user_id.favorites.id.type.last_modified to current time stamp

**04: Problem: I need to send the updated data back to the server**
- [ ] Map through the data to find the last_modified time stamps that are later than when I got the data (from the Date, in the HTTP header: "acquired_date")
- [ ] Send that data back to the server in an UPDATE fetch request

- [ ] If user_id/hobbies/id/last_modified > acquired_date, then
- [ ] UPDATE the user_id.state
- [ ] UPDATE the user_id.last_modified
- [ ] UPDATE the user_id/hobbies
- [ ] Each hobby has an id: user_id/hobbies/id
- [ ] user_id/hobbies/id/name
- [ ] user_id/hobbies/id/experience_level
- [ ] user_id/hobbies/id/experience_level/beginner
- [ ] user_id/hobbies/id/experience_level/advanced
- [ ] user_id/hobbies/id/experience_level/expert
- [ ] user_id/hobbies/id/years_played
- [ ] user_id/hobbies/id/last_modified
- [ ] UPDATE user_id/favorites
- [ ] If user.id.favorites.type is empty, then change it to "other"
- [ ] Update user_id.favorites.id.type.last_modified to current time stamp

- [ ] POST user_id/updateHobby/hobbies/id/name
- [ ] POST user_id/updateHobby/payload/hobbies/id/name
- [ ] POST user_id/updateHobby/payload/hobbies/id/experience_level
- [ ] POST user_id/updateFavorite/payload
- [ ] POST user_id/updateFavorite/payload/id/required
- [ ] POST user_id/updateFavorite/payload/name
- [ ] POST user_id/updateFavorite/payload/type

**05: Report the corrections to the console**
- [ ] fetch() GET the updated users
- [ ] For each user with a last_modified date > acquired_date,
- [ ] console.log() their (before and after?, definitely the UPDATED and POSTED) data

Ok. This is the sort of thing we need to work through.  What you have is FAR too complicated and you are making some assumptions that have no bearing in what you currently know. In any problem, you need to avoid making assumptions without valid reason.  So, let's go through it and compare to what we know so far.  I want you to then **explain how you decided on each point**.

| Task Choice | Fact |
| ------ | ------ |
| Defines endpoints for singular fields. | The spec says we have 6 endpoints: 3 gets for and 3 updates. There is no reason to assume that an API would contain endpoints for singular fields.  |
| Place data into dev environment | What exactly is this step doing?  Doesn't simply fetching get the data to where it needs to be? I think we can see that is true by the fact that you have a single step for that one section |
| Turn JSON data into an array | The spec does not indicate the form the data will take.  HOWEVER, it is reasonable in this case to assume that it returns an array for endpoints which are plural because this is absolutely standard API convention|
| fetches data with a GET after updates | The spec clearly indicates that updates return the data with the needed modify field.  There is no reason to assume you need to do another call after updating |
| No task for handling errors | The spec is clear that if an endpoint failures it will return an error |

By guesstimation, I would say your task list about 90% longer than it needs to be, particularly for a first try with incomplete (which I purposefully excluded) knowledge.  I gave you an example of breaking down a problem.  Did it seem as specific as what you have here?

I am glad you are learning. But some of these things you missed are definitively defined in the spec.  There was no need to learn that get is different than update (not even from the REST verb perspective, simply by what **I** defined).  The spec CLEARLY says

> All update endpoints - on success, returns the record with last_modified updated

I will be updating the specification on the epic shortly.  I will let you know when, and how, to proceed.
