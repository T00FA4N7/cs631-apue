# Class Overview of cs631 (APUE)

The main question: How will this class work/run?
- As a student, it is my job to watch the required videos for the week prior to class and
complete the respective checkpoint during my own time. Within the class period, I will
have discussions with fellow students/instructor, ask & answer questions, etc.

## What is (& isn't) APUE?
This class will **not** be treated as a:
- intro to working with the UNIX (or UNIX-based) environments
- basic programming class that teaches us the fundamentals of writing programs
- C-specific programming language tutorial learning syntax, ettiquette, etc

This class (as the name suggests) is taking a profound exploration and gaining
a deep understanding of what a UNIX-based OS environment is, what it looks like and why,
how to build fundamental parts of one (and hopefully much more)!

For this class, it seems that there are two expectations from what students will learn:
1. Develop their individual computer systems and programming knowledge and experience
2. Develop their skills as engineers (skills besides programming)

For the first topic, besides building up the environment functionalities (like ls, cat,
mv) that programmers all around the globe use on a day-to-day basis, this class will also
introduce IPC (interprocess communication) and network programming using the client-server
model (crucial parts of a systems programming experience). Additionally, as environments
are crucial part of an OS, we will learn foundational concepts in OS's such as:
- multi-user concepts (how an OS handles multiple users simultaneously)
- basic & advanced I/O
- process relationships

Besides these skills, we also will develop how to read large codebases properly and
efficiently, reading and writing docs with the proper ettiquettes (like man pages),
understanding how to plan out the parts of writting these functionalities (edge
cases & hidden requirements) and much more.

## The Why of APUE?
From above, it is clear what this class entails -> yet gaining all this knowledge, do we
care why we learn this information or why it is important to us as developers?

Understanding how an OS works, the environment associated it with it, the code used to
build up this system and everything else from this class can help you go far in any field
of CS that a person chooses to pursue.
- Allows a developer to be comfortable working with different OS'es
- Basic problem solving and programming skills
- Structure of building large programs (and the minor nuances too)
- Essentially the C programming language is what allows this world of technology to exist
so it is important to know it, to be comfortable with it, and to program applications in
it

## The How of APUE?
For simplicity, integrity, and congruency of the course, all students are required to
compile and execute their final programs on a NetBSD (UNIX-based) system, so install it
now!

As the class name suggests, there will be a solid amount of coding in this class. Hence,
we have to make sure we are comfortable editing, manipulating, compiling, executing our
programs on the same system, but also provide necessary documentation and comments for
anyone who reads our programs (instructor, myself in 5 years, etc). For this class,
Professor Schaumann has some basic requirements for our programs:
- be clearly structured (well-separated and compartmentalized)
- be well formatted (appropriate line breaks and white space)
- use a consistent coding style (indentation, placement of braces)
- meaningful names for files, variables, functions, etc
- comments are used when necessary explaining why (don't want to see more lines of
comments than code)

## Class Logistics of cs631:
The main resource (textbook) for this class is "Advanced Programming in the UNIX
Environment", Third Edition, by W. Richard Stevens, Stephen A. Rago.

### Grading Distribution & Assignments of cs631:
- Course Participation & Notes (50 points)
    - The in-person will be synchronous with discussions, so just participate (anyways
    what's the harm?)
- 2 Smaller Homework Assignments (25 points each)
    - Around 200-400 LOC
- 1 Midterm Project (100 points)
    - Up to 2 KLOC
- 1 Final [Group] Project (200 points)
    - Teams up to 2/3 People
- 1 Final [Individual] Project (100 points)

#### Course Participation & Notes:
For this section, students are expected to:
- Create a single text file for each lecture
    - Before the Lecture:
        - Notes on what I read, exercises completed, and any questions
    - After the Lecture:
        - Answers you've found or new things learned
        - What questions remain and what new questions arise
    - Follow up on answered questions in class or on the mailing list
    - At the end of the sem, submit all notes

The idea of these notes is to see how much I have learned and gained before and after
each week but also across the entire semester (and see how much I have changed maybe in
perspective, programming skills, etc).

# Miscellaneous:
- For some assignments, we are given the chance to resubmit your work to address any
problems identified to improve my grade (a week given to make these adjustments).

# Exercises:
1. Look at some of the binaries within NetBSD and try to think of some pseudocode for
their implementation. Possibly compare it with another OS's implementation of the same
function and try to understand their differences (and why those differences are needed).

# Questions:
