# Global Regular Expression Print (GREP) Command

- Basic explanation is it allows search of text/whatever inside of files


`man grep`



- Search for text inside of a file in the current directory
```
grep "I'm looking for some text" FILE_IM_LOOKING_IN.txt

```

  - Real world example:

  ```
  grep "django" manage.py
  ```

  echoes out this:

  ```
          from django.core.management import execute_from_command_line
              import django
  ```
