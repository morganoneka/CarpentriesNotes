# Activities
## Starting out with grep

Which command would result in the following output?:

```
and the presence of absence:
```

1. `grep "of" haiku.txt`
1. `grep -E "of" haiku.txt`
1. `grep -w "of" haiku.txt`
1. `grep -i "of" haiku.txt`

<details>
<summary>Answer</summary>

The correct answer is 3, because the -w option looks only for whole-word matches. The other options will also match ‘of’ when part of another word.
</details>

## Combining grep with other commands

`grep` can also be useful when used with other commands. For example, suppose you want to run `grep` on the output of `history` in order to see all the commands you ran that used `thesis.txt`. How would you write this script?

<details>
<summary>Answer</summary>

`history | grep "thesis.txt"`
</details>
