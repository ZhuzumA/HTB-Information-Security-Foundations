# Learning Dependecies

## 21st, 25th, 26th November 2024
I learned about **Linux**, **Windows OS**, and **Virtual Private Server**. How to install them and make basic configurations. 


### Key Takeaways
- **Linux Navigation**: At first was a personal project started in 1991 by a finnish student Linus Torvalds.
- **Working with files and directories**: Available in over 600 distributions.
- **Editing Files**:
- **Find Files and Directories**:
- **File Descriptions and Redirections**:
- **Filter Contents**:
- **Regular Expressions**:
- **Permission Managment**:

### Reflections
## Linux Navigation
Main commands to navigate in Linux:
- <span style="color:lightgreen"> *pwd*</span> - where am I;
- <span style="color:lightgreen"> *ls*</span> - to list all the contents inside a directory;
to display more information about directories and file I can use an option:
- <span style="color:lightgreen"> *ls -l*</span> - First, we see the total amount of blocks (1024-byte - 1 block) used by the files and directories listed in the current directory, also we see type and permissions, number of hard links to the file/directory, owner, group owner, size or number of blocks, date and time, and finally directory name.
- <span style="color:lightgreen"> *ls -la*</span> - to list all files of a directory, including hidden files that start with a dot at the beginning of its name. 
- <span style="color:lightgreen"> *cd*</span> - we can navigate to the directory and specify the path by adding the path to the specific directory, for instance: cd /dev/shm;
- <span style="color:lightgreen"> *cd -*</span> - to get back to the home directory;
- <span style="color:lightgreen"> *cd /dev/s [TAB x2]*</span> - if I type cd /dev/s and press *TAB* twice it will return all entries with the letter *s* in the directory of /dev/;
- <span style="color:lightgreen"> *cd ..*</span> - to jump to the parent directory, 1 level up in the directory hierarchy;
- <span style="color:lightgreen"> *touch*</span> - to create a file;
- <span style="color:lightgreen"> *mkdir*</span> - to create a directory;
- <span style="color:lightgreen"> *mkdir -p*</span> - to create parent directories;
- <span style="color:lightgreen"> *tree*</span> - to see the whole structure of directories;
- <span style="color:lightgreen"> *touch ./users/tom/readme.txt*</span> - create readme.txt inside tom dir, fram home directory;
- <span style="color:lightgreen"> *mv*</span> - move or rename files and dirs;
- <span style="color:lightgreen"> *rm*</span> - remove files;
- <span style="color:lightgreen"> *rm -r*</span> - remove not empty directory;
- <span style="color:lightgreen"> *rmdir*</span> - remove directory;
- <span style="color:lightgreen"> *nano*</span> file.txt - create text file in Nano editor;
- <span style="color:lightgreen"> *cat*</span> file.txt - to view the contents of the file;  
- <span style="color:lightgreen"> *which*</span> - to return the path to the file or link that should be executed;
- <span style="color:lightgreen"> *find*</span> - to find files and folders, I can use options to define search by parameters: 

![An example with multiple options](resources/find.png)
 
And here is an explonation of parameters:

![An detailed explanation of options](resources/find_parameters.png)


- <span style="color:lightgreen"> *locate*</span> - to return file or folders quicker through the system;
- <span style="color:lightgreen"> *find*</span> |wc -l - to count the total number of obtained results;  
- <span style="color:lightgreen"> *find*</span> 2> /dev/null - to redirect the resulting errors to the "null device", which discard all data;
- <span style="color:lightgreen"> *find*</span> 2> /dev/null > file.txt - to redirect standard result to file.txt without resulting errors;
- <span style="color:lightgreen"> *find*</span> 2> stderr.txt 1> stdout.txt - to direct STDOUT ot stdout file, and all resulting error files to STDERR;
- <span style="color:lightgreen"> *ls | grep*</span> ".txt" - in this case ls lists files, and its output is sent to `grep`, which filters for `.txt` files. 
- <span style="color:lightgreen"> *more*</span> displays file content one screen at a time
- <span style="color:lightgreen"> *less*</span> similar to more but allows backward navigation
- <span style="color:lightgreen"> *head*</span> return first 10 lines of the file
- <span style="color:lightgreen"> *tail*</span> return last 10 lines of the file
- <span style="color:lightgreen"> *sort*</span> alphabetically or numerically sort the content of the file to get a better overview
- <span style="color:lightgreen"> *grep -v*</span> search for lines not containing a specific pattern
- <span style="color:lightgreen"> *cut*</span> Extracts specific columns or fields from text
- <span style="color:lightgreen"> *tr*</span> translates or deletes characters
- <span style="color:lightgreen"> *column*</span> formats text into neatly aligned columns
- <span style="color:lightgreen"> *awk*</span> text processing tool for manipulating structured text
- <span style="color:lightgreen"> *sed*</span> stream editor for text manipulation
- <span style="color:lightgreen"> *wc*</span>  counts lines, words, and characters in a file

## Regular Expressions
A regular expression (regex) in Linux is like a powerful search tool. It’s a pattern of characters used to match, find, and manipulate text. Think of it as a way to describe what you’re looking for in a file or command output.

