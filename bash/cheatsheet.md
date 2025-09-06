## Creating, navigating, and interacting with directories

Make a new directory (mkdir)

```
$ mkdir new_directory
```

Delete an existing directory (rmdir)

```
$ rmdir -p /existing/directory/areYouSureYouWantToDeleteMe
```

Move a directory into a new directory (mv)

```
$ mv source_directory destination_directory
```

List all of the files in a directory (ls)

```
$ ls
$ ls -l # includes types and permissions
```

Print the path of the current directory (pwd)

```
$ pwd
```

Change the directory that you are in (cd)

```
$ cd /path/to/new/directory
$ cd .. # changes into the directory above
```

## Creating, navigating, and interacting with files

Remove a file (rm)

```
$ rm useless.txt
$ rm -r /directory/all_useless_files.txt
```

Copy a file (cp)

```
$ cp og.txt new.txt
```
Create a new file or files (touch)

```
$ touch fake.txt
$ touch fake1.txt fake2.txt
```

Display the contents of a file
```
$ cat fake.txt
```
Find files
```
$ find -name "fake" # finds all files across directories that contain fake
$ find -iname "fake" # finds all files (ignoring case) across directories that contain "fake"
$ find -not -name "fake" # finds every file that does not contain "fake.txt"
```
## Working with files
Cut lines and write results to stdout (cut)
```
$ cut -c 1-7 fake.txt # prints first seven characters of each line from the file
```
Cut section based on a delimiter (cut)
```
$ echo "the cat won't stop meowing" | cut -d ' ' -f 2,4,5
cat stop meowing
```
Head is used to print the "top" or first lines (default is 10; head)
```
$ head -n 7 fake.txt # -n is print by line
$ head -c 3 numbers.txt # -c is print by bytes
```
Tail is used to print the last specified numbers of lines (tail)
```
$ tail -n 7 fake.txt
$ tail -c 3 numbers.txt
```
Count lines, word, and bytes (wc)
```
$ wc fake.txt # counts number of lines, words, and bytes
$ wc -w fake.txt # counts number of words
```
Search and replace (sed)
```
$ sed s/cat/felines/ carnivores.txt # replaces all occurrences of cat with feline in the specified text file
$ sed 's/^$/d' fake.txt # delete a line with a certain pattern (in this case, an empty line)
```
Search for patterns in a file (grep)
```
$ grep cat carnivores.txt # searches for and prints any matches of the pattern (e.g. cat)
$ grep -w cat carnivores.txt # searches for & prints exact matches of the pattern
$ grep -B 2 cat carnivores.txt # prints the number of lines (2) before (-B) the match and after (-A) the match
$ grep -v cat carnivores.txt # searches for and prints everything but the pattern
$ grep 'Mountain lion\|Domestic cat' carnivores.txt # searches for and prints multiple patterns
```
Substitute characters (tr)
```
$ cat fake.txt | tr 'a-z' 'A-Z' # capitalizes all lowercase letters
$ cat fake.txt | tr -d 'w' # delete all w's
```
Arrange file (sort)
```
$ sort fake.txt # sort the file alphabetically
$ sort -r fake.txt # sort in reverse order
```
Remove duplicate lines (uniq)
```
$ uniq fake.txt
$ uniq -c fake.txt # counts number of times a line was replaced
```
Display a text or string (echo)
```
$ echo "Hello World!"
Hello World!
$ echo -e "Hello World" # displays with tab spaces
Hello   World!
```
AWK (powerful processing tool + programming language embedded into command line)
```
$ awk '{print $2,$4,$5}' fake.txt # extracts fields 2, 4, and 5 from the file
$ awk'$7 !~ /ˆ[a-f]/' fake.txt # print each line whose 7th field does not match the regular expression
```

## Helpful reminders & things to keep in mind

-   Files have information. Directories have files. Directories can also have directories.

-   A relative path specifies a location starting from the current location.

-   An absolute path specifies a location from the root of the file.

-   `...` means the directory above the current one. `.` means the current directory.

-   `*` matches zero or more characters in a file name, so `\*`.txt matches all files ending in .txt.

-   `?` matches any single character in a file name, so ?.txt matches a.txt but not any.txt.

-   The shell does not have a trash bin. Once something is deleted, it's **gone**. Be careful!!! 
