# Activities 1

## Variables in Loops
This exercise refers to the data-shell/molecules directory. ls gives the following output:

`cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb`

What is the output of the following code?

```
$ for datafile in *.pdb
> do
>    ls *.pdb
> done
```

Now, what is the output of the following code?

```
$ for datafile in *.pdb
> do
>	ls $datafile
> done
Why do these two loops give different outputs?
```

<details>
<summary>Answer</summary>

The first code block gives the same output on each iteration through the loop. Bash expands the wildcard `*.pdb `within the loop body (as well as before the loop starts) to match all files ending in `.pdb` and then lists them using `ls`. The expanded loop would look like this:

```
$ for datafile in cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb
> do
>	ls cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb
> done
cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb
cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb
cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb
cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb
cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb
cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb
```

The second code block lists a different file on each loop iteration. The value of the datafile variable is evaluated using `$datafile`, and then listed using `ls`.

```
cubane.pdb
ethane.pdb
methane.pdb
octane.pdb
pentane.pdb
propane.pdb
```
</details>

## Limiting Sets of Files
What would be the output of running the following loop in the data-shell/molecules directory?

```
$ for filename in c*
> do
>    ls $filename
> done
```

1. No files are listed.
1. All files are listed.
1. Only cubane.pdb, octane.pdb and pentane.pdb are listed.
1. Only cubane.pdb is listed.

<details>
<summary>Answer</summary>
4 is the correct answer. * matches zero or more characters, so any file name starting with the letter c, followed by zero or more other characters will be matched.
</details>

How would the output differ from using this command instead?

```
$ for filename in *c*
> do
>    ls $filename
> done
```

1. The same files would be listed.
1. All the files are listed this time.
1. No files are listed this time.
1. The files cubane.pdb and octane.pdb will be listed.
1. Only the file octane.pdb will be listed.

<details>
<summary>Answer</summary>

4 is the correct answer. * matches zero or more characters, so a file name with zero or more characters before a letter c and zero or more characters after the letter c will be matched.
</details?

## Saving to a file in a loop
In the `data-shell/molecules` directory, what is the effect of this loop?

```
for alkanes in *.pdb
do
    echo $alkanes
    cat $alkanes > alkanes.pdb
done
```
1. Prints cubane.pdb, ethane.pdb, methane.pdb, octane.pdb, pentane.pdb and propane.pdb, and the text from propane.pdb will be saved to a file called alkanes.pdb.
1. Prints cubane.pdb, ethane.pdb, and methane.pdb, and the text from all three files would be concatenated and saved to a file called alkanes.pdb.
1. Prints cubane.pdb, ethane.pdb, methane.pdb, octane.pdb, and pentane.pdb, and the text from propane.pdb will be saved to a file called alkanes.pdb.
1. None of the above.

<details>
<summary>Answer</summary>
The text from each file in turn gets written to the alkanes.pdb file. However, the file gets overwritten on each loop interation, so the final content of alkanes.pdb is the text from the propane.pdb file.
</details>

Also in the data-shell/molecules directory, what would be the output of the following loop?

```
for datafile in *.pdb
do
    cat $datafile >> all.pdb
done
```

1. All of the text from cubane.pdb, ethane.pdb, methane.pdb, octane.pdb, and pentane.pdb would be concatenated and saved to a file called all.pdb.
1. The text from ethane.pdb will be saved to a file called all.pdb.
1. All of the text from cubane.pdb, ethane.pdb, methane.pdb, octane.pdb, pentane.pdb and propane.pdb would be concatenated and saved to a file called all.pdb.
1. All of the text from cubane.pdb, ethane.pdb, methane.pdb, octane.pdb, pentane.pdb and propane.pdb would be printed to the screen and saved to a file called all.pdb.

<details>
<summary>Answer</summary>
3 is the correct answer. >> appends to a file, rather than overwriting it with the redirected output from a command. Given the output from the cat command has been redirected, nothing is printed to the screen.
</details>
