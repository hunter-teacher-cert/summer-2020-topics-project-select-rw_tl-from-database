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
Instructions are provided in ["Setting up your DVWA website"](Setting%20up%20your%20DVWA%20website.pdf)
for details.

A worksheet entitled "Database, Day 00" is provided that you can assign to your students.
Its answer key is also included, as well as an accompanying slide deck that also touches
on what lessons we will follow up this lesson with ("Database, Day 00 presentation").

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

4) Distribute the ["Database, Day 00" worksheet](https://tiny.cc/dvwasqlws)
([DOCX](Database%2C%20Day%2000.docx), [PDF](Database%2C%20Day%2000.pdf)).
This worksheet contains all the examples that students should complete.
Time for student work, alone or in pairs. (discovery)

If students finish early, encourage them to help classmates, but never give
away the answer!

5) Reconvene and demonstrate command syntax on the database behind the website,
using SQL commands. For script, see ["SQL Commands to Demo"](SQL%20Commands%20to%20Demo.pdf)
(live coding).

6) The rest of the slides explain the unit plan we have in mind.

7) Distribute ["SQL-Commands-Cheat-Sheet"](SQL-Commands-Cheat-Sheet.pdf)
for future reference. Discuss most used commands, time permitting.

## Follow-up

The teacher will set up classes and make assignments in Khan Academy's
[Computer Programming](https://www.google.com/search?client=firefox-b-1-d&q=Khan+Academy+in+the%22Computer+programming%22)
course, which contains a unit called ["Intro to SQL: Querying and managing data"]
(https://www.khanacademy.org/computing/computer-programming/sql).
The lessons involve an instructional video followed a "challenge",
plus some additional readings, which can be self-guided.

Students will complete all assignments from that unit, or whichever the
teacher considers doable. Depending on the student population, we recommend
assigning two (2) videos & challenges each per day. Class time can be devoted
to questions, catch-up, etc., or demonstrating queries on a class database.

The minimum for this unit is "SQL Basics", "More advanced SQL queries" and
at least one join in "Relational queries in SQL". There are more lessons in
Khan Academy, if you want do go deeper into SQL.

By the end of the Unit, based on Khan Academy, students will be able to understand
and complete the following code, which is in response to Computing/ Computer programming/
Intro to SQL: Querying and managing data/ Relational queries in SQL/ Challenge: Friendbook

## Sample end-of-unit student code
```SQL
CREATE TABLE persons (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    fullname TEXT,
    age INTEGER);

INSERT INTO persons (fullname, age) VALUES ("Bobby McBobbyFace", "12");
INSERT INTO persons (fullname, age) VALUES ("Lucy BoBucie", "25");
INSERT INTO persons (fullname, age) VALUES ("Banana FoFanna", "14");
INSERT INTO persons (fullname, age) VALUES ("Shish Kabob", "20");
INSERT INTO persons (fullname, age) VALUES ("Fluffy Sparkles", "8");

CREATE table hobbies (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    person_id INTEGER,
    name TEXT);

INSERT INTO hobbies (person_id, name) VALUES (1, "drawing");
INSERT INTO hobbies (person_id, name) VALUES (1, "coding");
INSERT INTO hobbies (person_id, name) VALUES (2, "dancing");
INSERT INTO hobbies (person_id, name) VALUES (2, "coding");
INSERT INTO hobbies (person_id, name) VALUES (3, "skating");
INSERT INTO hobbies (person_id, name) VALUES (3, "rowing");
INSERT INTO hobbies (person_id, name) VALUES (3, "drawing");
INSERT INTO hobbies (person_id, name) VALUES (4, "coding");
INSERT INTO hobbies (person_id, name) VALUES (4, "dilly-dallying");
INSERT INTO hobbies (person_id, name) VALUES (4, "meowing");

CREATE table friends (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    person1_id INTEGER,
    person2_id INTEGER);

INSERT INTO friends (person1_id, person2_id)
    VALUES (1, 4);
INSERT INTO friends (person1_id, person2_id)
    VALUES (2, 3);

SELECT persons.fullname, hobbies.name
    FROM persons
    JOIN hobbies
    ON persons.id = hobbies.person_id
    ;

SELECT perA.fullname, perB.fullname
    FROM persons perA
    JOIN friends
    ON perA.id = friends.person1_id
    JOIN persons perB
    ON friends.person2_id = perB.id
    ;
```
