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
