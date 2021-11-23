# Click Calendars - Scheduling Software

## Site Structure

### Page layout for users
Home, contact, and login pages available to all,
Home, contact, logout, download, and availability pages available to base users,
Home, contact, logout, download, availability, scheduling, employee managment, and account creation pages available for admin users

### Backend server structure
- App.js
    - Routes.js
        - UserController.js
            - All site pages
                - Site data (JS, CSS, Img)

### Database
All data is stored in MySQL (Maria DB after Bitnami changed support for MySQL) databases unique to the organization, and tables unique to the task/data.
The database structure is defined in dependencies.txt using create statements.
Features include a dependency of a single accounts table that with the employee number key being listed as a foreign key that cascades on delete to remove all data about one employee after the employee has been removed of the account table.

Database : Organization Name

New table for login : Admin (enum, name, email, hash)
    If the user has a valid admin account they will have acess to all features and all sub-direcctory pages
    For example : Adding base level employees, making the schedules

Table for Login : Accounts (enum, name, email, hash) 
    This is used only for logging in and registering a user on registerUser

Table for employee managament : Employees (id, enum, fullName, authLevel)
    This is used for managing all aspects of staff ( adding new employees on managment page, promoting, deleting employees )

Table for week schedule : WeekName (id, enum, fullName, sundayStart, sundayEnd...

Table for availability : Day (enum, insertTime, start, end)

#### Database features
- Timestamps
- Employee number in accounts on delete cascade

### Sample
Vist login page -> Serve login page (Get request) -> Send Login -> Validator checks for bad actors or corrupt data -> API request to module querying MySQL account databases, checking login and password hashes (Post request) -> Set token -> Redirect to home page of schedule with valid token -> Serve home page (Get request) -> ... 

## Features
- Quick diferential from base users and admins allowing for an ease of use throught the same base site
- Add your schedule to any calendar program (Apple, Google, Outlook, etc) due to support for turning your schedule into a .ics file adhering to RFC 5545 (ICalendar Standard)
- Support for multiple organizations stored on unique databases on a single server
- Easy to use interface for adding shifts that features a button to remove 'Edit' buttons alongside a print button to allow for quick printing from the same interface that you are using to build the schedule
- When adding shifts for particular members of an organization that have set availability, their availability will display below the time dropdown for the shift to remind the user of requested time parameters
- All dropdowns on edit schedule and availability pages are tab indexed to allow for extremly quick, mouseless data entry
- Backend built using Node JS to allow for quick, asynchronous code

## Release Date
Unfourtunately some aspects of the software are still in the testing phase so a release date has not been set for when the software is ready for full scale production.

## Author
- Colin McCormack, colin.william.mccormack@gmail.com

