# Hogwarts GraphQL

This is meant as an exercise in learning to build a GraphQL server with a
reasonable amount of relationships to help stretch beyond basic use cases.

# Problem Description

Hogwarts is in need of a new classroom managment system. In this system we need
to keep track of the following things:

1. Book

   - Books have:
     - `id` (ID)
     - `name` (string)
     - `author` (string) not a reference to any other object
     - `course` (Course)

2. Course

   - Courses have:
     - `id` (ID)
     - `name` (string)
     - `books` (Book[])

3. Section

   - Sections have:
     - `id` (ID)
     - `course` (Course)
     - `professor` (Professor)
     - `students` (Student[])
     - `people` (Person[])
     - `time` (string) something like "MW 10-11:15 TTh 2:30-3:45", nothing fancy

4. Person

   - People have:
     - `id` (ID)
     - `name` (string)
     - `sections` (Section[])

5. Professor

   - A Professor is also a Person
   - Professors have:
     - `id` (ID)
     - `name` (string)
     - `sections` (Section[])
     - `officeHours` (string) something like "MW 10-11:15 TTh 2:30-3:45", nothing fancy

6. Student

   - A Student is also a Person
   - Students have:
     - `id` (ID)
     - `name` (string)
     - `sections` (Section[])
     - `house` (enum House{Gryffindor,Hufflepuff,Ravenclaw,Slytherin})

The API we're building needs to be able to answer the following questions
efficiently in a single query:

1. Given a student id I would like to know what my course schedule is. This does
   not need to be in any given order.
2. Given a student id I would like to know what books I need for this semembers.
3. Given a course id I would like to know all of the students who are taking
   that course.
4. Given a book id I would like to know how many people need that book.
5. Any other interesting things you'd like you be able to answer.

You should also be able to add and update anything in the above data through the
API.

You may use any database you'd like (you could even keep things in-memory). If
you use a database, be sure to have the appropriate migration scripts to setup
the database. You may also wish to have a seed script that populates the
database with a base set of data. SQLite is a good database to start out with if
you're looking for a real-ish database that can store things that isn't just
keeping the data in-memory, but you don't have to worry about running the
database server in another tab or in docker.
