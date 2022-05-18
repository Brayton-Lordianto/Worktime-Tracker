[Summary of further consultation with Mr. ***redacted***]{.underline}

***After the first interview**, the client and I had a 1-2 hr
conversation about all the specifics of the extra wages system. The main
points have been categorized and summarized as follows. \*Information
from the interview is also added.*

**Who is the Client and what does he do?**

The Client, Mr. ***redacted***, is a general manager of ***redacted***, which is a ***redacted*** that has a huge lot of employees. One of his jobs
as a general manager is to calculate the extra wage pay of every
employee. In the company, all the employees are paid their fixed basic
salary right on the last day of every month. And then, it is up to Mr.
***redacted*** to calculate the extra wages quickly done, and have them
distributed to the employees sometime early in the next month. Although
there are exceptions, the extra wages are mainly calculated based on
extra or missed hours to work. This involves not only addition but also
deduction of extra wages (although the employees will not have any
deducted from his/her standard salary as it has already been given to
them before the extra wages are distributed. Mr. ***redacted*** is fine with
this different-time pay system.).

**Bigger Picture?**

The company actually has an excel table sheet (**Microsoft Access
Business Database**), where the CEO of the company makes changes to
standard salaries of different employees as well as the amount of Rp
worth 1 hour-- which differs from person to person. This is, according
to Mr. ***redacted***, a sustainable system that seems to work well. The only
thing Mr. ***redacted*** is concerned with, is the number of overtime hours that
he would normally calculate manually. The business database also
includes a lot of the employee's information, so he does not want this
product to have a whole lot of employee information as it is not
necessary.

**How does it work in the physical work environment?**

Mr. ***redacted*** explains that the hours used to calculate the extra wages of
an employee comes from the work time system that the whole company is
currently using. It involves providing monthly time cards for all
employees, which is located in two gates-- the company's entrance and
exit. Every day, an employee would use cards assigned to them and use a
punch card machine to record their work time.

The system is as follows: When an employee comes to work, he records the
time he enters on the time card. When the employee leaves work for the
day, he does the same. However, during work hours, an employee can for
multiple reasons leave the premises of the factory and then return on
the same day. When doing so, an employee also records the time they
leave the premises, and when they return. On average, there would be at
most 3 different times (including the initial work entry and final leave
for the day) where an employee enters and leaves the premises of the
factory. (i.e. login (checkin), logout (checkout), login, logout, login,
logout)

On the manual time cards (The client showed me these), there are 6
different boxes/columns to allow for these checkin-checkout time stamps
for each day and is divided into rows that represent different days of
the month. Once the month is over, Mr. ***redacted*** takes all the sheets of
the employees *he is assigned to calculate for* and will take around 5
hours every month to manually calculate the employees' extra wages.

**How is the extra wage calculated exactly?**

As previously mentioned, the extra wages are calculated generally by
looking at the employee's work time. The idea is that the extra is
calculated through the careful look of additional deductive bonuses for
every day respectively, and then add them all together to end up with
the final monthly bonus (though it must be noted that this bonus must be
positive or 0. There is never a reduction in the standard salary.).
Every day, an employee is generally expected to work from time X to time
Y, such as 7am\~3pm on weekdays/ 7am\~1pm on weekends. This means the
employee should work daily with a total of 7 hours (1 hour buffer for
lunches). If the employee works overtime or less by Z hours, the extra
wage assigned for that day will respectively be a bonus worth Z hours or
-Z hours. The calculation is repeated for each day and the total bonus
will be the addition of all the daily bonuses. Timezone is UTC.

Normal Pay:

-   Max hours of negative overtime in a day is - 2 hrs.

    -   Being absent on a day is a -2 overtime

-   Maximum culminated overtime in a week will be capped at -4 hrs.

    -   A week is calculated as week in the month. So a Monday-Sunday
        > might contain days from different "weeks" of the month.

-   A negative monthly overtime results in a 0 overtime.

Again, the numbers worth for each hour differs from person to person.

**What are the exceptions?**

Exception 1-- diligence pay workers: If these employees have full
attendance for the month, they receive a diligence pay of 1.000.000 Rp.
Missing 1 full day lowers the pay to 600.000 Rp, missing 2 lowers it to
300.000 Rp, and 3 or more absences will leave 0 diligence pay. The final
bonus for this type of employee is the bonus from normal calculations +
the diligence pay. The important thing here is to add a diligence pay--
full, 1 day missing, 2 day missing, 0.

Exception 2-- overtime-included workers: There is a number of overtime
hours already added to their salary by default. The only thing Mr.
***redacted*** has to calculate is the number of overtime hours beyond this
default (these workers work until 5 pm. Hours beyond this are their
additional overtime hours.) No overtime deductions made for these
workers.

Exception 3-- The extra wage is 0.

Exception 4- The extra wage is fixed.

Exception Note-- There should always be an option for Mr. ***redacted*** to add
no bonus to any type of employee, meaning that the hours concerned is
just 0.

**What is the problem with the current system?**

The current system, which requires about 5 hours of Mr. ***redacted***'s time to
calculate the employees' extra wages, is very inefficient. Using a
physical time card can be very error-prone.

Employees who want to calculate their extra wages before the end of the
month also calculate the overtime hours he has manually, which is hard
and inefficient, especially because he/she has to have access to the
time cards first.

**Additional Information?**

The client is familiar with a JSON format file and has a JSON viewer app
(Jayson) that he likes to use to view large amounts of data. He has
requested for the app to be able to send information to his email as a
JSON file with only the necessary information, which is the monthly
overtime, diligence absence, and extra wage type, as long as
calculations are accurate.

The client does not want weekly overtime to be shown because he thinks
that it is unnecessary. He also does not want the calculations to be
explicitly shown, so long as he sees that it is accurate. He wants to do
extensive testing of populating check-in/out logs manually and ensuring
that the calculations are accurate.

The client wants the program to work in the UTC timezone.
