# Homework Part II

# 1# Declaring variables for next time turn on the terminal
`declare -r MY_VAR=1`

# 2# How to Create, Delete the Folder and list with CMD/Powershell

## cd (change directory usage from Windows)

```powershell
cd .. #go to the parent folder
cd / #go to the C:\ Directory
cd "DevOps Training” #go to the folder DevOps Training (must be under the same folder)
cd ~ #go to the home directory
```

## dir (list directory usage from Windows)

```powershell
dir /d: #List all directories in the current path
dir /r: #Show read-only files
dir /h: #Show hidden files
dir /a: #Archive files
dir /s: #List system files
dir /i: #Not content indexed files
dir /l: #Reparse points
dir /-: #Add a minus in front of any of the file attribute to let the DIR command not show that kind of file.
```

## tree (show the tree of the files from the beginning of the parent Folder)

```powershell
tree <drive>: #Specifies the drive that contains the disk for which you want to display the directory structure.
tree <path>: #Specifies the directory for which you want to display the directory structure.
tree /f: #Displays the names of the files in each directory.
tree /a: #Specifies to use text characters instead of graphic characters to show the lines that link subdirectories.
tree /?: #Displays help at the command prompt.
```

## mkdir (Create Folder)

```powershell
mkdir <drive>: #Specifies the drive on which you want to create the new directory.
mkdir <path>: #Specifies the name and location of the new directory.
mkdir /? #Displays help at the command prompt.
```

## rmdir (remove the folder)

```powershell
rmdir [<drive>:]<path>: #Specifies the location and the name of the directory that you want to delete. Path is required. If you include a backslash () at the beginning of the specified path, then the path starts at the root directory (regardless of the current directory).
rmdir /s: #Deletes a directory tree (the specified directory and all its subdirectories, including all files).
rmdir /q: #Specifies quiet mode. Does not prompt for confirmation when deleting a directory tree. The /q parameter works only if /s is also specified.
#CAUTION: When you run in quiet mode, the entire directory tree is deleted without confirmation. Make sure that important files are moved or backed up before using the /q command-line option.
rmdir /?: #Displays help at the command prompt.
```

## del (delete the file)

```powershell
del <names>: #Specifies a list of one or more files or directories. Wildcards may be used to delete multiple files. If a directory is specified, all files within the directory will be deleted.
del /p: #Prompts for confirmation before deleting the specified file.
del /f: #Forces deletion of read-only files.
del /s: #Deletes specified files from the current directory and all subdirectories. Displays the names of the files as they are being deleted.
del /q: #Specifies quiet mode. You are not prompted for delete confirmation.
del /a[:]<attributes>: #Deletes files based on the attributes.
del /?: #Displays help at the command prompt.
```

## copy (Copy the files)

```powershell
copy /d: #Allows the encrypted files being copied to be saved as decrypted files at the destination.
copy /v: #Verifies that new files are written correctly.
copy /n: #Uses a short file name, if available, when copying a file with a name longer than eight characters, or with a file name extension longer than three characters.
copy /y: #Suppresses prompting to confirm that you want to overwrite an existing destination file.
copy /-y: #Prompts you to confirm that you want to overwrite an existing destination file.
copy /?: #Displays help at the command prompt.
```

## Move-Item (Move the files and folders)

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
Move-Item -Path C:\Temp -Destination C:\Logs
Move-Item -Path .\*.txt -Destination C:\Logs
```

# 3# grep, sed, awk and wget usage

## Grep (Grep is a good tool to use when you need to search for a text pattern in a file. For example, you may need to search for specific text in a system log file.)

```bash
grep -B num: #displays the lines before the search term match. Replace num with the number of lines to display.
grep -A num: #displays the lines after the search term match. Replace num with the number of lines to display
grep -C num: #displays the lines before and after the search term match. Replace num with the number of lines to display. The default value for num is 2.
grep -B 4 "fonts" /var/log/apache2/access.log #display before four lines
grep -l -i copyright *.html #display the lines that include the word "copyright" in all .HTML files
grep -L -i copyright *.html #display the lines that don't include the word copyright in all .HTML files.
```

## sed ( sed is to search for strings or patterns throughout a file and replace them with different strings.)

```bash
sed -e's/Copyright 2020/Copyright 2021/g' index.html > modified.html #changing the Copyright 2020 to Copyright 2021 from index.html file to modified.html
sed '4 i #This is the extra line' sedtest.txt #add an extra line in line number 4 but not saved in the file.
cat input.txt | sed 's/hello/world/' - > output.txt #display the input.txt file and change the word hello to world
sed -n '45p' file.txt #display the output of line number 45
sed -n  '1p ; $p' one.txt two.txt three.txt #display 1st line from the first and last file.
sed -e '/^foo/d' -e 's/hello/world/' input.txt > output.txt #delete the first line and change the word hello to world and save the file in output.txt
```

## awk ( awk is a full-featured programming language with functions, variables, flow control, and support for different data types.)

```bash
#example usage of awk
#names.txt
#1 Vince       Lombardi    Toyota      Fordham     1913
#2 Betty       Ford        Chevrolet   Bennington  1918
#3 Harrison    Ford        Toyota      Ripon       1942
#4 Mike        Rowe        Ford        Towson      1962

awk '($3 == "Toyota") {print}' names.txt #display the lines that include Toyota stored in variable $3(vertical 3rd role is automatically saved in $3)
awk '($5 < 1945) {print $2}' names.txt #disply the lines of the $2 that are lower than 1945
awk '{total += $5} END {print total/NR}' names.txt #display the total of $5 divided by the number of roles.
```

## wget ( Download Single or Multiple Files)

```bash
wget https://wordpress.org/latest.zip #download the latest version of Wordpress
wget -O wordpress-install.zip https://wordpress.org/latest.zip #download the latest version of Wordpress and save with the name
wget -tries=100 https://wordpress.org/latest.zip #will try 100 times to download
wget -c https://example/very-big-file.zip #if the connection get interrupted, the file will resume when the connection is back.
```