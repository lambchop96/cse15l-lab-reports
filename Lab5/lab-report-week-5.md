# Week 5 Lab Report - Commands

## `-name` Option

```
$ find technical/ -name chapter-13.3.txt
technical/911report/chapter-13.3.txt
```

`-name` recursively searches for files or folders of a specific name. Here, we found all files named "chapter-13.3.txt" for which there is only one, and now we know its specific location.

```
$ find technical/ -name biomed
technical/biomed
```

`-name` also works for folders. Since we did not include the ".txt" at the end, it found a folder named "biomed".

```
$ find technical/ -name chapter-1*.txt
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
```

Here, we found all text files that start with "chapter-1". Using patterns is useful to find all files or folders with a name that fits that certain pattern.

---

## `-type` Option

```
$ find technical/ -type d
technical/
technical/911report
technical/biomed
technical/government
technical/government/About_LSC
technical/government/Alcohol_Problems
technical/government/Env_Prot_Agen
technical/government/Gen_Account_Office
technical/government/Media
technical/government/Post_Rate_Comm
technical/plos
```

`-type d` recursively searches only for directories (hence, the 'd') within the given path. This is useful if we don't care about listing out all the files in a path as it may be quite long if there are many files within the various folders of a directory.

```
$ find technical/ -type f
technical/911report/chapter-1.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911report/chapter-12.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
etc.
```

Instead of searching for directories, `-type f` recursively searches only for files if you don't care about the folders in a directory.

```
$ find technical/ -type d -iname "g*"
technical/government
technical/government/Gen_Account_Office
```

Here, we combined the `-type` option with the `-iname` option so that we can recursively search for only directories that start with the letter 'g' regardless of case sensitivity.

---

## `-size` Option

```
$ find technical/ -size 50k
technical/biomed/1471-2156-3-17.txt
technical/biomed/1472-684X-1-5.txt
technical/biomed/gb-2001-2-8-research0030.txt
technical/biomed/gb-2002-3-5-research0025.txt
technical/government/Gen_Account_Office/Paper_Walker11-2002_acpro122.txt
```

`-size` helps find files and directories based on their size. Above, files that are 50kb are listed.

```
$ find technical/ -size +250k
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-3.txt
technical/government/Gen_Account_Office/d01591sp.txt
technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
```

Adding a plus sign before the byte count allows for searching for files that exceed a certain size. Here, we searched for files exceeding 250kb.

```
$ find technical/ -size +48k -size -50k
technical/biomed/1471-2148-1-8.txt
technical/biomed/1472-6807-2-3.txt
technical/biomed/gb-2001-2-12-research0055.txt
technical/biomed/gb-2002-3-12-research0085.txt
technical/biomed/gb-2002-3-7-research0035.txt
technical/biomed/gb-2002-4-1-r2.txt
```

We can also set a range of size to search for by using `-size` twice. This searched for files between 48kb and 50kb.
