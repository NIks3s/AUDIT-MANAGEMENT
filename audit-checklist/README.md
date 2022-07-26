# CDE-MFPE-Project-Audit-Management-System

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

## Module Name :

* ### Audit-Checklist-Microservice :
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

  * #### --Application Properties Toggle :<br/>
      spring.application.name=AuditChecklist<br/>
      server.port=8200<br/>
      spring.datasource.url=jdbc:h2:mem:checklistdb<br/>
      spring.h2.console.path=/db<br/>
      User Database : H2(In-Memory)<br/>
