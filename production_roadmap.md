# TalentSearch Production Roadmap

## Frontend

### Critical

* Full editability on all pages
  * Conditional editability based on permissions
  * Clean, unobtrusive edit interface (no large buttons)
* Error handling
  * Code-wise consistency (look up how to do this in react) - errors should generally "fall through" to a component that catches them in a managed way
  * UI-wise consistency (error dialogues should have a consistent look and not be horrendously scary to the user)
* Code cleanliness and documentation
  * TSDocs on important functions
  * Reduce repetition, genericize components when possible
  * Decompose large components into multiple smaller components
  * Restructure directory tree
    * "Components" tab only for components reused on multiple screens
    * Rename "model" to "data"
    * Reduce number of functions in each module
* Email integration (bring up outlook window)
* Styling, formatting, etc

### Important

* Saved user preferences
  * Saved searches
  * Candidate lists
* PM Dashboard
  * Show vacant roles, easy access to candidate lists
* Search from role card
  * Clickable search button on role card
  * Searches for skills, filters by profile skills and location
* Search from profile screen
  * Clickable search button on profile screen
  * Searches for skills, filters by role skills and location
* Profile pictures

### Reach

* Search profiles by previous roles (requires major backend work)

## Backend

### Critical

* Finalize beta permissions model (requires meeting w/ Marija, Jim, etc).
* Finalize beta data model (requires meeting w/ Marija, Jim, etc).
* Move multi-step data procedures to db storedprocs for atomicity
* Implement repair/reaper scripts for data consistency
* Use Azure cognitivesearch instead of fuse.js (requires azure permissions!)
* Import user account data from existing source (requires openIDs!)

### Important

* Saved user preferences
  * Saved searches
  * Candidate lists
* Profile pictures
  * Blob storage?

### Reach

* Increased denormalization for additional search functionality
  * Requires extreme care to avoid cyclic data dependencies
