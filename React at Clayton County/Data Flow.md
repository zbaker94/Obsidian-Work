When working with "external" data, it is important to retrieve that data as close to where is is used as possible. This will partially be dictated by your api design. Take the following example of a page that shows a user's news feed:

![[Pasted image 20230830101616.png]]

Depending on how your api is designed and your overall UX guidelines, you may fetch your data in any number of these components.

##### Where would you fetch the data for this page if you fetched all the data at once from a `/newsFeed?userid=x` endpoint?
##### answer
This is an easy one, just fetch the data at the top level in `NewsFeedPage`
![[Pasted image 20230830102340.png]]
Ignoring the obvious performance implications, this of course raises the question of how we will propagate all of that data to the components that need it. This is where using a [[Context Provider]] would come in handy.
##### What if the information for a user (profile image, name, notifications) is fetched from a separate endpoint?
##### answer
This one is a bit trickier than it may originally appear. Since we need the user data in both `Notifications` and `Profile`, we could fetch the data in both places but that means we will be fetching and refetching the same data in two sibling components. Instead of this we unfortunately have to fetch both types of data at the very top level
![[Pasted image 20230830103000.png]]
There could be consideration for wrapping both `Notifications` and `Profile` in a shared parent. This is a bad practice to get into namely because it introduces a component into our tree that has no semantic meaning to the final rendered page. 

##### What if `CreateNewPost` requires the users profile image as well?
##### answer
You may be noticing a trend. We now have 3 places where the users data is needed. All of which only share the topmost component as an ancestor. The answer here is the same as above, we still need to fetch both types of data at the top level.

##### What if notifications are fetched separately?
##### answer
Great news! we can now change our code to fetch just the notifications from the `Notifications` component! We still have to keep the user data at the top level and pass it around, though...


The last example may cause you to think that the best solution to this headache is to make every atomic section of the ui call its own endpoint. We would have a call for 
- User Data
- Navigation
- Notifications 
- PostList 
Each within only the component that uses them.

But wait, we still need to provide the profile image to `CreateNewPost` and we most certainly want to avoid redundant fetches. So what, then? Do we make a separate endpoint just for the profile image?

While this approach may work for some apps and while also technologies like [[GraphQL]] and [[tRPC]] exist, generally, this approach is a maintenance nightmare and breaks down once components need to fetch and refetch the same data.

This is where [[React Query]] comes in.

React Query manages the caching (and invalidation of the cache) for your entire app at the very top level. It does this by matching certain fetch functions to "query keys". Arrays of values that are evaluated in much the same way as the dependencies array for [[UseEffect]] and [[UseMemo]]. Furthermore, since React Query manages the state of any given cache, we can easily keep track of whether some data is fetching, has never fetched, etc. 

This means we can have whatever shape of data we need from any number of external sources and (assuming we set up the correct rules for refetching) simply access it from wherever it is needed.

Going back to our example, we can setup our data flow like so:
![[Pasted image 20230830104645.png]]
In this way, we can design our api and UI to reflect the business needs rather than the nuts and bolts of implementation. Each component that needs data from a given source can simply ask React Query for that data and if that data has already been fetched (and is not stale), the component receives it. Likewise if the data is fetching or in an error state, the component receives the relevant information so that the UI can reflect it. When the data is refetched for any reason, each consuming component is notified that the data is fetching *and* will receive the new data when it is available.

### References:
https://tanstack.com/query/latest/docs/react/guides/important-defaults