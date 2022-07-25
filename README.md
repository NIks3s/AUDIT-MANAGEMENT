# INTCDE22IJ087-POD1-AUDIT-MANAGEMENT
MFPE Project

# AUDIT-MANAGEMENT Application

This is a full-stack MFPE project built as part of Cognizant CDE internship.

Following services are part of the application:

## Authors :

<table>
    <tr>
        <td>
            <a href="https://github.com/Chandu-A-B">Chandu A B</a>
        </td>
        <td>
            <a href="https://github.com/NIks3s">Nikunj Baid</a>
        </td>
        <td>
            <a href="https://github.com/Navyachowdary9908">Nelluri Navyasree</a>
        </td>
    </tr>
</table>

# INTCDE22IJ087-POD1-AUDIT-MANAGEMENT
MFPE Project

# AUDIT-MANAGEMENT Application

This is a full-stack MFPE project built as part of Cognizant CDE internship.

Following services are part of the application:

## Frontend:
* Audit management Portal

## Backend:
* Authorization Microservice
* Audit Checklist Microservice
* Audit Benchmark Microservice
* Audit Severity Microservice


## Requirements
* Java 11
* Angular 13

## Setup

Launch the above mentioned 4 microservices in your IDE. Import the project as `Maven Project` and wait for the dependencies to install. If any port is unavailable in your machine you can change the port for the respective microservice in the `application.properties` file under `Backend/microservice/src/main/resources/application.properties`

After the 4 microservices are up and running launch the Audit-Management angular application using `ng serve`

## Usage

### Initial Launch

On initial launch of application the user is prompted with a home page of the application. In the navigation bar user can click the `Login` button for authentication.


### Login Portal

User has to enter his username and password to login. Following credentials can be used to login:

|  Username  |  Password  | 
|------------|------------|
|  nikunj    |  nikunj12  |
|  chandu    |  chandu12  |
|  navya     |  navya12   |


## Logged In

Authenticated users can now access the features of the application from the navigation bar under their username.


### Audit-Authorization-Microservice :
  This module is used for doing the **Authentication** and **Authorization** part of our project. 
  This microsevice provides the endpoints for authentication and validation. This MS creates JWTs(JSON Web Token)
  for a authenticated user who is in Database and then it validates the user based on the JWT token passed in the
  "Authentication"-Request-Header.("Bearer j.w.t...")

  * #### Postman details : 
    <table>
        <thead>
            <th>Method</th>
            <th>Postman URL</th>
            <th>Returns</th>
        </thead>
        <tbody>
            <tr>
                <td>GET</td>
                <td>http://localhost:8100/auth/health-check</td>
                <td>String</td>
            </tr>
            <tr>
                <td>POST</td>
                <td>http://localhost:8100/auth/authenticate</td>
                <td>JWT Bearer Token</td>
            </tr>
            <tr>
                <td>POST</td>
                <td>http://localhost:8100/auth/validate</td>
                <td>The Manager details</td>
            </tr>
        </tbody>
    </table>

### Audit-Checklist-Microservice :
  This module is used for retrieving the *List of Questions based on the user's request* for each *Audit Type* from the H2 in-memory database.
  This microservice is used by the Audit-Benchmark Microservice to store and retrieve the no of acceptable NOs for each Audit Type
  This microsevice is used by the Audit-Severity Microservice to evaluate the status of a project and provide an appropriate response.

  * #### --Endpoints : 
    <table>
        <thead>
            <th>Method</th>
            <th>Endpoint Path</th>
            <th>Returns</th>
        </thead>
        <tbody>
            <tr>
                <td>GET</td>
                <td>/AuditChecklist</td>
                <td>Displays the list of Questions</td>
            </tr>
        </tbody>
    </table>

  * #### --Dependencies on Other microsevices : *Authorization Microservice*

### MFPE-Audit-Management-Benchmark microservice


Audit Benchmark is a middleware microservice.
This microservice stores the number of acceptable “No” in the database.
Upon request it returns data as a list in a user-defined AuditBenchmark datatype.
It is used to pass the number of  acceptable “No” or the benchmark, in other words, to audit severity microservice.
Method:
GET:/AuditBenchmark:

### Audit-Severity-Microservice :

  This module is used for checking the severity of the audit by invoking the *Benchmark* and *Checklist*  Microservice as Request from the portal.
  This microservice will return the status of the audit response by giving the project execution status and the remedial action.

  * #### --Endpoints : 
    <table>
        <thead>
            <th>Method</th>
            <th>Endpoint Path</th>
            <th>Returns</th>
        </thead>
        <tbody>
            <tr>
                <td>POST</td>
                <td>/ProjectExecutionStatus</td>
                <td>Audit Severity</td>
            </tr>
        </tbody>
    </table>

  * #### --Dependencies on Other microsevices : *Audit-Authorization,Audit-Checklist,Audit-Benchmark*
