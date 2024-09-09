Please enter your full (preferred) name: Amartya Kalra

Please enter your Stevens username: akalra3

Briefly describe your experience level using a Unix-like OS:
I began using Unix-like operating systems in high school with embedded systems projects involving Arduinos and Raspberry Pi.
In both high school and college, I delved into low-level computer systems and security using shell utilities, text editors like vi and nano, and debugging tools such as gdb.
For personal development, I have created basic PowerShell and Bash/Zsh scripts to automate tasks in my programming environment.
Additionally, I have set up virtual machines running OpenBSD, Arch, Debian, and Ubuntu, experimenting with various desktop environments.
In my two internships, I worked extensively with Ubuntu servers that provided only a command-line interface.
This experience helped me become comfortable navigating filesystems and utilizing development tools through text-based user interfaces (TUIs),
such as lazydocker and lazygit, and working with compiler tools like makefiles, cmake, etc.
Currently, I primarily use EndeavourOS alongside Windows for personal use and extensive coding, employing terminal-based tools like zellij, neovim, yazi, and many more.

Briefly describe your programming experience (languages you know, skill level, group experience, project size in KLOC):
I consider myself to be between an intermediate and advanced programmer. I primarily code in C++, Python, and Rust, with substantial experience in Java and C.
I also have some experience with JavaScript, OCaml, and Go. My individual projects typically involve around 1,000 lines of code,
while group projects range from 2,000 to 3,000 lines.

My personal projects include building ray tracers with BVH optimizers, ray marchers, and other computer graphics techniques.
I am currently developing a Rust-based shell function to encrypt API keys in a repository and manage encrypted commits.
Additionally, I have worked on systems projects involving programming servos and motors for robotic applications.

I also have a strong interest in machine learning and deep learning. My projects in this area include developing ML programs for data collection, preprocessing,
and model training. Notable projects include creating models for problem identification and classification, music genre classification
using dimensionality reduction techniques, and stock trading analysis.

During my two internships, I worked on large codebases, which improved my ability to read and write clean, maintainable code.
One internship involved writing a mesh generation algorithm for facial recognition systems, while the other focused on developing models
and embeddings for efficient seismic imaging, involving extensive low-level optimizations.

Make sure to fetch and extract the cs631 APUE code examples as well as the NetBSD source code. Comment on anything that you found noteworthy.
I looked at the implementations of `ls`, `cat`, `mv`, and `grep` for OpenBSD and Ubuntu. In terms of how
code should be written, I feel that Ubuntu (GNU/Linux) definitely emphasizes more on
encapsulation rather than having a large number of variables to represent different things
(BSD). While encapsulation should make it easier to read, they tend to group a lot of things
together where possibly some people may not agree with the choice as the devs. 

Another detail that I am seeing is that because Ubuntu (GNU/Linux) has encapsulation, 
the size of the functions are a lot more comparable in comparison to BSD. More specifically,
the functions in BSD are all of various sizes (primarily very large groups of LOC clustered
together) while Ubuntu for the most part has reasonable function sizes. This is very
clearly shown by the infintitely nested if-statements, switch statements in OpenBSD 
functions while having a much more methodical, cleaner way of handling different cases
in GNU/Linux (essentially way, way more organization in GNU/Linux).

Also, it seems that there are a lot more features built within the GNU/Linux systems as
there almost 3-4 fold the size of the OpenBSD programs.

One odd characteristic I saw (which is kind of similar to their programming styles) is
the length and frequency of comments in their programs. OpenBSD had somewhat large comments
but not too frequently where as GNU/Linux had at least a comment every 5 LOC but were
relatively short.

Moreover, the OpenBSD code didn't use advanced features (according to me and the programs
I have seen and written) in comparison to GNU/Linux. GNU/Linux used enums, structs, a lot
more variables on the heap, macros, signal handling in their implementations compared to
OpenBSD.

Make sure to run all the code examples from the Week 01 videos. If you have any questions, not them here.
1. For the `getlogin` function, how was it possible for the program to successfully exec.
without the `unistd.h` lib but with the forward declaration? Where did the program know
the implementation of the `getlogin` function?
2. I understand why exit failed in the simple-shell.c program, but I'm curious how would we be able to
include it when building our own mini-shell. Would we natively add the exit command as a built-in or is there
some way we can include all shell built-ins into our program?
3. What is the point of using the include guard in simple-cat.c (and other) programs? Is it just for ettiquette
or is there another reason for this?

Please note any particular (sub)topics or aspects of this week's materials that you would like me to revisit in class:
When discussing about the function prototypes in the ANSI standard for C, I was not entirely sure
the benefits that come from this property. I originally thought it would be good for function overloading,
but realized that is not implemented in C, so I just want to learn about the benefits of this property in a programming language.

In the lecture, you stated that the if the C compiler doesn't know what a function returns, it assumes that it will return
an integer. By any chance, I wanted to know if you could explain more on this and maybe correlate this choice to one of the
concepts in their UNIX philosophy.
