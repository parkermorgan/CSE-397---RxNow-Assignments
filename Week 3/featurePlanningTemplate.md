# Feature Planning Report - Detail Design
<!-- Instructions
Please fill this out during your planning meeting.
Each member of the group should complete a feature every two weeks. You are encharge of ensuring that your feature is complete.

You need to make a copy of this file.
Name it the <FeatureNumber>_<Feature title>.md and
Put it in the <artifacts/<team>/project/engineering/detaileddesign directory
    where <team>, will be replace with your team's name 
    i.e. artifacts/RecSrv/project/engineering/methodology/02_UserProfile.md
-->

### Reference Information (10 pts)
---
* **Feature Title**: User Account Creation and Authentication
* **Feature Number**: PF1
* **Date**:  05/09/2026
* **Author**: 
* **Team Members**: 

| Role | Team member name|
-- | --
| Product Owner | |
| Scrum Master | |
| Tech Lead (Front-End) | Parker Morgan |
| Tech Lead (Back-End) | |
| Tech Lead (Database) | |
| Quality Assurance | | 
| CM/DM | | 
| Responsible Engineer | | 
| Responsible Engineer | | 


----
### Traceablility (10 pts)
* **Requirement Number** (SRS Ref #): <!-- https://mermaid.js.org/syntax/requirementDiagram.html -->
* **Design Number** (SDD Ref #): <!-- Suggestion: https://mermaid.js.org/syntax/c4.html -->
* **Test Plan** (TPD Ref #):
* **User Documnet** (Ref Section #):
* **Installation Document** (Ref #):
* **Software Developer Guide** (Ref #): 

----
### Agile Taksing Information (10 pts)
* **Epic Story**:
<!--Format:
As <<>>,
I want <<>>,
so that <<>> -->
* **Value**: 
* **Planned Delivery**: 
<!--Use https://mermaid.js.org/syntax/gitgraph.html -->
* **Schedule**:
<!-- Use https://mermaid.js.org/syntax/gantt.html -->
* **Known Dependancies/Obsticles**: 
* **GitHub**
    * **GitHub Issue Number**: 
    * **GitHub Branch**: 
    * **GitHub Project**: 


---
Detailed Design 
---
<!-- NOTE: Not all projects will follow the 3-Tier and MVC architecture, please find the corresponding functionality. You may use N/A for any of the them but you must provide a detailed reason. 
-->
### FrontEnd (20 pts)
**Workflow Description**: <!-- Use paragraph and https://mermaid.js.org/syntax/sequenceDiagram.html-->
The user initiates the authentication process by entering credentials into the `AuthComponent`. The `AuthController` captures this data and performs client-side validation to ensure the password meets the complexity requirements defined in the system security policies. Once validated, the `AuthService` (Back Interface) dispatches an asynchronous POST request to the API. Upon a successful authentication, the system stores the JWT token, updates the `UserAccount` model state, and redirects the user to the application dashboard.

```mermaid
sequenceDiagram
    participant U as User
    participant V as AuthView
    participant C as AuthControl
    participant S as AuthService
    participant B as Backend API

    U->>V: Enters Credentials
    V->>C: handleLogin(data)
    C->>C: validatePasswordRequirements()
    C->>S: postAuthentication(payload)
    S->>B: POST /api/auth/login
    B-->>S: 200 OK (JWT Token)
    S-->>C: resolveAuth(token)
    C->>V: updateAppState(true)
    V-->>U: Redirect to Dashboard
- Agile Info:
    - Story: As a user, I want to create an account and log in securely so that my personal data is protected and accessible only to me.
    - Est Story Points: 5
    - Assigned Responsible Engineer: Parker Morgan
    - GitHub Issue Number: 

<!-- See Role -->

**Classes**:
* **Model**:
    * **UML Class**:
        <!-- Use https://mermaid.js.org/syntax/classDiagram.html: --->
        classDiagram
            class UserAccount {
                +String email
                +String passwordHash
                +Boolean isAuthenticated
                +String sessionToken
                +serialize()
            }
    * ***Code Location***: `src/models/UserAccount.js`
* **Control** 
    * **UML Class**:
        <!-- Use https://mermaid.js.org/syntax/classDiagram.html: --->
        ```mermaid
        classDiagram
            class AuthController {
                +processSignup(data)
                +processLogin(creds)
                +processReset(email)
                +processLogout()
                -validateForm(data)
            }
        ```
        * **Create** (Function name): `processSignup`
        * **Read** (Function name): `processLogin`
        * **Update** (Function name): `processReset`
        * **Delete** (Function name): `processLogout`
        * ***Code Location***: `src/controllers/AuthController.js`

* **View** (UML Class)
    <!--- Use https://mermaid.js.org/syntax/classDiagram.html: --->
    ```mermaid
    classDiagram
        class AuthComponent {
            +renderSignupForm()
            +renderLoginForm()
            +renderResetForm()
            +destroySessionUI()
            -toggleLoader()
        }
* **User Interface (Wireframe)**:
    * **Create** (Function name): `renderSignupForm`
    * **Read** (Function name): `renderLoginForm`
    * **Update** (Function name): `renderResetForm`
    * **Delete** (Function name): `destroySessionUI`
    * ***Code Location***: `src/views/AuthComponent.jsx`
* **Back Interface** (UML Class):
    ```mermaid
    classDiagram
        class AuthService {
            +apiPostUser(payload)
            +apiGetAuth(payload)
            +apiPatchPassword(payload)
            +apiDeleteSession()
        }
    ```
    * **Create** (Function name): `apiPostUser`
    * **Read** (Function name): `apiGetAuth`
    * **Update** (Function name): `apiPatchPassword`
    * **Delete** (Function name): `apiDeleteSession`
    * ***Code Location***: `src/services/AuthService.js`

### Back-End (20 pts)
* **Business Logic**: 
<!-- Use https://mermaid.js.org/syntax/flowchart.html -->
- Agile Info:
    - Story: 
    - Est Story Points: 
    - Assigned Responsible Engineer:
    - GitHub Issue Number: 

**Classes**
* **Models**: 
    <!--Use UML and Sequence or ZenUML -->
    * **UML Class**:
        <!-- Use https://mermaid.js.org/syntax/classDiagram.html: --->
    * ***Code Location***:
* **Control**: 
    <!-- Use UML and https://mermaid.js.org/syntax/sequenceDiagram.html -->
    * **UML Class**:
        * **Create** (Function name):
        * **Read** (Function name):
        * **Update** (Function name):
        * **Delete** (Function name):
        * ***Code Location***: 
            <!-- Use https://mermaid.js.org/syntax/classDiagram.html: -->

* **View**(UML Class)
    <!--- Use https://mermaid.js.org/syntax/classDiagram.html: --->
    * **Front-End API** ():
        * **Create** (Function name):
        * **Read** (Function name):
        * **Update** (Function name):
        * **Delete** (Function name):
        * ***Code Location***: 
    * **Database Interface** (UML Class):
        * **Create** (Function name):
        * **Read** (Function name):
        * **Update** (Function name):
        * **Delete** (Function name):
        * ***Code Location***: 
    
### Database (20 pts)
* **Data Relationship Logic**: 
<!-- Use https://mermaid.js.org/syntax/entityRelationshipDiagram.html -->
- Agile Info:
    - Story: 
    - Est Story Points: 
    - Assigned Responsible Engineer:
    - GitHub Issue Number: 

**Classes**:
<!--Use https://mermaid.js.org/syntax/entityRelationshipDiagram.html -->
* **Models**: (Table/Doc Descriptions) 
    * ***Code Location***: 
* **Control**: DBMS
    * Setup, Maintenance, Trigger Scripts
        * **Create** (Function name):
        * **Read** (Function name):
        * **Update** (Function name):
        * **Delete** (Function name):
        * ***Code Location***: 
* **View** (UML Class)
    <!--- Use https://mermaid.js.org/syntax/classDiagram.html: --->
    * **Back-End API/Queries** ():
        * **Create** (Function name):
        * **Read** (Function name):
        * **Update** (Function name):
        * **Delete** (Function name):
        * ***Code Location***:

---
### Review (10 pts)
- [ ] All elements of the form are filled out
    - [ ] Reference 
    - [ ] Traceablity
    - [ ] Agile
    - [ ] Detailed Design 
- [ ] Epic Story is created in the project's repo Issue
    * Issue Number (Reference):
    <!-- Include a link to the Issue--> 
- [ ] Sub stories are created as the project's repo Issues
    * Issue Number 1 (i.e. Front-End): 
    * Issue Number 2 (i.e. Back-End):
    * Issue Number 3 (i.e. Database):
    <!-- Include a link to the Issues--> 
- [ ] All stories/issues project attributes are filled out
- [ ] Teammembers have reviewed the items
