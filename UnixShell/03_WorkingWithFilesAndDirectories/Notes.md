# Creating directories
So we've learned how to look at the structure of directories and files... but how do we make directories of our own?

What directory are we in? How can we tell? `pwd`

Let's return to the `data-shell` directory. Say we want to create a directory called `thesis`. First, let's make sure this folder doesn't exist using `ls -F`.

The command we run to create the new folder is: `mkdir thesis`. It stands for "make directory" and makes a directory within our current working directory. Let's use `ls -F` to make sure it worked.

## Tips for creating directories
Spaces can be problematic.  For example: `mkdir morgans things` creates two directories! We could instead run `mkdir "morgans things"`... but that can make things difficult down the line. So, instead, it's best to avoid using spaces in file or folder names.

# Creating files
Let's take a look inside the directory: `ls -F thesis`. There isn't anything in there yet.

Use `cd thesis` to enter the thesis directory. Then, we're going to use a text editor called Nano to create a file called `draft.txt`. Type: `nano draft.txt`.

Nano is a text editor, and I do really mean text. It's not like Word where you can include pictures, or even fonts or colors. It's literally just text.

## Working with Nano
Let's type a few lines of text. 

```
My really awesome science paper

Introduction
In my super cool science paper, I am going to describe my awesome science experiment.
```

When we're done, we can press `ctrl + o` to save the file. After this, we'll be asked what to name the file. The default is `draft.txt`. Press `return` or `enter` to save to that file.

Nano doesn't leave any output when we edit. But when we type `ls` we see that we now have a file called `draft.txt`!

## Using Touch
There's another way to create a file. Try typing the command `touch my_file.txt`. What happened? Type `ls -l`. This shows us the size of the file. What do you notice about the size of our new file? When do you think this might be useful?

# Moving files and directory.
Let's go back to the `data-shell` directory. We have a file called `draft.txt` but that isn't super descriptive. What if we want to change the name to `science_paper.txt`? We're going to use a command called `mv`, or move. 

Type: `mv thesis/draft.txt thesis/science_paper.txt`. Let's run `ls thesis`. 

## Be Careful!
The command `mv` can be dangerous. If the file you're moving to already exists, you can overwrite the file silently—Unix won't tell you! If you want to avoid this, we have a flag we can add. Try: `mv -i file1 file2`.

## Changing directories using mv
Now, let's move the `science_paper.txt` file into our current directory. We'll type `mv thesis/science_paper.txt .`. If we type `ls thesis`, we'll see that the `science_paper.txt` file isn't there. But typing `ls .` shows that it is in our current directory!

# Copy?
We can also copy files. Let's try copying the `science_paper.txt` file back to our `thesis` folder. `cp science_paper.txt thesis/another_science_paper.txt`. If we type `ls thesis`, then we can see our file got copied into the directory!

We also could copy an entire folder. `cp -r thesis thesis_backup`. 

(explain what recursive means here?)

# Activities 1
https://github.com/morganoneka/CarpentriesNotes/blob/master/UnixShell/03_WorkingWithFilesAndDirectories/Activities.md

# Removing
`rm science_paper.txt`. If we use `ls` we can see that the file is gone. Be careful, though. Removing is FOREVER! There is no trash bin to un-delete files from.

We can use `rm` safely though. Let's create a file: `touch temp.txt`. If we do `rm -i temp.txt`, we are prompted before it gets deleted.

## Removing directories
IF we try `rm thesis` we see that doesn't work. Instead, `rm -r thesis`. Super dangerous—use `rm -r -i thesis`.

# Wildcards.
Sometimes we want to do things on a large number of files. How might we go about that?

Type `ls data-shell/molecules`. We have a lot of different files in here. 

The `*` means "zero or more characters of any kind". `ls *.pdb` matches any file that ends in `.pdb`. 

The `?` is also a wildcard. It matches exactly one character. So `?ethane.pdb` matches only `methane.pdb`, but `*ethane.pdb` matches both `ethane.pdb` and `methane.pdb`.

# Activities 2
https://github.com/morganoneka/CarpentriesNotes/blob/master/UnixShell/03_WorkingWithFilesAndDirectories/Activities.md

