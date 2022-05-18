CLIENT TESTING

+---------+--------------+---------------------+---------------------+
| Action  | Method of    | Desired Result      | Met?                |
| Test    | Testing      |                     |                     |
+=========+==============+=====================+=====================+
| Making  | In Account   | \- Access denied.   | Met                 |
| sure    | login mode:  | Displays a          |                     |
| the     |              | noUsername error.   |                     |
| account | \- Login     |                     |                     |
| login   | with a       | \- Access denied.   |                     |
| /logout | non-existent | Displays a          |                     |
| system  | username and | clientMismatch      |                     |
| is      | both an      | error.              |                     |
| secure  | existent and |                     |                     |
| and     | non-existent | \- Access denied.   |                     |
| func    | password.    | Displays an         |                     |
| tional. |              | employeeMismatch    |                     |
|         | \- Login     | error.              |                     |
| This    | with a       |                     |                     |
| feature | client       | \- The login page   |                     |
| sa      | username but | will be directed to |                     |
| tisfies | a            | the corresponding   |                     |
| part of | non-matching | employee            |                     |
| the     | password.    | information page.   |                     |
| 1^rst^  |              |                     |                     |
| success | \- Login     | \- The login page   |                     |
| cr      | with an      | will be directed to |                     |
| iteria. | employee     | the corresponding   |                     |
|         | username but | employee list page. |                     |
|         | a            |                     |                     |
|         | non-matching | \- The page will be |                     |
|         | password.    | directed to the     |                     |
|         |              | login page with     |                     |
|         | \- Login     | username and        |                     |
|         | with a       | password fields     |                     |
|         | matching     | cleared.            |                     |
|         | employee     |                     |                     |
|         | username and |                     |                     |
|         | password.    |                     |                     |
|         |              |                     |                     |
|         | \- Login     |                     |                     |
|         | with a       |                     |                     |
|         | matching     |                     |                     |
|         | client       |                     |                     |
|         | username and |                     |                     |
|         | password.    |                     |                     |
|         |              |                     |                     |
|         | \- Logging   |                     |                     |
|         | out from     |                     |                     |
|         | both the     |                     |                     |
|         | employee and |                     |                     |
|         | client       |                     |                     |
|         | account      |                     |                     |
|         | page.        |                     |                     |
+---------+--------------+---------------------+---------------------+
| Making  | From both    | \- Denied. Displays | Met                 |
| sure    | Check-in/out | employee error.     |                     |
| c       | to Account   |                     |                     |
| hanging | AND from     | \- Denied. Displays |                     |
| mode is | Account to   | the same errors as  |                     |
| only    | C            | corresponding to    |                     |
| allowed | heck-in/out: | No. 1.              |                     |
| for     |              |                     |                     |
| c       | \- Attempt   | \- Mode will be     |                     |
| lients. | to change    | changed             |                     |
|         | mode by      |                     |                     |
| This    | entering an  |                     |                     |
| sa      | employee     |                     |                     |
| tisfies | account.     |                     |                     |
| the     |              |                     |                     |
| client  | \- Attempt   |                     |                     |
| verif   | to change    |                     |                     |
| ication | mode by      |                     |                     |
| feature | entering a   |                     |                     |
| o       | non-matching |                     |                     |
| utlined | and          |                     |                     |
| in      | non-existent |                     |                     |
| success | account.     |                     |                     |
| c       |              |                     |                     |
| riteria | \- Attempt   |                     |                     |
| 6.      | to change    |                     |                     |
|         | mode by      |                     |                     |
|         | entering a   |                     |                     |
|         | client       |                     |                     |
|         | account.     |                     |                     |
+---------+--------------+---------------------+---------------------+
| Check   | \- Attempt   | \- Error will be    | Met                 |
| -in/out | to do        | displayed for the   |                     |
| for     | check-in/out | client.             |                     |
| emp     | for a client |                     |                     |
| loyees. | account.     | \- Displays the     |                     |
|         |              | same errors as No.  |                     |
| This    | \- Attempt   | 1.                  |                     |
| sa      | to do an     |                     |                     |
| tisfies | check-in/out | \- Logs will be     |                     |
| the     | by entering  | recorded in the     |                     |
| ti      | a            | database with the   |                     |
| mestamp | non-matching | timestamp and       |                     |
| re      | and          | employee. If the    |                     |
| cording | non-existent | log day and/or      |                     |
| feature | account.     | month does not      |                     |
| o       |              | exist, it will be   |                     |
| utlined | \- Doing a   | created. And then,  |                     |
| in      | check-in/out | connections between |                     |
| success | for an       | the log and the     |                     |
| c       | employee     | corresponding day   |                     |
| riteria | account.     | will be made.       |                     |
| 6.      |              |                     |                     |
|         |              |                     |                     |
| *This   |              |                     |                     |
| feature |              |                     |                     |
| is not  |              |                     |                     |
| i       |              |                     |                     |
| ntended |              |                     |                     |
| for     |              |                     |                     |
| cl      |              |                     |                     |
| ients.* |              |                     |                     |
+---------+--------------+---------------------+---------------------+
| Se      | In the       | \- As the name is   | Met                 |
| arching | client's     | searched, the list  |                     |
| for an  | account      | of employees will   |                     |
| e       | mode:        | automatically       |                     |
| mployee |              | update to matched   |                     |
| and     | \- Attempt   | employees with      |                     |
| viewing | to search    | names that start    |                     |
| their   | for names of | with the searched   |                     |
| info    | the clients  | letters.            |                     |
| rmation | on search    |                     |                     |
| by the  | bar.         | -This will redirect |                     |
| client. |              | the client to the   |                     |
| This    | \- Pressing  | selected employee's |                     |
| sa      | on the name  | editable            |                     |
| tisfies | of the       | information page.   |                     |
| the     | employee.    |                     |                     |
| 3^rd^   |              |                     |                     |
| success |              |                     |                     |
| cr      |              |                     |                     |
| iteria. |              |                     |                     |
+---------+--------------+---------------------+---------------------+
| Edits   | \- Attempt   | \- All fields are   | Met                 |
| and     | by an        | disabled except for |                     |
| rea     | account      | the password.       |                     |
| d-write | logged in    | Changes to password |                     |
| access  | employee to  | are saved in the    |                     |
| to      | change       | database.           |                     |
|         | information. |                     |                     |
| client  |              | \- Username text    |                     |
| infor   | \- Attempt   | field is disabled   |                     |
| mation, | by client to | (username is        |                     |
| e       | change       | unique). Changes to |                     |
| mployee | employee     | employee name and   |                     |
| infor   | name,        | password will be    |                     |
| mation, | username,    | saved to the        |                     |
| and     | and          | database.           |                     |
|         | password.    |                     |                     |
| logs.   |              | \- All information  |                     |
|         | \- Attempt   | except username can |                     |
| Editing | by client to | be changed.         |                     |
| access  | change       |                     |                     |
| of      | client       | \- Changes are      |                     |
| e       | information. | saved to the        |                     |
| mployee |              | database. Daily     |                     |
| and log | \- Attempt   | work time and       |                     |
| info    | by client to | overtime and        |                     |
| rmation | change       | monthly overtime    |                     |
| largely | employee     | and diligence       |                     |
| by      | type.        | absences will       |                     |
| clients |              | update              |                     |
| will    | \- Attempt   | correspondingly.    |                     |
| satisfy | to change,   |                     |                     |
| the     | add, and     | \- Changes are      |                     |
| 5^th^   | delete logs  | saved in the        |                     |
| and     | of a         | database. Daily     |                     |
| 7^th^   | selected     | work time and       |                     |
| success | employee.    | overtime and        |                     |
| cr      |              | monthly overtime    |                     |
| iteria. |              | and diligence       |                     |
|         |              | absences will       |                     |
| Editing |              | update              |                     |
| the     |              | correspondingly.    |                     |
| client  |              |                     |                     |
| profile |              |                     |                     |
| info    |              |                     |                     |
| rmation |              |                     |                     |
| sa      |              |                     |                     |
| tisfies |              |                     |                     |
| the     |              |                     |                     |
| 2^nd^   |              |                     |                     |
| success |              |                     |                     |
| cr      |              |                     |                     |
| iteria. |              |                     |                     |
+---------+--------------+---------------------+---------------------+
| An      | Attempting   | \- There is no way  | Met                 |
| adding  | to add       | to add an employee. |                     |
| e       | employees    |                     |                     |
| mployee | by:          | \- Corresponding    |                     |
| f       |              | error message       |                     |
| eature, | \- Logging   | displayed.          |                     |
| but     | in as an     |                     |                     |
| only    | employee.    | \- The added        |                     |
| for     |              | employee will be    |                     |
| c       | \- Trying    | saved to the        |                     |
| lients, | all cases:   | database with the   |                     |
| sat     | no name      | corresponding added |                     |
| isfying | entered, no  | information.        |                     |
| the     | username     |                     |                     |
| 4^th^   | entered, no  |                     |                     |
| success | password     |                     |                     |
| cr      | entered, and |                     |                     |
| iteria. | trying an    |                     |                     |
|         | existing     |                     |                     |
|         | username.    |                     |                     |
|         |              |                     |                     |
|         | \-           |                     |                     |
|         | Submitting a |                     |                     |
|         | valid name,  |                     |                     |
|         | password,    |                     |                     |
|         | username,    |                     |                     |
|         | and type.    |                     |                     |
+---------+--------------+---------------------+---------------------+
| Method  | On all types | \- Work Time for    | Met                 |
| of      | of           | all types of        |                     |
| calc    | employees:   | workers is          |                     |
| ulating |              | calculated by       |                     |
| daily   | \-           | (check-out log -    |                     |
| work    | Populating a | check-in log).      |                     |
| time    | weekday with |                     |                     |
| and     | 2 logs with  | For Normal Pay      |                     |
| daily   | a workday    | Workers: The first  |                     |
| ov      | between 6    | daily overtime will |                     |
| ertime. | and \>6      | yield (workday - 7) |                     |
|         | hours, and   | hours. The last     |                     |
| A       | below 6      | case will yield a   |                     |
| ccurate | hours.       | cap of -2 hours.    |                     |
| pro     |              |                     |                     |
| cessing | \- Same for  | \- Work Time is     |                     |
| and     | a weekend:   | calculated the same |                     |
| capping | Populating a | way.                |                     |
| of      | weekend with |                     |                     |
| these   | a workday    | For Normal Pay      |                     |
| values  | between 5    | Workers: The first  |                     |
| satisfy | and \>5      | two cases will just |                     |
| the     | hours, and   | yield a daily       |                     |
| 8^th^   | below 5      | overtime of the     |                     |
| and     | hours.       | (workday - 5)       |                     |
| 9^th^   |              | hours. The last     |                     |
| success | \-           | case will yield a   |                     |
| cr      | Populating a | cap of -2 hours.    |                     |
| iteria. | weekday with |                     |                     |
|         | 4 logs.      | \- The work time    |                     |
|         |              | should yield a      |                     |
|         | \-           | value of (fourth    |                     |
|         | Populating a | log time - third    |                     |
|         | weekday with | log time) + (second |                     |
|         | 3 logs.      | log time - first    |                     |
|         |              | log time)           |                     |
|         |              |                     |                     |
|         |              | \- The daily work   |                     |
|         |              | time and overtime   |                     |
|         |              | (for normal pay     |                     |
|         |              | workers) should     |                     |
|         |              | yield a -3. The     |                     |
|         |              | monthly overtime    |                     |
|         |              | will also be a -3.  |                     |
+---------+--------------+---------------------+---------------------+
| H       | For a        | \- The monthly      | Met                 |
| andling | *NormalPay*  | overtime is the     |                     |
| a       | employee     | total of the daily  |                     |
| bsences | (without     | overtimes added.    |                     |
| and     | populating   |                     |                     |
| capping | any logs on  | \- Each day's       |                     |
| monthly | Sundays):    | absence will count  |                     |
| o       |              | as a -2 to the      |                     |
| vertime | \- Populate  | monthly overtime.   |                     |
| for     | logs for a   | The weekly overtime |                     |
| *Nor    | whole month  | will be capped at   |                     |
| malPay* | except       | -4.                 |                     |
| emp     | Sundays,     |                     |                     |
| loyees. | with a fixed | \- The monthly      |                     |
|         | daily        | overtime will be    |                     |
| This    | overtime     | capped at the       |                     |
| also    | above 0 for  | minimum of 0 hours. |                     |
| sa      | each day.    |                     |                     |
| tisfies |              |                     |                     |
| the     | \- Populate  |                     |                     |
| 8^th^   | logs for a   |                     |                     |
| and     | whole month  |                     |                     |
| 9^th^   | except       |                     |                     |
| success | Sundays with |                     |                     |
| cr      | some         |                     |                     |
| iteria. | absences in  |                     |                     |
|         | the same     |                     |                     |
|         | week of the  |                     |                     |
|         | month.       |                     |                     |
|         |              |                     |                     |
|         | \- Populate  |                     |                     |
|         | logs for a   |                     |                     |
|         | whole month  |                     |                     |
|         | except       |                     |                     |
|         | Sundays with |                     |                     |
|         | a negative   |                     |                     |
|         | daily        |                     |                     |
|         | overtime for |                     |                     |
|         | each day.    |                     |                     |
+---------+--------------+---------------------+---------------------+
| Monthly | \-           | \- 1, 2 and 3       | Met                 |
| pro     | Populating a | diligence absences  |                     |
| cessing | *D           | will be stored in   |                     |
| de      | iligencePay* | the database as 1,  |                     |
| pending | employee     | 2 and 3             |                     |
| on the  | with logs    | respectively. 4     |                     |
| type of | that         | absences will be    |                     |
| the     | indicate 1,  | stored as 3, but    |                     |
| em      | 2, 3 and 4   | when viewing the    |                     |
| ployee. | absences in  | absent days, there  |                     |
|         | a month and  | will be 4 absences. |                     |
| This    | calculate    |                     |                     |
| also    | monthly      | \- no changes to    |                     |
| sa      | extra.       | attributes. Their   |                     |
| tisfies |              | types speak for     |                     |
| the     | \- Inputting | their extra wages.  |                     |
| 8^th^   | random logs  |                     |                     |
| and     | for          |                     |                     |
| 9^th^   | *NoExtraPay, |                     |                     |
| success | Ca           |                     |                     |
| cr      | nceledBonus, |                     |                     |
| iteria. | and          |                     |                     |
|         | FixedPay*    |                     |                     |
| (mainly | employees.   |                     |                     |
| for     |              |                     |                     |
| non     |              |                     |                     |
| -normal |              |                     |                     |
| type    |              |                     |                     |
| emp     |              |                     |                     |
| loyees: |              |                     |                     |
| *Dilige |              |                     |                     |
| ncePay, |              |                     |                     |
| NoEx    |              |                     |                     |
| traPay, |              |                     |                     |
| Cancele |              |                     |                     |
| dBonus, |              |                     |                     |
| Fi      |              |                     |                     |
| xedPay* |              |                     |                     |
|         |              |                     |                     |
| Unless  |              |                     |                     |
| in      |              |                     |                     |
| dicated |              |                     |                     |
| othe    |              |                     |                     |
| rwise.) |              |                     |                     |
+---------+--------------+---------------------+---------------------+
| Making  | In a client  | \- A mail composer  | Met                 |
| sure    | account:     | delegate should     |                     |
| that    |              | show up with pretty |                     |
| the     | \- Choose    | printed data for    |                     |
| email   | different    | username, name,     |                     |
| feature | months to    | extraWageType,      |                     |
| works   | send (month  | monthlyOvertime,    |                     |
| and     | and year     | and                 |                     |
| that    | specified)   | diligenceAbsences   |                     |
| the     | as JSON.     | of all employees    |                     |
| JSON    |              | that logged in the  |                     |
| info    |              | month. The          |                     |
| rmation |              | information should  |                     |
| and     |              | be printed as a     |                     |
| file is |              | JSON and attached   |                     |
| ac      |              | as a JSON file.     |                     |
| curate. |              | When sent, email is |                     |
|         |              | received by         |                     |
| This    |              | destination.        |                     |
| sa      |              |                     |                     |
| tisfies |              |                     |                     |
| the     |              |                     |                     |
| 10^th^  |              |                     |                     |
| success |              |                     |                     |
| cr      |              |                     |                     |
| iteria. |              |                     |                     |
+---------+--------------+---------------------+---------------------+

