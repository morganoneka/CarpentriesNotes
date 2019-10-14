Moving forward, we're gong to learn more about what makes shell so powerful: the ability to combine existing programs in new ways.

# More with wildcards
Let's return to the `molecules` database, which we already took a look at. If we `cd molecules` then `ls -F`, we see that we have lots of files that end in `.pdb`, which are Protein Data Bank format files, looking at type and position of each atom in a molecule.

We're going to use a new command, `wc`. It counts the number of lines, words, and characters in the files we pass it.

If we wanted to get this info about each file, we could type `wc cubane.pdb`, then `wc ethane.pdb`... or, we could use wildcards. `wc *.pdb`.

## Specifying output
We don't always need all three of those numbers though, so we can provide options to `wc` to specify what output we want. `wc -l *.pdb` provides just the line counts. `wc -w` counts the number of words and `wc -c` counts the number of characters

## Forget the file name?
Try typing `wc -l`. We didn't specify a file, so it's expecting us to type stuff. If you make this mistake, type `ctrl + c`.

# Redirect
What if we want to save this output for later? `wc -l *.pdb > lengths.txt`. Notice nothing is printed out. Now, type `ls`— we see that we have a file called `lengths.txt` that we didn't have before.

Running a new command called `cat`, we can see the output from before. The command `cat` lets us read without writing, and can be used to look at many files at once. For example, try `cat *.pdb`.

Sometimes, if we have long files, `cat` is not the best option. Using `less` only prints out a few lines a time. You can go forward by pressing space, back by pressing `b` and can quit by pressing `q`.

# Sorting
Look at `lengths.txt` once again. If we run `sort lengths.txt`, what do we expect? That isn't what we get. That's because, sort automatically sorts based on characters. If we type `sort -n lengths.txt` we sort numerically, so we get the output we expect.

Run `sort -n lengths.txt > sorted_lengths.txt`.  Now, we can use `head -n 1 sorted_lengths.txt` to see that the file with the fewest lines is methane.

# A caveat
Don't use `>` to output to the same file. Example: `sort -n lengths.txt > lengths.txt`. This will mess things up.

# Two carrots
There is a similar operator `>>`. Let's see how this works.

The function `echo` prints strings that we tell it to. Example: `echo hello world!`.

Now, let's run `echo hello > testfile1.txt`. If we `cat testfile1.txt`, we have the word hello. `echo goodbye > testfile1.txt`. We see that goodbye replaced hello. However, running `echo hello >> testfile2.txt` then `echo goodbye >> testfile2.txt`. We have both words in the file.

# Activities Part 1
https://github.com/morganoneka/CarpentriesNotes/blob/master/UnixShell/04_PipesAndFilters/Activities.md

# Pipes
Sometimes it can be a pain to write intermediate output to files. We can use something called pipes to help. What this does is it takes the output from one command, then feeds it in as output to the next one. 

Let's see how this works by using this to get the file with the smallest number of files. `sort -n lengths.txt | head -n 1`

We can combine as many as we want! `wc -l *.pdb | sort -n | head -n 1`.

# Nelle's files
Ok all of this is great, but how can we use this? Let's `cd` into the `north-pacific-gyre/2012-07-03` directory. Let's take a look at the files. `wc -l *.txt`.

Everything looks great. But if we type this: `wc -l *.txt | sort -n | head -n 5`, we see a file is 60 lines shorter. 

When Nelle looks to see if any files have too short of lines using `wc -l *.txt | sort -n | tail -n 5`, we see that one of the lines have a Z at the end. Her lab puts a Z at the end when files have missing info. That isn't what we want. If we type `ls *Z.txt`, we see that there are two files with these issues.

Nelle doesn't want to lose these files, but she can't use them in certain analyses.

Going forward, we can use `*[AB].txt` to only get files with A or B at the end. 

# Activities Part 2
https://github.com/morganoneka/CarpentriesNotes/blob/master/UnixShell/04_PipesAndFilters/Activities.md
