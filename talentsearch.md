# Munich Reinsurance TalentSearch (name pending)

<!-- TOC -->

- [Munich Reinsurance TalentSearch (name pending)](#munich-reinsurance-talentsearch-name-pending)
  - [Project Outline](#project-outline)
    - [Core Functionalities](#core-functionalities)
    - [Non-Functionalities](#non-functionalities)
    - [User Roles](#user-roles)
      - [Role 1: Asset](#role-1-asset)
      - [Role 2: Project Manager](#role-2-project-manager)
      - [Role 3: Administrator](#role-3-administrator)
    - [Application Structure](#application-structure)
      - [Pages](#pages)
        - [Profile Page](#profile-page)
        - [Project Page](#project-page)
        - [Role Search Page](#role-search-page)
        - [Asset Search Page](#asset-search-page)
    - [Skills System](#skills-system)
    - [Roles System](#roles-system)
    - [Time Management System](#time-management-system)

<!-- /TOC -->

This is a conceptual design document for Munich Re TalentSearch.  TalentSearch is a proposed resource-allocation application for internal use within Munich Reinsurance and its subsidiaries.  TalentSearch would provide features to document user skillsets and allow the matching of those skillsets to the needs of current projects (both technical and nontechnical).  TalentSearch would also provide basic time-management functionality to allow users to indicate their capacity for additional work.

## Project Outline

### Core Functionalities
	
TalentSearch will provide the following core functionalities:

* Track user skills, interests, projects, and available work capacity through a simple, easy-to-use profile page.
* Track project requirements through a "role-based" interface, allowing the factoring of project requirements into roles with associated skillsets, and the matching of user profiles to those skillsets.
* Allow users to search available project roles based on their skillsets.
* Allow project managers to search available users based on the skillsets required by their projects.
* Allow the assignment of users to roles, and the tracking of past roles filled by users.

### Non-Functionalities

In order to prevent scope-creep, it is important to note what TalentSearch is *not* intended to do.  TalentSearch will *not*:

* Provide detailed project management and organization functionality (e.g. todo lists, messaging, announcements, scheduling, sprint management, etc).  This should be done using other software - TalentSearch exists to facilitate the *matching of users to projects*; it is not intended to manage the *internal logistics of those projects*.
* Provide user-to-user communication, except through role requests and assignments.  The application will expose contact information (e.g. company email addresses and skype) - detailed communication should be carried out through those channels, and will not be done through the application.
* Publicly document project status (e.g. "project blog"-type functionality or publicly-visible "popularity" or "interest" rankings).  TalentSearch is not intended to provide a way to "keep tabs" on the goings-on of various projects - it is *strictly* intended for asset management.

### User Roles

To accomplish the core functionalities, TalentSearch will be based on a hierarchical three-level user role design.

#### Role 1: Asset

The *asset* role is the base role assigned to every TalentSearch user.  Users with the *asset* role can do the following:

* Edit their profiles to reflect their skills, interests, projects, and available time.
* Search available project roles based on their profile skills.
* Request available project roles that fit their profile skills.

#### Role 2: Project Manager

The *project manager* role is assigned to users in charge of a project listed on TalentSearch.  Users with the *project manager* role can do the following (in addition to the permissions of the *asset* role):

* Manage and configure the relevant project page.  Includes, but is not limited to:
    * Defining project roles and associated skillsets.
    * Modifying project description/information.
* Search for users whose skillsets match required project roles.
* View role requests from assets for their managed project.
* Compile "candidate lists" of users who seem to be a likely fit for a given project role, pending approval and assignment by an administrator (see below).

#### Role 3: Administrator

The *administrator* role is assigned to users who have the final say in asset allocation and project oversight.  Users with the *administrator* role can do the following (in addition to the permissions of the *asset* and *project manager* roles):

* Create new projects
* Assign project managers to projects.
* Assign assets to project roles.

### Application Structure

This section describes the core structural elements of the TalentSearch application.

#### Pages

The TalentSearch application will be structured around the following pages.  Rough mock-ups of the most important of these pages may be found here:

https://tpnmgz.axshare.com/
password: ultrapower

##### Profile Page

The *profile page* will serve as a typical user's "homepage."  The profile page will contain:

* A user portrait
* A brief user bio
* A list of the user's skills (for more information, see [here](#skills-system)).
* A list of the user's project interests.
* A list of the user's current projects.
* The user's current time availability.

##### Project Page

The *project page* describes a given project, and displays the available (and filled) roles for that project.  The project page will contain:

* A project summary describing the project's purpose and context within Munich Re.
* A skill-searchable list of project roles (for more information, see [here](#roles-system)).
* A list of assets currently working on the project.
* Contact information for the project manager.

The role list will be interactively-sortable through clickable skill-selections, and also provide an "auto-match" feature to import skill selections from a user's profile.

##### Role Search Page

The *role search page* will allow users to search available roles that match specified skills.  Each role will link to its corresponding project page.

##### Asset Search Page

The *asset search page* will allow project managers and administrators to search for assets who match the skills needed by project roles.

### Skills System

The core of TalentSearch's functionality is the *skills system*, which forms the basis of the matching of assets to roles.

The skills system will be based primarily on user selections from pre-populated lists of available skills.  The choice of pre-populated (rather than freeform) will allow for much more-powerful and seamless search and filtering functionality, which is *crucial* for the application to satisfy its core design requirement of matching assets to available roles.

Skills will be separated into "hard skills" and "soft skills," per the usual definition of these terms.  "Hard skills" may be further separated by problem-space (e.g. "programming," "underwriting," "actuarial skills," etc).

Skill proficiency will be indicated on a ranked scale.  To facilitate ease of integration into search features and to eliminate needless slop, a relatively coarse ranking system will be preferred (e.g. a 3-valued ranking system: "beginner," "comfortable," and "experienced").

A freeform "other skills" category may be provided for assets to document skills that are not accounted-for in the application; these will not be used for search functionality, but can be read and considered by project managers and administrators.

A mechanism will be provided for users to suggest skills to be added to the existing skills list for selection and integration with search features.

Skills will be displayed in a cohesive way throughout the application.  When skills lists are provided in a search context, skills matching the search will be highlighted and placed first in the list display, to provide an easy visual reference for the "degree of match" between the user's skillset and the role skillset.

### Roles System

The skills system must interact seemlessly with a *roles system* in order for users to be effectively matched to project roles consonant with their skillsets.

Roles correspond to a specific job on an existing project.  Roles may be displayed on the project page, role search page, *or* user page - it is crucial that the role display be consistent across contexts for application cohesion.

Roles will typically be displayed as "panels" in a vertically-scrollable list.  Each panel will display:

* The role name
* A brief description of the role
* The project name
* The skills required by the role.
* The time commitment required by the role (for more information, see [here](#time-management-system)).

Role panels will be clickable, and on click will expand to provide more-detailed information about the role.  Clickable expansion is highly-compatible with display in a vertically-scrollable list.  Display of skills within a role panel will be consistent with the aforementioned rules for skill display.

### Time Management System

TalentSearch will also provide a basic *time-management system* to allow project managers and administrators to have some notion of the availability of an asset for a given role.  The TalentSearch time management system will support the following features:

* Specify an estimation of the weekly time requirements of a project role
* Specify an estimation of the weekly time availability of an asset
* Emit a warning when a role is assigned that will cause an "over-alottment" of time resources.

It is important to stress that, as TalentSearch is *not* a full project management suite, this functionality (while important) will remain as basic in implementation as can be managed while still fulfilling these goals.  The TalentSearch time management system should *not* be relied on to track user hours for purposes other than ascertaining the user's availability to be added to a new project.
