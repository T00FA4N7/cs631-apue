# The History of UNIX
The journey begins in 1969 at AT&T in New Jersey where developers Dennis Ritchie & Ken
Thompson worked with Dough McIllroy and Joe Ossana to build a replacement of MULTICS OS.
- The MULTICS OS was primarily defined by using a single-level memory where memory can be
located in RAM or storage disk yet doesn't matter when it comes to the physical location
for processes inside the OS.

Together, the C programming language was created by Ritchie in parallel with UNIX (as it
is the primary language that **eventually** built up the system) and descended from the
B programming language (designed by Thompson). After this development, UNIX was rewritten
in C in 1973 allowing the OS to be easily portable (it was originally written in assembly
for the specific target platform and hardware of the system).

Two years after, students from UC Berkeley bought a copy of UNIX and made some variations
to it creating BSD or the Berkely Software Distribution of UNIX. At the root of the tree,
UNIX decided to spread into 2 directions: BSD & System V (paid variation of UNIX).

## Timeline of UNIX History with Notable Events:
- 1984 -> 4.2BSD released (TCP/IP) [Two very important protocols that control the world of
technology we are living in]
- 1991 -> Linus Torvalds starts working on the Linux kernel (Yay Linux!)
    - Proper Name: GNU/Linux (No Other Way Around It)
- 1993 -> Settlement of USL vs BSDi; NetBSD and FreeBSD were created from this event
    - Time worked in favor for GNU/Linux as the lawsuit introduced a free version of
    UNIX that businesses may be interested in in comparison to the BSD counterparts ->
    possibly explaining Linux's market dominance currently (over BSD)
- 1994 -> Single UNIX Specification introduced
- 1995 -> 4.4 BSD-Lite Released; OpenBSD forked off NetBSD
- 2000 -> Darwin created (for MacOS)
- 2005 -> Hadoop; DTrace; ZFS (advanced file system); Solaris Containers
- 2006 -> AWS ("Cloud Computing" comes full circle)
- 2008 -> Android; Solaris open sourced as OpenSolaris

## UNIX is Omnipresent:
Clearly from the trees and graphs shown in the slides (and video), one thing can easily
be stated regarding about UNIX -> UNIX is omnipresent. In most of the technologies we
use on a day-to-day basis, it functions based on a UNIX-like OS. This, in turn, explains
one of the major points from the first segment in which allowing us to learn about UNIX
and its environment can help us understand the technologies we use (around us) better.

# Miscellaneous:
- Within a BSD system, one is able to view the history of their system in the 
`/usr/share/misc` directory and find the family tree of OS'es from there.

# Questions:
- What is the single UNIX specification? Is it similar to the current form of POSIX?
    - According to Slide Week 1 Segment 3, POSIX has developed and is now equivalent
    to the Single UNIX Specification (SUS).
