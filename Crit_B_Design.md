**Criterion B: Design Overview**

-   The client wishes that the program will store the following extra
    > wage types: normal pay, diligence pay, fixed pay, canceled bonus,
    > and no extra pay (*refer to Appendix B-- Summary of Client
    > Interview*).

-   The client wishes for the program only the most basic information
    > (username, password, name) for the client and employee profile.

-   The client is adamant on a JSON file of *only* type, overtime, and
    > diligence absence so that he can manipulate the data with a JSON
    > app he uses (*refer to Appendix B*).

# Entity Relationship Diagram (ERD) 

[![](./media/image12.png){width="6.5in"
height="2.0in"}](https://lucid.app/documents/edit/a2ebeb44-0dfc-4886-a478-28c75d77b72e/0?callback=close&name=docs&callback_type=back&v=1956&s=624)

TECHNICAL

-   Each employee will be uniquely identified by their username.

-   There is only one client, so there is only one row, for the "Client"
    > table, and no primary key is needed. This client account will be
    > hard-coded and can be changed when the client needs to.

-   Data rows added to the "Log" table are done through a user login, so
    > only the employee account and the date of the login are recorded.
    > Both attributes are necessary to connect logs to "Day" and "Month"
    > entities.Thus, there are two foreign keys from "Log" all the way
    > to "Month".

-   Only monthly overtime for normal pay employees and diligence
    > absences for diligent pay employees are important monthly
    > information. Other employee types have either a fixed, canceled,
    > or zero extra pay.

-   "Month", "Day", and "Logs" should be related to each other, but all
    > entities should relate back to an "Employee". The delete rule
    > should be cascading-- e.g. deleting an "Employee" deletes all
    > "Month", "Day", "Log" relating to that employee.

USER EXPERIENCE

-   The user does not explicitly see these entities. The "Employee" and
    > "Client" entities hold credentials that allow for log in.

-   When employees look for their information on a certain day/month,
    > they will see information from a hybrid of these entities.

# Data Flow Diagram (DFD)

[![](./media/image11.png){width="7.476975065616798in"
height="2.5282720909886263in"}](https://lucid.app/documents/edit/900fa9cf-9651-4069-8358-5fedce7d6ac9/0?callback=close&name=docs&callback_type=back&v=1152&s=624)

-   In the vicinity of the workplace, employee check-in/outs will be
    > recorded in the system database.

-   Otherwise, employees can view their own information and logs, and
    > clients can navigate and view all employees and information.

-   The program stores all the logs for recording purposes, and, if
    > applicable, processes the diligence pay absences or monthly
    > overtimes and daily worktimes.

-   The client can choose to email this information to himself as a JSON
    > file for him to view with his preferred JSON app viewer.

-   If needed, the client can change any logs or work time in the local
    > database.

# UML Diagrams

[![](./media/image2.png){width="7.25in"
height="8.416666666666666in"}](https://lucid.app/documents/edit/a66e2876-56ac-4c37-a6e3-8737f3c5e427/0?callback=close&name=docs&callback_type=back&v=3567&s=697)

*A line connecting an enumerator and a class means that the enumerator
is used in the class.*[^1]

-   The "JsonHandler" HAS AN "EmailHelper", and HAS MANY
    > "ToBeJsonEmployee(s)". These help send the JSON file to the
    > client's email.

-   The "credentialsHandler" class handles checking for entered user
    > credentials for check-in/out and user account authentication.

-   The "Logger" class handles adding check-in/out logs, or
    > client-changes to logs.

-   "DayCalculator" class calculates daily work time and, if applicable,
    > overtime of every day. The "MonthCalculator" class calculates the
    > monthly overtimes or diligence pay absences, where applicable, of
    > every month.

-   Classes are abstract and separate from the UI. Users will not
    > directly see or interact with classes.

# Flowcharts

## System Flowchart: Overview of the App[![](./media/image10.png){width="7.041666666666667in" height="3.8472222222222223in"}](https://lucid.app/documents/edit/b126fec8-1abf-4e88-b42a-ee1fe28c6e16/0?callback=close&name=docs&callback_type=back&v=2286&s=676)

-   The design starts with a login page that leads to a user's account
    > page.

-   By authenticating the client account, the program's login mode can
    > be changed to a mode for check-in/out or vice versa.

-   Employee's can check information like their status, work time, and
    > logs for the day, but cannot change them.

-   A client can add, delete, search, view, and change the employee's
    > basic profile information, including logs of any employee.

-   A client can also view and change his profile information, and
    > choose a month to send JSON information of his employees to his
    > email.

-   All changes are reflected in the local database.

## Algorithm Flowcharts (refer to Criterion A-- Success Criteria **\# 8, 9, 10**)

### Checking-in or out

[![](./media/image14.png){width="6.375in"
height="5.5in"}](https://lucid.app/documents/edit/adb2ad1c-dc07-474a-a60d-152c09914d10/0?callback=close&name=docs&callback_type=back&v=4355&s=612)

-   A specific error message should display for each case of whether the
    > credentials were empty, an password mismatch, or a
    > client-attempted check-in/out.

-   The algorithm checks credentials before recording the timestamp.

-   The timestamp used is the "Date" fundamental data type offered in
    > Swift, and stored as a dateTime in the sqlite database.

-   The algorithm ensures that every log will have a month and day
    > entity corresponding to it, and that worktimes and overtimes, if
    > applicable, will be *automatically* updated.

-   "Month" and "Day" in flowchart refers to Day and Month entities that
    > are compositely identified by an employee it belongs to and the
    > date.

-   

### Calculating For Day Work Time And Overtime

### 

### [![](./media/image16.png){width="6.375in" height="7.819444444444445in"}](https://lucid.app/documents/edit/d2b21c9e-ed62-42c3-8efd-c07e620a5784/0?callback=close&name=docs&callback_type=back&v=1147&s=612)

### 

-   *Note*: -3 as a work time and overtime will never be reached if the
    > employee has an even number of logs and represents a day with an
    > odd number of logs.

```{=html}
<!-- -->
```
-   The algorithm accounts for intermediate exits of an employee by
    > calculating work time in pairs of logins/logouts.

-   For normal pay employees, any more than 5 hours on a Saturday and 8
    > hours on a weekday is overtime.

### Processing for month information

### [![](./media/image3.png){width="6.375in" height="5.805555555555555in"}](https://lucid.app/documents/edit/843022fa-4c20-4fd7-973f-a45d38b84da0/0?callback=close&name=docs&callback_type=back&v=1950&s=612) 

-   This algorithm creates dictionaries that hold specific values for
    > each possible day of the month. The use of dictionaries are
    > convenient because the different dictionaries can be related by
    > the day of the month as a key.

-   Accounting for every day of the month is necessary to handle
    > absences.

-   Only absences are important for diligence pay employees. Canceled
    > bonus, no extra pay, and fixed pay employees do not need the
    > monthly overtimes either.

-   The algorithm ensures that (for normal pay employees) an absence on
    > Sunday would not have any overtime effect, while an absence on any
    > other day would be a deduction of 2 overtime hours.

-   

### Monthly Overtime [![](./media/image8.png){width="6.375in" height="7.833333333333333in"}](https://lucid.app/documents/edit/8d5c27ff-eedf-4172-a067-36215036fefa/0?callback=close&name=docs&callback_type=back&v=1010&s=612)

-   This algorithm applies only to normal pay employees.

-   The algorithm handles for the regulation: weekly overtimes cannot be
    > below -4 hours. This requires looping through each week and every
    > day of the month.

-   The overtime hours per week is then added to get normal pay overtime
    > hours.

### Sending Json Information as an Email To Client

[![](./media/image17.png){width="6.375in"
height="8.26388888888889in"}](https://lucid.app/documents/edit/47e16659-6b27-486d-8ad2-0433839eeaa2/0?callback=close&name=docs&callback_type=back&v=1911&s=612)

-   Algorithm sends a JSON email of the information of an employee on a
    > month.

-   The client chooses a month and year, which identifies the month.

-   "Fetched" refers to a fetchresults of Month entities-- which have an
    > employee related to it.

-   Through these Month entities, *username, extra wage type, name,
    > monthly overtime, and diligence absences* are extracted.

# Mockups 

\*Made With Mockflow.com (MockFlow)

*[On the iPad, the program should look the same as the iPhone mockups,
only bigger.]{.underline}*

## Log In Page 

![](./media/image13.png){width="6.338542213473316in"
height="6.176014873140858in"}

-   The only manager is the client.

-   The two modes available are 'check-in \| check-out' and 'account
    > login' mode. (*refer to Appendix C-- proposed product outline*)

-   Only the client can change modes and the default is the 'account
    > login' mode.

-   check-in/out logins will record timestamps as part of an employee's
    > work time.

-   check-in/out is intended logins on a device in the work vicinity.

-   To change modes, the client will have to fill out his username and
    > password.

-   The informative alert can be dismissed, showing this page again.

-   Login credentials are validated by local database information.

## Employee List Page

![](./media/image5.png){width="6.151042213473316in"
height="6.220043744531933in"}

-   Pressing on the name of an employee will open the Employee
    > Changeable Information Page of that employee.

-   Deleting an employee will also delete the employee in the local
    > database.

-   The list of employees is scrollable, and is sorted alphabetically.

-   Search system will show employees with last or first names
    > containing the keyword.

-   Allow users to log out.

-   Allow adding new employees manually.

-   An option to switch to the Profile tabs is provided.

## Client Profile Page

![](./media/image1.png){width="6.729089020122485in"
height="5.6793088363954505in"}

-   An option to switch to the Profile tabs is provided.

-   Direct changes to the client's profile will be reflected in the
    > database.

-   Choosing a month (and year) with the datepicker will allow the
    > client to send an email of all necessary information (*refer to
    > Criteria A*) as a JSON.

## Employee Unchangeable Information Page

-   This page is for employees who do an 'account' mode
    > login.![](./media/image7.png){width="7.0625in"
    > height="6.526042213473316in"}

-   Employees are given read-only access; They cannot change their logs
    > manually.

-   Users can log out.

## Employee Changeable Information Page

-   The client can see all the information of employee work
    > time.![](./media/image4.png){width="6.5in"
    > height="5.796875546806649in"}

-   The client can change any information, so as to deal with special
    > circumstances.

-   The client can smoothly move back and forth between employee
    > information and the list of employees.

-   In addition to the information above, the work time hours for the
    > day will also be calculated and shown.

-   Overtimes will be shown for Normal Pay Employees, and diligence
    > absences will be shown for diligence pay employees.

## Unchangeable Logs Page

-   This list is for employees.![](./media/image9.png){width="6.5in"
    > height="7.333333333333333in"}

-   Read-only access is provided. Any issues can be directed to the
    > client.

## Changeable Logs Page

-   Client has read-write access to employee logs. Changing logs will
    > update the worktime
    > calculations.![](./media/image6.png){width="6.5in"
    > height="7.333333333333333in"}

## Adding Employee Form Page

![](./media/image15.png){width="6.5in" height="6.319444444444445in"}

-   The client can add new employees this way.

-   One of the fields is the password of the employee, so adding an
    > employee will also register their account.

# Software Development Framework

-   The intended framework for this application is the Waterfall model.

-   The Waterfall model breaks down the intended product into many
    > different tasks. Its highlight is to create a system by performing
    > these tasks in a sequential manner that will depend on the
    > deliverables of the previous task.

-   This framework is most fitting because the client prefers to be
    > involved in a minimal number of interviews, and does not want to
    > be actively involved in the production process of the application.

-   Thus, it is sensible to gather all the wants and needs of the client
    > beforehand, and then work with that on to the next task.

-   This makes it easy to have the end goal in mind from the start,
    > which will be helpful for creating a relevant product.

-   Breaking down the program into smaller parts also allows for a clear
    > and defined structure which makes the program more easy/efficient
    > to approach and create.

# Testing Plan

+--------------+----------------------+--------------------------------+
| Action Test  | Method of Testing    | Desired Result                 |
+==============+======================+================================+
| Making sure  | In Account login     | \- Access denied. Displays a   |
| the account  | mode:                | noUsername error.              |
| login/logout |                      |                                |
| system is    | \- Login with a      | \- Access denied. Displays a   |
| secure and   | non-existent         | clientMismatch error.          |
| functional.  | username and both an |                                |
|              | existent and         | \- Access denied. Displays an  |
| This feature | non-existent         | employeeMismatch error.        |
| satisfies    | password.            |                                |
| part of the  |                      | \- The login page will be      |
| 1^rst^       | \- Login with a      | directed to the corresponding  |
| success      | client username but  | employee information page.     |
| criteria.    | a non-matching       |                                |
|              | password.            | \- The login page will be      |
|              |                      | directed to the corresponding  |
|              | \- Login with an     | employee list page.            |
|              | employee username    |                                |
|              | but a non-matching   | \- The page will be directed   |
|              | password.            | to the login page with         |
|              |                      | username and password fields   |
|              | \- Login with a      | cleared.                       |
|              | matching employee    |                                |
|              | username and         |                                |
|              | password.            |                                |
|              |                      |                                |
|              | \- Login with a      |                                |
|              | matching client      |                                |
|              | username and         |                                |
|              | password.            |                                |
|              |                      |                                |
|              | \- Logging out from  |                                |
|              | both the employee    |                                |
|              | and client account   |                                |
|              | page.                |                                |
+--------------+----------------------+--------------------------------+
| Making sure  | From both            | \- Denied. Displays employee   |
| changing     | Check-in/out to      | error.                         |
| mode is only | Account AND from     |                                |
| allowed for  | Account to           | \- Denied. Displays the same   |
| clients.     | Check-in/out:        | errors as corresponding to No. |
|              |                      | 1.                             |
| This         | \- Attempt to change |                                |
| satisfies    | mode by entering an  | \- Mode will be changed        |
| the client   | employee account.    |                                |
| verification |                      |                                |
| feature      | \- Attempt to change |                                |
| outlined in  | mode by entering a   |                                |
| success      | non-matching and     |                                |
| criteria 6.  | non-existent         |                                |
|              | account.             |                                |
|              |                      |                                |
|              | \- Attempt to change |                                |
|              | mode by entering a   |                                |
|              | client account.      |                                |
+--------------+----------------------+--------------------------------+
| Check-in/out | \- Attempt to do     | \- Error will be displayed for |
| for          | check-in/out for a   | the client.                    |
| employees.   | client account.      |                                |
|              |                      | \- Displays the same errors as |
| This         | \- Attempt to do an  | No. 1.                         |
| satisfies    | check-in/out by      |                                |
| the          | entering a           | \- Logs will be recorded in    |
| timestamp    | non-matching and     | the database with the          |
| recording    | non-existent         | timestamp and employee. If the |
| feature      | account.             | log day and/or month does not  |
| outlined in  |                      | exist, it will be created. And |
| success      | \- Doing a           | then, connections between the  |
| criteria 6.  | check-in/out for an  | log and the corresponding day  |
|              | employee account.    | will be made.                  |
| *This        |                      |                                |
| feature is   |                      |                                |
| not intended |                      |                                |
| for          |                      |                                |
| clients.*    |                      |                                |
+--------------+----------------------+--------------------------------+
| Searching    | In the client's      | \- As the name is searched,    |
| for an       | account mode:        | the list of employees will     |
| employee and |                      | automatically update to        |
| viewing      | \- Attempt to search | matched employees with names   |
| their        | for names of the     | that start with the searched   |
| information  | clients on search    | letters.                       |
| by the       | bar.                 |                                |
| client. This |                      | -This will redirect the client |
| satisfies    | \- Pressing on the   | to the selected employee's     |
| the 3^rd^    | name of the          | editable information page.     |
| success      | employee.            |                                |
| criteria.    |                      |                                |
+--------------+----------------------+--------------------------------+
| Edits and    | \- Attempt by an     | \- All fields are disabled     |
| read-write   | account logged in    | except for the password.       |
| access to    | employee to change   | Changes to password are saved  |
|              | information.         | in the database.               |
| client       |                      |                                |
| information, | \- Attempt by client | \- Username text field is      |
| employee     | to change employee   | disabled (username is unique). |
| information, | name, username, and  | Changes to employee name and   |
| and          | password.            | password will be saved to the  |
|              |                      | database.                      |
| logs.        | \- Attempt by client |                                |
|              | to change client     | \- All information except      |
| Editing      | information.         | username can be changed.       |
| access of    |                      |                                |
| employee and | \- Attempt by client | \- Changes are saved to the    |
| log          | to change employee   | database. Daily work time and  |
| information  | type.                | overtime and monthly overtime  |
| largely by   |                      | and diligence absences will    |
| clients will | \- Attempt to        | update correspondingly.        |
| satisfy the  | change, add, and     |                                |
| 5^th^ and    | delete logs of a     | \- Changes are saved in the    |
| 7^th^        | selected employee.   | database. Daily work time and  |
| success      |                      | overtime and monthly overtime  |
| criteria.    |                      | and diligence absences will    |
|              |                      | update correspondingly.        |
| Editing the  |                      |                                |
| client       |                      |                                |
| profile      |                      |                                |
| information  |                      |                                |
| satisfies    |                      |                                |
| the 2^nd^    |                      |                                |
| success      |                      |                                |
| criteria.    |                      |                                |
+--------------+----------------------+--------------------------------+
| An adding    | Attempting to add    | \- There is no way to add an   |
| employee     | employees by:        | employee.                      |
| feature, but |                      |                                |
| only for     | \- Logging in as an  | \- Corresponding error message |
| clients,     | employee.            | displayed.                     |
| satisfying   |                      |                                |
| the 4^th^    | \- Trying all cases: | \- The added employee will be  |
| success      | no name entered, no  | saved to the database with the |
| criteria.    | username entered, no | corresponding added            |
|              | password entered,    | information.                   |
|              | and trying an        |                                |
|              | existing username.   |                                |
|              |                      |                                |
|              | \- Submitting a      |                                |
|              | valid name,          |                                |
|              | password, username,  |                                |
|              | and type.            |                                |
+--------------+----------------------+--------------------------------+
| Method of    | On all types of      | \- Work Time for all types of  |
| calculating  | employees:           | workers is calculated by       |
| daily work   |                      | (check-out log - check-in      |
| time and     | \- Populating a      | log).                          |
| daily        | weekday with 2 logs  |                                |
| overtime.    | with a workday       | For Normal Pay Workers: The    |
|              | between 6 and \>6    | first daily overtime will      |
| Accurate     | hours, and below 6   | yield (workday - 7) hours. The |
| processing   | hours.               | last case will yield a cap of  |
| and capping  |                      | -2 hours.                      |
| of these     | \- Same for a        |                                |
| values       | weekend: Populating  | \- Work Time is calculated the |
| satisfy the  | a weekend with a     | same way.                      |
| 8^th^ and    | workday between 5    |                                |
| 9^th^        | and \>5 hours, and   | For Normal Pay Workers: The    |
| success      | below 5 hours.       | first two cases will just      |
| criteria.    |                      | yield a daily overtime of the  |
|              | \- Populating a      | (workday - 5) hours. The last  |
|              | weekday with 4 logs. | case will yield a cap of -2    |
|              |                      | hours.                         |
|              | \- Populating a      |                                |
|              | weekday with 3 logs. | \- The work time should yield  |
|              |                      | a value of (fourth log time -  |
|              |                      | third log time) + (second log  |
|              |                      | time - first log time)         |
|              |                      |                                |
|              |                      | \- The daily work time and     |
|              |                      | overtime (for normal pay       |
|              |                      | workers) should yield a -3.    |
|              |                      | The monthly overtime will also |
|              |                      | be a -3.                       |
+--------------+----------------------+--------------------------------+
| Handling     | For a *NormalPay*    | \- The monthly overtime is the |
| absences and | employee (without    | total of the daily overtimes   |
| capping      | populating any logs  | added.                         |
| monthly      | on Sundays):         |                                |
| overtime for |                      | \- Each day's absence will     |
| *NormalPay*  | \- Populate logs for | count as a -2 to the monthly   |
| employees.   | a whole month except | overtime. The weekly overtime  |
|              | Sundays, with a      | will be capped at -4.          |
| This also    | fixed daily overtime |                                |
| satisfies    | above 0 for each     | \- The monthly overtime will   |
| the 8^th^    | day.                 | be capped at the minimum of 0  |
| and 9^th^    |                      | hours.                         |
| success      | \- Populate logs for |                                |
| criteria.    | a whole month except |                                |
|              | Sundays with some    |                                |
|              | absences in the same |                                |
|              | week of the month.   |                                |
|              |                      |                                |
|              | \- Populate logs for |                                |
|              | a whole month except |                                |
|              | Sundays with a       |                                |
|              | negative daily       |                                |
|              | overtime for each    |                                |
|              | day.                 |                                |
+--------------+----------------------+--------------------------------+
| Monthly      | \- Populating a      | \- 1, 2 and 3 diligence        |
| processing   | *DiligencePay*       | absences will be stored in the |
| depending on | employee with logs   | database as 1, 2 and 3         |
| the type of  | that indicate 1, 2,  | respectively. 4 absences will  |
| the          | 3 and 4 absences in  | be stored as 3, but when       |
| employee.    | a month and          | viewing the absent days, there |
|              | calculate monthly    | will be 4 absences.            |
| This also    | extra.               |                                |
| satisfies    |                      | \- no changes to attributes.   |
| the 8^th^    | \- Inputting random  | Their types speak for their    |
| and 9^th^    | logs for             | extra wages.                   |
| success      | *NoExtraPay,         |                                |
| criteria.    | CanceledBonus, and   |                                |
|              | FixedPay* employees. |                                |
| (mainly for  |                      |                                |
| non-normal   |                      |                                |
| type         |                      |                                |
| employees:   |                      |                                |
| *D           |                      |                                |
| iligencePay, |                      |                                |
| NoExtraPay,  |                      |                                |
| Ca           |                      |                                |
| nceledBonus, |                      |                                |
| FixedPay*    |                      |                                |
|              |                      |                                |
| Unless       |                      |                                |
| indicated    |                      |                                |
| otherwise.)  |                      |                                |
+--------------+----------------------+--------------------------------+
| Making sure  | In a client account: | \- A mail composer delegate    |
| that the     |                      | should show up with pretty     |
| email        | \- Choose different  | printed data for username,     |
| feature      | months to send       | name, extraWageType,           |
| works and    | (month and year      | monthlyOvertime, and           |
| that the     | specified) as JSON.  | diligenceAbsences of all       |
| JSON         |                      | employees that logged in the   |
| information  |                      | month. The information should  |
| and file is  |                      | be printed as a JSON and       |
| accurate.    |                      | attached as a JSON file. When  |
|              |                      | sent, email is received by     |
| This         |                      | destination.                   |
| satisfies    |                      |                                |
| the 10^th^   |                      |                                |
| success      |                      |                                |
| criteria.    |                      |                                |
+--------------+----------------------+--------------------------------+

BIBLIOGRAPHY

Works Cited

> MockFlow. "MockFlow - Wireframe Tools, Prototyping Tools, UI Mockups,
> UX Suite, Remote Designing." *Mockflow.com*, mockflow.com. Accessed 4
> Feb. 2021.
>
> "UML Class Diagram Enumeration - Software Ideas Modeler."
> *Www.softwareideas.net*, www.softwareideas.net/class-diagram-enum.
> Accessed 4 Feb. 2021.

‌

[^1]: ("UML Class Diagram Enumeration - Software Ideas Modeler")
