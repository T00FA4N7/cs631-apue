Before reviewing the basics of UNIX (including shells, functions, the C language, etc),
let's take a top-down approach to understanding how UNIX is constructed.

# Top-Down Hierarchy of UNIX:
At the outside-most level of UNIX comes applications; these are applications that users
use for their own personal reasons such as Slack, an Email Client, music players, etc.

The next level below is shell; the shell is also an application but is different than
the layer above as it introduces the user to interact with lower-level parts of the shell
directly (it is considered as a different part). Additionally, library routines are in
the same level as they are pre-written pieces of code that perform common tasks (similar
to the binaries that provide functionalities in a shell).

The next level are system calls - which are really the pathway of going from userspace
to kernelspace. In any function that requires to use some hardware, the program will
travel from userspace to kernelspace (and possibly back to userspace); but to do so,
the programs call wrapper functions which ultimately call a system call that allows
this change of modes (spaces) for the machine. Applications (or even users using the shell)
can use the wrapper functions that call the system calls or sometimes even use the system
calls directly.

Finally, one of the most important parts of the OS: the kernel. Specifically, for UNIX 
and most UNIX-based systems, the OS uses a monolithic kernel which means that the kernel
performs most tasks and actions of the system (leaving very little to be in userspace).
It has its pros and cons as communication between different processes has very little
overhead, yet if one process were to suspend, it can prevent the whole kernel from moving
on to its next action. More specifically, ther kernel controls the hardware, manages
memory, performs task scheduling, handles file system, IPC, network connections, and a
lot more.

# Docs in UNIX Environments:
As you can see, there is a lot of code that we deal with when using UNIX environments
whether it be in writing our own C programs or using shell commands for a particular task.
Sometimes, in order to get further with your task, you may need to research more about
a function or command that you are using; you could search online and go through a cycle
of purple links or you could use a better solution: man pages!

Man (Manual) pages are documentation for shell commands and also std-lib C functions that
are native on your machine. These provide clear instructions, descriptions, essentially
every single detail that you need regarding a command/function and allow you to get those
details quite easily. To organize the list of commands and functions within the man pages,
there are 3 different categories:

1. User Commands
    - Contains documentation for your most common programs that you run on your shell: ls,
    cat, cd, grep, etc
2. System Calls
    - Contains documentation for the system calls (userspace -> kernelspace) like open, 
    close, read, write
    - Points in kernel code where functions are implemented
3. Library Calls
    - Contains C lib functions such as printf, fprintf, getlogin, etc
    - Userspace code that performs desired functions

Most UNIX machines follow the IEEE POSIX standard where these OS'es must have the same
API, command-line utilities, and interfaces (including man pages) for software
compatibility for different variants of UNIX.

# C Language in UNIX Environments:
Although the C language was developed in parallel with UNIX, because it can be used on
different systems (including those not UNIX-based), it follows a different standard than
POSIX namely: ANSI.

Due to the C language following the ANSI standard, we now have a bunch of more features
that are greatly important to developers:
- Function Prototypes
    - Separate function between its declaration and implementation
- Generic Pointers
    - Void pointer type so that we can provide generality to our functions by not
    specifying a certain type (reducing redundant code)
    - Additionally comes with some risks (cannot read a void pointer)
- Abstract Data Types
    - Makes C portable; let's say I want to use a type that is specific to a library
    such as `time_t`; This type is used for anything to do with time in the C library,
    but if I wish to execute the same program on a Windows machine (without adt's, I would
    have to write a new program to run on that architecture)
    - Minimizes changing code and also reduces amount of redundant code
- Error Handling:
    - Return Values:
        - Within ANSI C functions, we can always have some expectation of what the value
        returned will be based on its behavior (which just simply makes life easier)
    - `errno` variables:
        - Now, if we have an error in our program, rather than debugging it solely by
        ourselves and checking lines that don't have a problem; we can use the value of
        the global variable `errno` to tell us what went wrong in our program
    - `strerror` & `perror`:
        - `errno` is great but it only provides a number; having some way of transforming
        the number into a message for the developer/user to understand would be great and
        that can be done with these two functions

# Shells in a UNIX Environment:
At the most basic level, shells are programs that repeat indefinitely where they take in
standard input and try to execute a command based on the given standard input and hopefully
show some output (either to stdout or stderr). In order to execute this command, the program
has to fork (create a new process), and make that new process exec the command given. The
original (parent) process must wait for the new process to finish/terminate and then may
continue.

