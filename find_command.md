# Find Command

`man find`


- Find all files in current directory
```
find .
```

- Find all files and directories in specific directory
```
find /path/to/FOLDERYOUWANT_TO_FIND
```


## Search by Type

- Find all directories `d`
```
find . -type d
```

- Find all files `f`
```
find . -type f
```

## Search by Name

- Find file when knowing exact file name
```
find . -type f -name "i_KNOW_FILE_NAME_AND_EXT.txt"
```

- Find file when only knowing the first few letters with REGEX *widlcard* `*`
  - Note, this way is case sensitive

```
find . -type f -name "I_dont_know_na*"
```

- Find file when only knowing the first few letters with REGEX *widlcard* `*` and an case-insensitive use of -name with `-iname`  

```
find . -type f -iname "i_DONT_kNoW_nA*"
```

- Creative use of REGEX wild card, returning all Python files

```
find . -type f -name "*.py"
```

## Search by Time


### By Minutes

- Find files that have been modified less than 10 minutes ago

```
find . -type f -mmin -10
```


- Find files that have been modified more than 10 minutes ago

```
find . -type f -mmin +10
```

- Combining the time restraints to be more than 1 minute ago but less than an hour and half ago
```
find . -type f -mmin +1 -mmin -90
```

### By Days

- Find files that have been modified less than 10 days ago

```
find . -type f -mtime -10
```


- Find files that have been modified more than 10 days ago

```
find . -type f -mtime +10
```

- Combining the time restraints to be more than 1 day ago but less than three months ago
```
find . -type f -mtime +1 -mtime -90
```

### Other time constraints

- For access minutes and access days
```
amin atime
```

- For change minutes and change days
```
cmin ctime
```

## By Size

- Finding all files over 5 megabytes
```
find . -size +5M
```

- Finding all files under 5 megabytes
```
find . -size -5M
```

- Finding all file between 5 and 10 megabytes
```
find . -size +5M -size -10M
```

  - Also have ability to search by by kilobytes `k` and gigabytes `G `

## By empty files
- Find all empty files
```
find . -empty
```

## Find by permissions
- Find all files with permissions of 777 (ower super, user super, guest super)
```
find . -perm 777
```

## Find files only 'x' sub-directories deep
- Find all files in only the first two directories (nothing deeper)

```
find . -type f -maxdepth 2
```

### Examples of how to use `find` for real world situation

- Changing all of the permissions for the selected folder so that the specified user `user_name` has `chown` (change owner) permissions to `www-data`. The `{}` is a placeholder since this being executed (`-exec`) in the find command. The `+` or the `\;` are the same thing, just ending the command's line.

```
find path/FOLDER_NAME -exec chown user_name:www-data {} +
```
-OR-

```
find path/FOLDER_NAME -exec chown user_name:www-data {} \;
```

- Changing all of the sub-directory's permissions to 775 with `chmod` (change permissions)

```
find DIRECTORY_NAME -type d -exec chmod 775 {} +
```

  - Double checking that worked:
  ```
  find DIRECTORY_NAME -perm 775
  ```

- Changing all of the files in the main directory (and all sub-directories) to 664 permissions

```
find DIRECTORY_NAME -type f -exec chmod 664 +
```


- Delete all files that have a .png extension and only the first two sub directories

  - First run the find command, to make sure you are doing what you think you are doing.

  ```
  find . -type f -name "*.png " -maxdepth 2
  ```

  - If what you see echoed to you is correct, then you can add an `-exec` command to the find command and it'll run that

  ```
  find . -type f -name "*.png " -maxdepth 2 -exec rm {} +
  ```
