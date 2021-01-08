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
