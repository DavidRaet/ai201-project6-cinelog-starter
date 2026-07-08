# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->

## Comment 1 — Rename
**What I did:** 

Rename the save_to_watchlist function in services/watchlist_service.py to add_to_watchlist, and update all references to this function throughout the codebase. 

**How I verified:** 

I verified that the function was renamed correctly by running the test suite and ensuring all tests passed. I also searched the codebase for any remaining references to save_to_watchlist and confirmed that they were updated to add_to_watchlist.

## Comment 2 — Deduplication
**What I did:**

I added a check in the add_to_watchlist function to prevent duplicate entries from being added to the watchlist by checking if the movie ID already exists in the user's watchlist before adding it. If it does exist, the function returns a message using the AlreadyInCollectionError exception.

**How I verified:**

I verified that the deduplication logic works by writing a test case (this will added upon addressing comment 3) that attempts to add a duplicate movie ID to the watchlist and checks that the AlreadyInCollectionError exception is raised. 

## Comment 3 — Missing test

**What I did:**

I added another test file, tests/test_watchlist.py, to cover the deduplication logic in the add_to_watchlist function along with similar tests seen in tests/test_collection.py. The test cases include adding a movie to the watchlist, attempting to add a duplicate movie, and adding a non-existent movie ID, 

**How I verified:**

I verified that the new test cases pass by running the test suite and ensuring that all tests in tests/test_watchlist.py pass successfully and that they don't interfere with existing tests in tests/test_collection.py. 



## Comment 4 — Default visibility

**My position:**

I believe that the default visibility of the watchlist should be public by default.

**Reasoning:**

Having a public default visibility allows users to share their watchlists with friends and the community, which can enhance engagement and provide social value. By nature, watchlists are often shared and discussed among users, and making them public by default encourages this behavior. However, if users prefer privacy, they can easily change the visibility settings to private after creating their watchlist. This approach balances social engagement with user control over privacy.

**Tradeoff acknowledged:**

A public default visibility may also require the user to take an extra step to make their watchlist private if they prefer not to share it, which could be seen as a minor inconvenience. However, I believe the benefits of social engagement and discoverability outweigh this tradeoff.

## Comment 5 — Sort order

**My position:**

I believe that the watchlist should be sorted by date added in descending order by default.

**Reasoning:**

As per Jamila's comment, sorting by date added in descending order allows users to see the most recently added movies at the top of their watchlist. This is particularly useful for users who frequently update their watchlists and want to quickly access their latest additions. 

**Engagement with reviewer's point:**

I agree with Jamila's point about the importance of seeing the most recently added movies first. From a user experience perspective, this sorting order aligns with common user expectations and behaviors when managing lists.  

## Comment 6 — Rebase
**What conflicted:**

- The .gitignore file had conflicts, but from the branch I was rebasing onto, the .gitignore file had all the necessary entries, so I kept the version from the branch I was rebasing onto.

- The services/watchlist_service.py and routes/watchlist_routes.py file had conflicts because of the naming change from save_to_watchlist to add_to_watchlist along with any references to this function throughout the file. 

**How I resolved it:**

I resolved the conflicts by keeping the version of the .gitignore file from the branch I was rebasing onto, as it contained all the necessary entries. For the services/watchlist_service.py and routes/watchlist_routes.py files, I manually merged the changes by ensuring that all references to save_to_watchlist were updated to add_to_watchlist.

**How I verified no conflict remains:**

I verified by running git status to ensure there were no remaining conflicts and that the working directory was clean. I also ran the test suite to confirm that all tests passed successfully, indicating that the codebase was in a stable state after resolving the conflicts. If running git rebase --continue introduced any new conflicts, I would repeat the conflict resolution process until the rebase was complete and all conflicts were resolved.

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->

    The watchlist feature allows users to add movies to a personal watchlist, view their watchlist, and manage the visibility of their watchlist. Additionally, any duplicate entries are prevented from being added to the watchlist, ensuring that each movie appears only once. 
    
    Default visibility is set to public, allowing users to share their watchlists with others. Although users who prefer privacy may find it inconvenient to have to change the visibility setting to private once creating the watchlist, the benefits of social engagement and discoverability outweigh this tradeoff. 
    
    The watchlist is also sorted by date added in descending order by default, allowing users to see the most recently added movies at the top of their watchlist. This sorting order aligns with common user expectations and behaviors when managing lists. 

    To test the features, you can run pytest tests/ to run the entire test suite, if you choose to run tests individually, you can run pytest tests/test_watchlist.py or pytest tests/test_collection.py to run the tests for the watchlist and collection features, respectively. 
    
    You can also manually test the endpoints using a tool like Postman or curl. For example, you can use the GET /watchlist/<user_id> endpoint to view a user's watchlist, the POST /watchlist/<user_id>/add endpoint to add a movie to the watchlist, and the DELETE /watchlist/<user_id>/remove endpoint to remove a movie from the watchlist. You can also test the visibility settings by using the PUT /watchlist/<user_id>/visibility endpoint to change the visibility of the watchlist.