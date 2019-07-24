# Terminal Basics for navigation and file/directory manipulation

- Want to look up a command? Check the manual
```
man COMMAND
```

- Print Working Directory
```
pwd
```

- Change Directory
```
cd
```

- List everything in a directory (current directory if second parameter is blank)
```
ls
```

- Long form, can be added to commands
```
ls -l
```

- Listing hidden files (can be combined with `-l`)
```
ls -a
```

- Relative Path
  - `.` is current directory, `..` is one directory above, so command this is moving up one directory.
  ```
  ../
  ```
  - This can be chained to move up multiple directories. This moves up two directories
  ```
  ../..
  ```

- Make new Directory

```
mkdir
```

- Make new file (specify extension type)

```
touch NEW_FILE_NAME.ext
```

- Copy File
```
cp NEW_FILE_NAME.txt COPY_OF_FILE.txt
```


- Copy an entire directory
```
cp -R ORIGINAL_DIR/ COPIED_DIR/
```


- Secure Copy File (you can also specify the path for the copy)
```
scp NEW_FILE_NAME.txt SECURE_COPY_OF_FILE.txt
```

  - *Note, moving and renaming a file is the same command, so keep that in mind when renaming or moving a file, you can do both in one swoop if so desired*
- Change file or directory name (you can also move the file/directory during this)

```
mv ORIGINAL_FILE_AME.txt NEW_FILE_NAME.txt
```

- Move a file or directory

```
mv FILE_NEEDED_TO_MOVE.txt path/to/where/FILE_NEEDED_TO_MOVE.txt
```
  - This can also be done without specifying the file name (jsut specifying the path)
  ```
  mv FILE_NEEDED_TO_MOVE.txt path/to/where/
  ```
  - You also can rename the file during this processes
  ```
  mv FILE_NEEDED_TO_MOVE.txt path/to/where/FILE_RENAMED.txt
  ```

- Remove (delete) a file (be careful)

```
rm FILE_NEEDING_DELETION.csv
```

- To delete a directory use the `-r` since dealing with a directory and `-f` to force it
```
rm -rf DIRECTORY_NEEDING_DELETION
```


- Perform command on something with execute command (see the find command for more verbose examples)

```
-exec
```