*The client and I discussed the functionalities of the product. The
client was unwilling to publicize our conversation. The transcript is
cluttered, so I decided to summarize the meeting. This appendix is a
summary of the meeting.*

Overall, the client praised all the main functionalities of the program
features that were brought up in the success criteria. We went through
each of the success criteria and he was satisfied with the program. He
focused a lot on the core functionality of checking if daily work time,
daily overtime, monthly overtime, number of absences, fixedPay, weekly
considerations, capping these values on the daily, weekly, and monthly
scale. Basically, he looked at everything that was already outlined in
the Testing Plan of Criterion B. After seeing the Criterion D video and
doing some testing, he was pleased with the functionalities working. He
found the design fairly intuitive and usable with a little bit of
training, and was especially pleased with the list of employees and
navigating around employees. He also credited the way that the client
can easily choose a date and send JSON information he needs.

He also talks about what can be improved to make the program more
wholesome. Here is the summary of what he talked about:

The client wants to connect the program's database information with his
business' Microsoft Access database. He wants this to be a two way
connection that happens regularly, but not in real-time. He does not
like that the client would have to add employees manually, especially
the first time of adding around 60 employees assigned to him. These
employees are already in the database so he thinks it is better to have
a way to transfer the data from the business database to set the
employees in the local database. If this is done regularly, with
duplicates handled, added employees to the workforce can also be
reflected automatically in the local database. Furthermore, the client
wants this to happen the other way around too. After the end of each
month, he thinks it will be good if the monthly information can be
transferred for normal pay and diligence pay employees. This would be
good because he would not need to cross-reference, for example, the
monthly overtime in the file sent by email with the actual cash
information in the business database. It would be better if everything
was exported to the business database to deal with the cash wages. He
agrees that some formatting would need to be done to handle the
different fields and systems of the two different databases and to allow
interoperability.
