# Activities 1
## Renaming files
Suppose you created a file called `statstics.txt`. It was only after creating and saving this file that you realize you misspelled the file name! Which of these commands could you use to fix the mistake? Do you know what the other commands would do?

1. cp statstics.txt statistics.txt
1. mv statstics.txt statistics.txt
1. mv statstics.txt .
1. cp statstics.txt .

<details>
  <summary>Answer</summary>
  
  Number 2 is correct.

The first command will create a second file with the correct name, but the incorrectly name file will still exist.

The third and fourth commands indicate where to move or copy the file to, but don't provide a new file name. 
</details>


## Moving and copying
Consider the following commands and their outputs:
- `pwd`
  - `/Users/jamie/data`
- `ls`
  - `proteins.dat`
- `mkdir recombine`
- `mv proteins.dat recombine/`
- `cp recombine/proteins.dat ../proteins-saved.dat`

Which of these would be the result if we typed `ls`?
1. proteins-saved.dat
2. recombine
3. proteins.dat recombine
4. proteins-saved.dat

<details>
  <summary>Answer</summary>
  
The `mkdir` command will create a new directory called `recombine`. The `mv` command after that will move `proteins.dat` into the new directory. Finally, the `cp` command will create a copy of the `recombine/proteins.dat` file in the parent directory of our current working directory. Then, our current working directory will contain zero files and one folder, the folder called `recombine`. Therefore, the second answer is correct!
</details>


***

# Activities 2

## List files matching a pattern
When our working directory is `molecules`, which commands will produce the following output: `ethane.pdb  methane.pdb`?
1. `ls t*ane.pdb`
1. `ls *t?ne.*`
1. `ls *t??ne.pdb`
1. `ls ethane.*`

<details>
  <summary>Answer</summary>
 
 Number 3 is correct. Number 1 will only match files that begin with "t" and end with "ane.pdb", which none of the files do. Number 2 shows all files whose names start with zero or more characters, followed by `t`, then a single character, then `ne.` followed by two or more characters. This will give us `octane.pdb` and `pentane.pdb`. Number 4 only shows files starting with `ethane.`, which would only match `ethane.pdb`.
</details>


## Organizing directories and files
Continuing with "molecules" as our working directory, what command(s) could we use to copy `octane.pdb` and `pentane.pdb` to the `data-shell` directory? Remember that `data-shell` is the parent directory of `molecules`.
1. `cp ???tane.pdb data-shell`
1. `cp *tane.pdb ../`
1. `cp *tane.pdb data-shell`
1. `cp ???tane.pdb ~`

<details>
  <summary>Answer</summary>
  Number 2 is correct. Number 1 and 3 will result in an error, because there is no `data-shell` directory in `molecules`. Number 1 and 4 are incorrect because `???tane.pdb` will only match `pentane.pdb` and not `octane.pdb`. Also, number 4 copies the files to the user's home directory, not the `data-shell` directory.
</details>

## Reproducing a folder structure
Suppose you are starting a new experiment and want to create a specfic directory structure, so that your output data is organized. You want an outer folder called "2019-10-14", a subfolder called "data", and within "data" two folders called "process" and "raw". In other words, you want your directory structure to look like this:

```
2019-10-14/
└── data/
    ├── processed/
    └── raw/
```
    
Assuming you want "2019-10-14" to be in your current working directory, how would you create this file structure? Tip: you'll definitely want to use the command that makes directories, and you might also make use of the command that changes your working directory.


<details>
  <summary>Answer</summary>
There are a lot of solutions. Here are two:

```
$ mkdir 2019-10-14
$ mkdir 2019-10-14/data
$ mkdir 2019-10-14/data/processed
$ mkdir 2019-10-14/data/raw
```

(or)

```
$ mkdir 2019-10-14
$ cd 2019-10-14
$ mkdir data
$ cd data
$ mkdir raw
$ mkdir processed
```

But there are plenty of ways to do this that are correct! 
</details>