**Key Ideas**:
1. Match Characters: Use simple patterns to find specific text.
*Example*: `cat file.txt | grep "error"` - looks for the word "error" in a file.
2. Special Symbols:
- `.`: Matches any single character.
*Example*: `b.t` matches "bat", "bit", or "bot".
- `*`: Matches zero or more of the previous character.
*Example*: `ab*` matches "a", "ab", or "abb".
- `[]`: Matches any character inside the brackets.
*Example*: `[aeiou]` matches vowels.
- `^`: Matches the start of a line.
*Example*: `^Error` matches lines starting with "Error".
- `$`: Matches the end of a line.
*Example*: `log$` matches lines ending with "log".
3. Combine Patterns:
I can mix these symbols to build powerful search patterns.

**Grouping**
Among other things, regex offers us the possibility to group the desired search patterns. Basically, regex follows three different concepts, which are distinguished by the three different brackets:
Operators       Description
`(a)`           to group parts of a regex, Inside the brackets, I can define further patterns which should be processed together.
`[a-z]`         to define character classes. Inside the brackets, I can specify a list of characters to search for.
`{1,10}`        to define quantifiers. Inside the brackets, I can specify a number or a range that indicates how often a previous pattern should be repeated.
`|`             Also called the OR operator and shows results when one of the two expressions matches
`.*`            Also called the AND operator and displayed results only if both expressions match
To use these operators, you need to apply the extended regex using the `-E` option in grep.


**Permission Managment**
The whole permission system on Linux systems is based on the octal number system, and basically, there are three different types of permissions a file or directory can be assigned:
- `(r)` - Read;
- `(w)` - Write;
- `(x)` - Execute;
The permissions can be set for the *owner*, *group*, and *others* like presented in the next example with their corresponding permissions:

![Permission Managment](/Linux/resources/permission.png)

We can modify permissions using the `chmod` command, permission group references (`u` - owner, `g` - Group, `o` - others, `a` - All users), and either a [`+`] or a [`-`] to add remove the designated permissions. In the following example, let us assume we have a file called `shell` and we want to change permissions for it so this script is owned by that user, becomes not executable, and set with read/write permissions for all users.
Example to apply `read` permissions for all users and see the result:
`chmod a+r shell && ls -l shell`

To change the owner and/or the group assignments of a file or directory, we can use the `chown` command. The syntax is like following:
![Usinf chown command](/Linux/resources/permission-owner-change.png)

**Practical Excersices** 
1. Used this command to resolve the problem: 
`find / -type f -name *.conf -size +25k -size -28k -newermt 2020-03-03 2>/dev/null` 
2. How many total packages are installed on the target system?
`dpkg -l | grep -c '^ii'`
3. How many files exist on the system that have the ".log" file extension?
`find / -type f -name *.log 2> /dev/null |wc -l`
The file we will need to work with is the /etc/passwd file on our target and we can use any shown command above. Our goal is to filter and display only specific contents. Read the file and filter its contents in such a way that we see only:
4. A line with the username cry0l1t3.
`grep "cry0l1t3" /etc/passwd`
5.	The usernames.
`cat /etc/passwd | awk '{print $1}'`
6.	The username cry0l1t3 and his UID.
`grep "cry0l1t3" /etc/passwd | cut -d: -f1,3`
7.	The username cry0l1t3 and his UID separated by a comma (,)
`grep "cry0l1t3" /etc/passwd | cut -d: -f1,3 | tr ':' ','`
8.	The username cry0l1t3, his UID, and the set shell separated by a comma (,)
`awk -F: '/cry0l1t3/ {print $1 "," $3 "," $7}` /etc/passwd
9.	All usernames with their UID and set shells separated by a comma (,).
`awk -F: '{print $1 "," $3 "," $7}' /etc/passwd`
10.	All usernames with their UID and set shells separated by a comma (,) and exclude the ones that contain no logic or false.
`cat /etc/passwd | grep -v "false\|nologin" | awk -F: '{print $1 "," $7}'`
11.	All usernames with their UID and set shells separated by a comma (,) and exclude the ones that contain nologin and count all lines of the filtered output.
`cat /etc/passwd | grep -v "nologin" | awk -F: '{print $1 "," $7} | wc -l'`
12. How many services are listening on the target system on all interfaces? (Not on localhost and IPv4 only)
`ss -l -4 | grep -v "127\.0\.0" | grep "LISTEN" | wc -l`
13. Use cURL from your Pwnbox (not the target machine) to obtain the source code of the "https://www.inlanefreight.com" website and filter all unique paths of that domain. Submit the number of these paths as the answer.
`curl https://www.inlanefreight.com | tr " " “\n” | grep “www.inlanefreight.com” | tr “'” ‘"’ | cut -d’"’ -f2 | sort -u | wc -l`

Regular Expression excersices:
14. Show all lines that do not contain the `#` character in specific file:
`grep -E "#" /etc/ssh/sshd_config`
15. Search for all lines beginning with Password and containing yes.
`grep -E "(Password.*yes)" etc/ssh/sshd_config`