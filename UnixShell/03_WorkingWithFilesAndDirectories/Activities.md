# Activities 1
## Renaming files
Suppose you created a file called `statstics.txt`. It was only after creating and saving this file that you realize you misspelled the file name! Which of these commands could you use to fix the mistake? Do you know what the other commands would do?

1. cp statstics.txt statistics.txt
1. mv statstics.txt statistics.txt
1. mv statstics.txt .
1. cp statstics.txt .

### Answer
Number 2 is correct.

The first command will create a second file with the correct name, but the incorrectly name file will still exist.

The third and fourth commands indicate where to move or copy the file to, but don't provide a new file name. 

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

### Answer
The `mkdir` command will create a new directory called `recombine`. The `mv` command after that will move `proteins.dat` into the new directory. Finally, the `cp` command will create a copy of the `recombine/proteins.dat` file in the parent directory of our current working directory. Then, our current working directory will contain zero files and one folder, the folder called `recombine`. Therefore, the second answer is correct!

***

# Activities 2
