# Web App Restful-API System Design

### 1- Describe high level design
Show the main note app components and the logical interactions that will fulfill the requirements.

Create a notes system with user authentication where users can save, list and delete their notes through a RESTful API.

**Resources:**
* Save Note: Creates a new note with the title and the content.
* List Notes: Returns all notes from the authenticated user.
* Delete Note: Removes a specific note from the authenticated user.

**Authentication:**
The system will use JWT authentication to ensure that only logged in users can access resources, it will be requided in all requests.

### 2. Web App UI
The Web App UI will be very simple and cleaner for users. 
Initial the app show a login screen. The user will fill the nickname, password and click the Login button, for new users will have a button to register. After the user logged, the user will access the principal scream that it will show a list of all saved notes with a button to create a new one. When the user access into the note it will appear the 2 buttons. One with the function to back to list all notes Screem and other to delete de note in red color.  

**Login Scream**
This screan will have 4 components. 
  1. Label input for nickname. 
  2. Password Input for the password.
  3. A button to login 
  4. A link to redirect to Register screan. 

**Main Screan**
This screan will have 3 components. 
 1. Header component, will show the first name of user and a button to logout. 
 2. List Notes component 
 3. New Note button component 

**Note Screan**
This screan will have 4 components
 1. Header Component, will show the Title of the note. 
 2. The Body Note Component. 
 3. The Backspace Button Component.
 4. The Delete Button Component. 


### 3. Data Model
For the Note App System, we need to support the following queries: 
Query 1 : List all notes. 
Query 2:  Record a new Note. 
Query 3 : Delete a note.

A relational database (RDB) will be used. A RDB can easily model the data. The structure of the business data is very clear and the relationship between the only two entities (user, note) is stable.  

#### Entity Relationship Model 
![image](https://github.com/LucianoTulio/Web-App-Restful-API-System-Design/assets/3699130/7e3a9ab8-1202-4b62-85c7-ce452726e233)


### 4. Restful API
For the Note app it will have only 4 endpoints. The only route that won't required Authentication is the Loging. All the others route will be required a Valid JWT to ensure that only logged users can acess the resources.    

***Login:*** 
Method: POST
Address: /login
Request body: (x-www-form-urlencoded)
nickname: (string) The user nickname
password: (string) The user password

***Save Note***   
Method: POST
Address: /notes
Header: Beare token (valid JWT)
Request body:
content: (string) Content of the note.

***List Notes:***
Method: GET
Address: /notes
Header: Beare token (valid JWT)

***Delete Note:***
Method: DELETE
Address: /notes/{id}
Header: Beare token (valid JWT)
Route parameter:
id: (integer) ID of the note to be deleted.


### 5. Web Server
We use the microservice architecture for this Notes App System. This is the High-level design. 
![FEEFO](https://github.com/LucianoTulio/Web-App-Restful-API-System-Design/assets/3699130/72d163fe-a90b-4f44-a64e-3b717dec62d0)

We will show a briefing over each component of the system from top to bottom.
**User:** a user to list, create and delet notes on their computer or mobile phone. 

**Public API Gateway:** this is a fully managed service that supports authentication, rate limiting, route managment and other functionality to imnprove the security.
**Notes System Service:** Service in charge to keep the Notes Information. Create, List and Delete Notes. And service in charge to keep the User Information. Create and update information of users. 

**Notes System Database:** A relationship database to keep all informations.




