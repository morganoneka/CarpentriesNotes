# Activities: Part 1

## Using the double carrots
Navigate back to the `data-shell` directory. Suppose you wanted to create a file that lists all the `.pdb` files in the `molecules` folder **AND** the contents of the file "`data/amino-acids.txt`". In other words, the file looks like this:
```
molecules/cubane.pdb
molecules/ethane.pdb
molecules/methane.pdb
molecules/octane.pdb
molecules/pentane.pdb
molecules/propane.pdb
Alanine		Ala
Arginine	Arg
Asparagine	Asn
Aspartic acid	Asp
Cysteine	Cys
Glutamic acid	Glu
Glutamine	Gln
Glycine		Gly
Histidine	His
Isoleucine	Ile
Leucine		Leu
Lysine		Lys
Methionine	Met
Phenylalanine	Phe
Proline		Pro
Serine		Ser
Threonine	Thr
Tryptophan	Trp
Tyrosine	Tyr
Valine		Val
```

How would you do this?

1)
```
ls molecules/*.pdb >> myfile.txt
cat data/amino-acids.txt >> myfile.txt
```

2)
```
ls molecules/*.pdb > myfile.txt
echo data/amino-acids.txt > myfile.txt
```

3)
```
ls molecules/*.pdb > myfile.txt
echo data/amino-acids.txt > myfile.txt
```

<details>
  <summary>Answer</summary>
  
  Number 1!
  
  Number 2 uses `echo`. This will print out `data/amino-acids.txt` instead of the _contents_ of `data/amino-acids.txt`
  
  Number 3 again uses `echo` where it shouldn't, but there is a second mistake. The `>>` on the second line will write over the contents we put in `myfile.txt` in the previous command.
  
</details>

# Activities: Part 2
## Piping Commands Together
In our current directory, we want to find the 3 files which have the least number of lines. Which command listed below would work?

1. `wc -l * > sort -n > head -n 3`
2. `wc -l * | sort -n | head -n 1-3`
3. `wc -l * | head -n 3 | sort -n`
4. `wc -l * | sort -n | head -n 3`

<details>
  <summary>Answer</summary>
  
  Option 4 is the solution. The pipe character `|` is used to connect the output from one command to the input of another. `>` is used to redirect standard output to a file. Try it in the `data-shell/molecules` directory!
  
</details>

## Pipe Reading Comprehension
A file called `animals.txt` (in the `data-shell/data` folder) contains the following data:

```
2012-11-05,deer
2012-11-05,rabbit
2012-11-05,raccoon
2012-11-06,rabbit
2012-11-06,deer
2012-11-06,fox
2012-11-07,rabbit
2012-11-07,bear
```

What text passes through each of the pipes and the final redirect in the pipeline below?

`cat animals.txt | head -n 5 | tail -n 3 | sort -r > final.txt`

Hint: build the pipeline up one command at a time to test your understanding

<details>
  <summary>Answer</summary>
  The `head` command extracts the first 5 lines from `animals.txt`. Then, the last 3 lines are extracted from the previous 5 by using the tail command. With the `sort -r` command those 3 lines are sorted in reverse order and finally, the output is redirected to a file `final.txt`. The content of this file can be checked by executing `cat final.txt`. The file should contain the following lines:

```
2012-11-06,rabbit
2012-11-06,deer
2012-11-05,raccoon
```
</details>


## Pipe Construction
For the file `animals.txt` from the previous exercise, consider the following command:

`cut -d , -f 2 animals.txt`

The `cut` command is used to remove or ‘cut out’ certain sections of each line in the file, and `cut` expects the lines to be separated into columns by a Tab character. A character used in this way is a called a **delimiter**. In the example above we use the -d option to specify the comma as our delimiter character. We have also used the `-f` option to specify that we want to extract the second field (column). This gives the following output:

```
deer
rabbit
raccoon
rabbit
deer
fox
rabbit
bear
```

The `uniq` command filters out adjacent matching lines in a file. How could you extend this pipeline (using uniq and another command) to find out what animals the file contains (without any duplicates in their names)?

<details>
  <summary>Answer</summary>
  
  `cut -d , -f 2 animals.txt | sort | uniq`
  
</details>
