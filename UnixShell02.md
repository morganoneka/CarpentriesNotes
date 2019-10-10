# Directory Names and Structures
Your home directory (where you are when you open up the command line) is going to look different depending on if you use Windows or Mac. For Mac: `/home/nelle`, and on Windows it will be similar to `C:\Documents and Settings\nelle` or `C:\Users\nelle`.

But what exactly is a home directory? First, let's look at how directories are structured

[ put image here, or draw on board, or pull up ]

Your **root directory** is going to start either with just a slash (i.e. `/Users/morgan/`) or with a C (i.e. `C:\Users\morgan`).

We use slashes to indicate sub-folders, or folders within a folder. If a file is in `/Users/morgan/Documents/file.txt`, that means there is a folder called `Documents` inside my home directory, and inside `Documents` is a file called `file.txt`.

# How can we look at what's in our directory?
But maybe we're getting ahead of ourselves. Let's first learn how to use the command line to look in our current directory.

Type: `ls -F /`

What do you see? Can you guess what some of this means?

# Creating Bash commands
So the command we typed above displayed all the folders and files in our root directory. But why? Let's talk more about our first commands.

## Dissecting the above command
`ls` is the command we ran. It's short for "list structures". When you enter this keyword, it commands the computer to show you all of the items in your current directory.

`-F` is an **option** (also called switches or flags). When you type `ls` on its own, it looks different. What `-F` does is it appends a `/` to all directory names.

`/` is called an **argument**. In our command above, this was used to determine what directory we wanted to look at the contents of. Because we used `/` as our argument, this looked at our root directory. 

## Terminology and error messages
The difference between options and arguments? Options are determined by the computer (or the person who wrote the script, but we'll get into that later) and can only take on certain values. If we type `ls -x`, we get an error.

But arguments can be tailored to whatever you are working on. Let's say we want to look at our home directory instead. We could type `ls -F /Users/morgan`. 

## Some thing you may have noticed
First, you may have noticed that we need to put spaces between commands, options, and arguments. `ls-F` does not work. 

However, we can also have too many spaces. `ls - F` also does not work.

The command line isn't Google—it can't correct our mistakes. Typing `ks` will not work, because `ks` isn't a command that the command line knows how to execute.

And finally, case (whether things are upper or lower case) matters. `LS -F /` will not run. `ls -f /` will give us a different result.

Fortunately, when we make these mistakes, we will get an error message to help us out! Making mistakes that seem simple or stupid are incredibly common. 

# Learning more
So how do we know what the options for a command are? There are too many commands, each with their own options, some which you will never use, so memorizing all the options would be a waste of time.

We can type `ls --help` or `man ls` to see the options. Depending on your computer, only one of these might work. We will take a look at both so that you know how they work.

`ls --help` looks like X.

`man ls` looks like Y.

If there are certain options you use a lot, you may start to remember those. But if you ever forget, or if you need to do something new, typing `ls --help` or `man ls` will help you out!

If you ever forget about `help` or `man`, you can also go online for help. You probably already knew that. 
