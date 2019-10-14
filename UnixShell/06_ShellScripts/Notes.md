# Introduction
We  are going to take the commands we repeat frequently and save them in files so that we can re-run all those operations again later by typing a single command. For historical reasons, a bunch of commands saved in a file is usually called a shell script, but make no mistake: these are actually small programs.

Return to `molecules` and use `nano middle.sh` to create a file which will become our shell script. Enter text: `head -n 15 octane.pdb | tail -n 5`. 

We've written similar code before, and this will select lines 11-15 of octane.pdb. Save file and exit. Use `ls` to check that the directory `molecules` now has a file called `middle.sh`.

Now, to run this, we type `bash middle.sh` to ask the shell to execute our script.

# Command line arguments
What if we want to select lines from an arbitrary file? We could edit middle.sh each time to change the filename, but that would probably take longer than typing the command out again in the shell and executing it with a new file name. Instead, let’s edit middle.sh and make it more versatile. Type `nano middle.sh` and change to: `head -n 15 "$1" | tail -n 5`.

The special variable `$1`, when used within a shell script, means the first argument on the command line. We put quotes around it in case it includes spaces. The code will not function as expected if there are spaces in the file name.

Now, run `bash middle.sh octane.pdb`. It runs just like before. But we can also run `bash middle.sh pentane.pdb` and it runs the code on a different file.

# Further customization
`nano middle.sh` -> `head -n "$2" "$1" | tail -n "$3"`. If we run `bash middle.sh pentane.pdb 15 5`... what do we get? We can further edit the script's behavior: `bash middle.sh pentane.pdb 20 5`.

# Comments
This works just how we want! But the next person who reads our script may not easily be able to determine what our script does. We can improve our script by adding comments to the top

```
# Select lines from the middle of a file.
# Usage: bash middle.sh filename end_line num_lines
head -n "$2" "$1" | tail -n "$3"
```

A comment starts with a `#` character and runs to the end of the line. The computer ignores comments, but they’re invaluable for helping people (including your future self) understand and use scripts. The only caveat is that each time you modify the script, you should check that the comment is still accurate: an explanation that sends the reader in the wrong direction is worse than none at all.

# Many files, one script
What if we want to process many files in a single pipeline? For example, if we want to sort our .pdb files by length, we would type:

`wc -l *.pdb | sort -n`

because wc -l lists the number of lines in the files (recall that wc stands for ‘word count’, adding the -l option means ‘count lines’ instead) and sort -n sorts things numerically. We could put this in a file, but then it would only ever sort a list of .pdb files in the current directory. If we want to be able to get a sorted list of other kinds of files, we need a way to get all those names into the script. We can’t use $1, $2, and so on because we don’t know how many files there are. Instead, we use the special variable $@, which means, ‘All of the command-line arguments to the shell script’. We also should put $@ inside double-quotes to handle the case of arguments containing spaces ("$@" is equivalent to "$1" "$2" …) Here’s an example:

`$ nano sorted.sh`

```
# Sort files by their length.
# Usage: bash sorted.sh one_or_more_filenames
wc -l "$@" | sort -n
```

`bash sorted.sh *.pdb ../creatures/*.dat`

# Activities 1
https://github.com/morganoneka/CarpentriesNotes/blob/master/UnixShell/06_ShellScripts/Activities.md