## Consistency in a UNIX Environment:
One of the fundamental parts of the UNIX philosophy is consistency: treating regular files,
directories, sockets, pipes all as files, tools that behave the same no matter the version
as they are based on the UNIX standard, tools that behave in a predictable manner.

For **our class**, we wish to do the same and try to write programs that almost look
as part of the source code for an OS rather than a random boring CS assignment.

# Concepts within the UNIX Philosophy:
- Simplicity
    - Split everything into the most fundamental blocks so that we can keep code reusable
    and modular
- Least Surprise
    - Code that does what you expect it to do in all situations (right and wrong hopefully)
- Take in from stdin, put out on stdout
    - Very useful for pipes, make life easier by having a generalized definition of where
    you take in and throw data
- Have meaningful strings and codes
    - This is important just to have a good developer experience when working in an env.
    like UNIX
- Have good documentation for their code
    - Same like above; very important to have a good developer experience when working in
    an environment like UNIX

# Files and Directories in a UNIX Environment:
In simple terms, the filesystem of UNIX and UNIX-based OS'es are a tree starting at the
root directory (/) and traversing our way down with directory or filenames. For files that
are deep within the filesystem, we add a (/) character at the end of the directory name
to the absolute file path of the directory we just traversed through.

As mentioned above, directories are files too; but special in that they contain mappings
between inodes (index nodes) and filenames called directory entries which allow users
to access the files inside of a directory very easily and quickly.

# Users in a UNIX Environment:
In a UNIX Environment, anyone and everyone is treated as some number called a UID. In
order to give permissions to that user, put them into a group, etc, we use numbers to
represent this and that's how a UNIX environment functions with user and group id.

# Time in a UNIX Environment:
In order to analyze programs (and hopefully how to make them faster), we need a way to time
them and with the UNIX environment we can get 3 main time values:
1. Clock Time -> Time that has elapsed in total
2. User CPU Time -> Time the process spent in userspace
3. System CPU Time -> Time the process spent in kernelspace

# I/O in a UNIX Environment:
To make the I/O API very extensible and easy to use for UNIX systems, we treat every
I/O as a file within our file descriptor table (numbers that identify a file to the kernel).

File I/O in UNIX comes in two different flavors: buffered & unbuffered. Unbuffered uses
system calls that directly go to the kernel which directly writes to the file in name. 
Buffered uses library functions that write to a buffer in user space (which when filled 
gets written to the file using a system call).

# Processes in a UNIX Environment:
A program that executes in memory is called a **process**. Every process (similar to a
user) has an integer (namely a PID) that represents itself (for other programs to identify).

The sequence of moves used when working with processes in a UNIX environment is fork, exec,
and wait where the parent process forks creating a child process, giving the child process
an executable to run, and the parent process waiting for the child process to execute and
terminate before it moves on with the rest of the instructions it has to execute.

## Signals in a UNIX Environment:
Signals are ways of informing a program of a new event and respectively to perform an
action in the condition of this new event occurring. Within the UNIX environment, users
get full control over what happens when a particular signal is sent:
- Let the default action remain for a process when that signal is sent
- Force no action to occur for a process when that signal is sent
- Perform some custom function to occur for a process when that signal is sent

# Miscellaneous:
- For some commands, there might be a system call and library call with the same name. In
order to differentiate them when using man pages, you can add the specific section of
the function you are looking for like: `man 3 printf` (looks for the C lib printf func).
    - This is because the man function will always pull up the first page it finds.
- The rationale section is pretty cool on the Single Unix Specification website since it
gives a glimpse on the thoughts that came into mind when implementing these
functionalities.
- All our code for this class has to compile using a cc compiler on a NetBSD 10.0 system
with the flags: `-Wall -Werror -Wextra`
- I have used some of the EXIT flags in the past, but didn't know that there were so many
other flags for the exit command within the `sysexits(3)` man page.
- Signals to remember: Ctrl + C sends the interrupt signal while Ctrl + d sends the EOF
signal.
- Avoid magic numbers in C programming and use flags/keywords that are readable to others
(this is an ettiquette that literally makes sense).
- Can use the `getpid` function in the C lib to get the pid of the currently executing
function (which likely will be the main thread).

# Questions:
- For the `getlogin` function, how was it possible for the program to successfully exec.
without the `unistd.h` lib but with the forward declaration? Where did the program know
the implementation of the `getlogin` function?
- If the compiler doesn't know what a function returns, it assumes that it will return
an integer. This is an interesting functionality, I wonder why the developer of the C
compiler did so?
- I understand why `ls -l` and `cat <file>` failed in simple-shell.c, but am not too
sure about `exit`.
- What is the point of using the include guard in simple-cat.c program?
