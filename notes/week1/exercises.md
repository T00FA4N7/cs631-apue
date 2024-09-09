# Exercise #1:
For this exercise, I saw that there was a syntactical issue with a missing semicolon
for the `printf` statement so I first fixed that. After attempting to compile the program,
I had a implicit function declaration warning/error, so I used the man page to inform me
of the right header file for the correct function declaration. Additionally, I saw that
the result of this function was a pointer which could possibly result in a nullpointer
being returned. Hence, I checked the pointer result after calling the function: if it was
a null pointer, I printed an error message with `fprintf` and returned a non-zero number;
otherwise, I printed the proper greeting message and returned 0 to indicate a successful
execution.

```c
#include <stdio.h>
#include <unistd.h>

int
main() {
    char *login = getlogin();
    if (login == NULL) {
        fprintf(stderr, "Error: string returned from getlogin in NULL");
        return 1;
    }

	printf("Welcome to CS631 Advanced Programming in the UNIX Environment, %s!\n", login);
    return 0;
}
```

# Exercise #2:
I am looking at the implementation of `ls` for OpenBSD and Ubuntu. In terms of how
code should be written, I feel that Ubuntu (GNU/Linux) definitely emphasizes more on
encapsulation rather than having a large number of variables to represent different things
like (BSD). While that should make it easier to read, they tend to group a lot of things
together where possibly some people may not agree with the choice as the devs. 

Another detail that I am seeing is that because Ubuntu (GNU/Linux) has encapsulation, 
the size of the functions are a lot more similar in comparison to BSD. More specifically,
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
