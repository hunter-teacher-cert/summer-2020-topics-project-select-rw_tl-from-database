# Topic: Introduction to Structured Query Language
## Team Members
1. Tsee Lee
2. Rosane Weiss

## Lesson Overview

This is a standalone lesson that can delivered at almost any time. We wrote it
for a year-long senior elective class to transition from the cybersecurity unit
to the database unit, which covers the industry standard database language SQL.
To introduce the SQL unit, we present database manipulation and vulnerability.
The "hook" is to fulfill perhaps the most common request from students in a CS class:
to learn to hack. To do this, we use the Damn Vulnerable Web App (DVWA). DVWA is a
PHP/MySQL web application with a plethora of vulnerabilities built-in.
Its main goals are to help security professionals to test their skills and tools
in a legal environment, to help web developers better understand the processes of
securing web applications and to aid teachers/students to teach/learn web app security
in a classroom environment.

We will use DVWA to teach SQL by guiding students to write queries that "trick"
the database into giving more information than intended.

## Preparations

To deliver this lesson, you will first need to set up your own DVWA website & database.
This can be straightforward and virtually free if you have basic Linux familiarity,
or extremely complicated and time-consuming if you want to rely on free website hosts.
Instructions are provided in:\
["Setting up your DVWA website"](Setting%20up%20your%20DVWA%20website.pdf)

Student worksheet: ["Database, Day 00" worksheet](https://tiny.cc/dvwasqlws)
([DOCX](Database%2C%20Day%2000.docx), [PDF](Database%2C%20Day%2000.pdf))\
[Worksheet Answer Key](Database%2C%20Day%2000%20%5BAnswer%20Key%5D.pdf)\
Slide deck: ["Database, Day 00 presentation"](Database%2C%20Day%2000%20presentation.pdf)

## Lesson: "Introduction to Website Database Vulnerabilities"

See "Database, Day 00 presentation" for the PowerPoint for this lesson.

1) Slide 1: What does it mean to hack a database?
	(The idea here is to have students understand that to hack is to "trick")

2) Slide 2: Discuss with students the legal aspects of hacking
(group and class discussion). In class, I start by asking students how they
would fare in federal prison. Then I ask them about legality of opening
someone's mail, a federal crime because it's delivered by the USPS.
But why federal jurisdiction? Depending on what social studies classes
they have taken, they may or may not know that this is governed by the
Interstate Commerce clause of the U.S. Constitution. And the courts will
assume that anything done on the Internet, even if hacking a local website,
will involve data packets traveling across state lines. I remind them that
the only reason hacking the website in this lesson is ok is that I set up
the site, and gave them permission. If they hack into any other site, they
will be prosecuted, go to federal jail, and no one at the school or their
family will be able to help.

3) Slide 3: Types of vulnerabilities. Briefly discuss each. We are going to
try the Error based vulnerability in this lesson. We are going to trick the
database into giving us extra information, by mistake. (Q/C/C)

4) Distribute the student worksheet, which contains all the examples that
students should complete. Time for student work, alone or in pairs. (discovery)

If students finish early, encourage them to help classmates, but never give
away the answer!

5) Reconvene and demonstrate command syntax on the database behind the website,
using SQL commands. For script, see ["SQL Commands to Demo"](SQL%20Commands%20to%20Demo.pdf)
(live coding).

6) The rest of the slides explain the unit plan we have in mind.

7) Distribute ["SQL-Commands-Cheat-Sheet"](SQL-Commands-Cheat-Sheet.pdf)
for future reference. Discuss most used commands, time permitting.

## If There Is Time

The teacher will set up classes and make assignments in Khan Academy's
[Computer Programming](https://www.google.com/search?client=firefox-b-1-d&q=Khan+Academy+in+the%22Computer+programming%22)
course, which contains a unit called ["Intro to SQL: Querying and managing data"](https://www.khanacademy.org/computing/computer-programming/sql).

The lessons involve an instructional video followed a "challenge", plus
some additional readings, which can be self-guided. Students will complete
all assignments from that unit, or whichever the teacher considers doable.
Depending on the student population, we recommend assigning two (2)
videos & challenges each per day. Class time can be devoted to questions,
catch-up, etc., or demonstrating queries on a class database.

The minimum for this unit is "SQL Basics", "More advanced SQL queries" and
at least one join in "Relational queries in SQL". There are more lessons in
Khan Academy, if you want do go deeper into SQL.

By the end of the Unit, based on Khan Academy, students will be able to understand
and complete the code in ["End of the unit code"](End%20of%20the%20unit%20code.pdf),
The document also contains screenshots of Khan's online IDE. A very small snippet of
the code is included below for those unfamiliar with SQL.

### Sample ["End of the unit code"](End%20of%20the%20unit%20code.pdf)
```SQL
CREATE TABLE persons (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    fullname TEXT,
    age INTEGER);

INSERT INTO persons (fullname, age) VALUES ("Bobby McBobbyFace", "12");

SELECT perA.fullname, perB.fullname
    FROM persons perA
    JOIN friends
    ON perA.id = friends.person1_id
    JOIN persons perB
    ON friends.person2_id = perB.id
    ;
```

## Take It Further
After completing Khan's unit on SQL, it's time to set up a database that
students have full control over. They can collect data, populate the database,
and run analysis on that data. Options here on will depend on teacher's
comfort level and available time.
- The best option, especially if they already set up the DVWA server on
a Linux computer, is to install/turn on the mysql server. This gives maximum
flexibility.
- The quickest option is to continue using Khan's website with its IDE. However,
this can be confusing to students since they will be marked wrong by the autograder.
- Another option without setting up a class server is [pythonanywhere](https://www.pythonanywhere.com/),
which offers python, bash, and sql consoles for free. The downsides include
a limit of 2 consoles running at a time, not being able to access or share
outside an account, and that every student needs to set up their own copy
of any databases.
- [SQLite](https://www.sqlite.org/index.html) is an option if students have
their own computers. It's self-contained, but the API is in C/C++.
