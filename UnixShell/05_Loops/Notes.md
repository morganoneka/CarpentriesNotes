# Introduction
Loops allow us to run a command (or many commands) on many itmes in a list. They are THE REASON programming is so powerful.

First, `cd creatures`. We have 3 `.dat` files, which have the same structure: common name, classification, date, followed by DNA sequences.

Example: `head -n 5 basilisk.dat minotaur.dat unicorn.dat`. We want to print out the classification for each species, which is on the second line. This means that for each file, we would nead to pipe `head -n 1 | tail -n 1`. For three files, not bad. For a hundred, or a million files... that'd take way too long and be prone to errors.

The general format of a loop (either type or write... can't decide)
```
for thing in list_of_things
do
    operation_using $thing  
done
```

So how can we do this for our example?
```
$ for filename in basilisk.dat minotaur.dat unicorn.dat
> do
>    head -n 2 $filename | tail -n 1
> done
```

Notice how the shell puts a `>` on the line. That reminds us that we haven't finished typing a complete command yet.

# Activities 1
https://github.com/morganoneka/CarpentriesNotes/blob/master/UnixShell/05_Loops/Activities.md

# Another loop example
Slightly more complicated loop:
```
$ for filename in *.dat
> do
>     echo $filename
>     head -n 100 $filename | tail -n 20
> done
```

The shell starts by expanding *.dat to create the list of files it will process. The loop body then executes two commands for each of those files. The first command, echo, prints its command-line arguments to standard output. The head command gets the first 100 lines of the file, then passes them to the tail command. The tail command takes the last 20 lines of that input; this then prints lines 81-100 from each file.

( show file: HowLoopsWork.png )

# Activities 2
https://github.com/morganoneka/CarpentriesNotes/blob/master/UnixShell/05_Loops/Activities.md
