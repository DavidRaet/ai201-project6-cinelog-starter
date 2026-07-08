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
**How I verified:**

## Comment 4 — Default visibility
**My position:**
**Reasoning:**
**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**
**Reasoning:**
**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->