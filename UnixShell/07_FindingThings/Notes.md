# Introduction
In the same way that many of us now use ‘Google’ as a verb meaning ‘to find’, Unix programmers often use the word ‘grep’. ‘grep’ is a contraction of ‘global/regular expression/print’, a common sequence of operations in early Unix text editors. It is also the name of a very useful command-line program.

grep finds and prints lines in files that match a pattern. For our examples, we will use a file that contains three haikus taken from a 1998 competition in Salon magazine. For this set of examples, we’re going to be working in the writing subdirectory:

```
$ cd
$ cd Desktop/data-shell/writing
$ cat haiku.txt
```

Let's find lines that contain the word "not":  `grep not haiku.txt`.

Here, "not" is the pattern we're looking for. Grep takes that and prints out all the lines in the file that contain that word.

By default, grep is case-sensitive. `grep The haiku.txt` misses the lowercase `the`'s.

We can use `grep -w text haiku.txt` to do a case-insensitive search.

Note that a ‘word boundary’ includes the start and end of a line, so not just letters surrounded by spaces. Sometimes we don’t want to search for a single word, but a phrase. This is also easy to do with grep by putting the phrase in quotes. `grep -w "is not" haiku.txt`.

Another useful option is `-n` which numbers the lines that match: `grep -n "it" haiku.txt`.

We can combine options (i.e. flags) as we do with other Unix commands. For example, let’s find the lines that contain the word ‘the’. We can combine the option -w to find the lines that contain the WHOLE word ‘the’ and -n to number the lines that match:

`$ grep -n -w "the" haiku.txt`

Now, we want to use the option -v to invert our search, i.e., we want to output the lines that do not contain the word ‘the’.

`$ grep -n -w -v "the" haiku.txt`

# Activities
https://github.com/morganoneka/CarpentriesNotes/blob/master/UnixShell/07_FindingThings/Activities.md
