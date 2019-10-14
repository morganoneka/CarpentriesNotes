# Activities 1
## Exploring more ls flags
What happens when you run the following commands?:
- `ls -l`
- `ls -h`
- `ls -l -h`
- `ls -lh`

What do you notice about the output for `ls -l -h` and `ls -lh`?

<details>
<summary>Answer</summary>

The `-l` option makes ls use a long listing format, showing not only the file/directory names but also additional information such as the file size and the time of its last modification. If you use both the `-h` option and the `-l` option, this makes the file size ‘human readable’, i.e. displaying something like 5.3K instead of 5369. 

`ls -l -h` and `ls -lh` give the same answer. When you use flags that are only one character (for example, `-l`, and not `--help`), you can combine them together in one flag if you want. Doing this is entirely based on personal preference, and both are equally right!
</details>

## Reverse chronological order
By default, `ls` lists the contents of a directory alphabetically by name. `ls -t` lists items by time of last change, and `ls -r` lists contents of a directory in reverse order. Which file is displayed last when you combine the `-t` and `-r` flags?

<details>
<summary>Answer</summary>

The most recently changed file is listed last when using `-rt`. This can be very useful for finding your most recent edits or checking to see if a new output file was written.
</details>

## Reading the manual
Using `man ls` or `ls --help` (whichever works on your machine). Find the flags that let ls:
- Recursively list subdirectories 
- Sort files by time of file creation (when combined with the `-t` flag)
- Print output that is not sorted

<details>
<summary>Answer</summary>
`ls -R` recursively lists subdirectories. `ls -U -t` uses the time of file creation for sorting. `ls -f` prints output that isn't sorted in any obvious way.
</details>

***

# Activities 2

## Absolute vs. relative paths
Starting from `/Users/amanda/data`, which of the following commands could Amanda use to navigate to her home directory, which is `/Users/amanda`?

1. `cd .`
1. `cd /`
1. `cd /home/amanda`
1. `cd ../..`
1. `cd ~`
1. `cd home`
1. `cd ~/data/..`
1. `cd`
1. `cd ..`

<details>
<summary>Answer</summary>

5, 7, 8, and 9 are correct.
</details>

## Relative path resolution
Looking at this file: http://swcarpentry.github.io/shell-novice/fig/filesystem-challenge.svg

1. Using this diagram, if `pwd` displays `/Users/thing`, what will `ls -F ../backup` display?
2. Using the filesystem diagram below, if "pwd" displays "/Users/backup", and "-r" tells "ls" to display things in reverse order, what command could you use to produce the following output: "pnas_sub/ pnas_final/ original/"

<details>
<summary>Answer</summary>

1. `original/ pnas_final/ pnas_sub/`
2. `ls -r -F` or `ls -r -F /Users/backup`
</details>
