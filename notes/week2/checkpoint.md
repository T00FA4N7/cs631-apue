Please enter your full (preferred) name: Amartya Kalra

Please enter your Stevens username: akalra3

What happens if you run 'ulimit -n 0'? Why?
- Running `ulimit -n 0` sets the maximum number of open file
descriptors per process to 0; I was able to determine this by
looking at the man pages and searching for the n flag within the
command. I ran this command on both my NetBSD and Linux systems
and got errors when I tried to write a program to open files
such as EMFILE (Error Max File Descriptors) and ENFILE
(Error No File Descriptors).

What, if anything, did you learn? Any other comments?
- I learned that if we have multiple file descriptors opened of
the same files; we need to be even more sure about the data we
are handling with. Because stdlib doesn't provide locks on these
files, if a program were to handle 2 or more file descriptors of
the same file, actions need to be synchronized but also programmers
need to be aware of the modes too as that can definitely lead to
lots of confusion (so really make sure that each decision you make
for every line of code is what you want and exactly what you want
- nothing more and nothing less). Also, it was interesting that if
we have two or more file descriptors for the same file, their offsets
are independent of one another (which again is something a developer
has to be aware about if there is the writing permission on these
files). In terms of the exercise, the task of replacing a specific
word seems daunting; but for my first idea, I was thinking of copying
the entire file into memory, replace the word, and write back to the
file; but am curious if there is a better solution (or even if there are
possible bugs in mine).

Identify a flag that may be passed to open(2) that was not discussed in the videos or slides.
What does it do? Is it OS specific?
- A flag that may be passed to open that was not discussed in the
videos or slides was O_TMPFILE. For some reason, I could only find this
flag in GNU/Linux machines and none of the BSD systems (at least not for
OpenBSD and NetBSD). The use of this flag is to provide a way to create a
temporary file that is not linked to any directory (ensures that the file
is not accessible to other processes). The unique thing about it is that
in order to create a file with this flag, for the file to be created, the
first argument points to a directory instead of a file like most other
instances of calling the open system call.

Run the hole.c program on different Unix systems (NetBSD, macOS, Linux, ...).
Does the behavior differ? Why?
- Besides NetBSD, I was able to run the program on GNU/Linux systems
(Debian & EndeavourOS) and in both scenarios they created sparse files
(and when copied also created sparse files). I was able to go into the
man pages and see that they supported sparse files (which rather confirmed
my experience). But, I was curious as to the explanation of why they use
this standard and luckily, I was able to get somewhat of an answer from ArchWiki. 

In Arch, when reading sparse files, the file system automatically (and transparently)
converts metadata that represents empty blocks into "real" blocks filled with
null bytes. Also it states that the advantage of sparse files is that storage
is only allocated when actually needed. Additionally, another interesting fact
is that while Arch supports sparse files to be copied as sparse files, for other
applications that may run, they could possibly copy the entire file (so we can
expect different types of behavior which is unfortunately not good).

If you create a new file, write, say, 10 bytes of data, and then seek to the end of the file, where do you end up? Why?
You end up at the offset of 10 bytes (or at least in this scenario the end
of the file). To answer the question why, it seems blatantly obvious that if
we create a new file (should be truncated to 0 bytes), write 10 bytes of data,
and seek to the end, we would be located at the end of that block of bytes hence
at the 10 byte offset. However, reading this question and thinking of that answer,
slightly made me unsure so I decided to write a program to show where would I be
and it also shows 10 bytes after the starting position of the file.

Consider the following two commands, cmd >file 2>&1 and cmd 2>&1 >file. Is there a difference?
- Yes, there is a difference. For the first command, both stdout and stderr will
be redirected to file. Reading from left to right, the command directs stdout to file,
and after takes stderr output to the location of file descriptor 1 which was changed
to file in the section of the command beforehand.

For the second command, stderr is directed to the terminal while stdout is directed
to file. Reading from left to right, the command takes the stderr to the location
of file descriptor 1 which is the terminal (at this point in time) and then
takes the stdout and redirects that to file.

Please note any particular (sub)topics or aspects of this week's materials that you would like me to revisit in class:
- I don't believe I have any questions; more so, that I need to review my notes and
take another look to remember the slightly lose parts in my mind right now. If
something does change, I'll make sure to ask in class!
