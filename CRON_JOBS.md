# CRON Jobs
[Cronjob.guru](https://crontab.guru)


- See List of current user's cron jobs in a CRON Table

```
crontab -l

```

- Edit list of cron jobs (brings up default editor)
```
crontab -e
```

- Basic syntax layout:
  - minute hour day month day-of-week command

- Run a basic echo (print) command to a file every minute of every day of every month

```
* * * * * echo 'Hello' >> /tmp/test.txt
```

- Note, the asterisk  c6an match any value, but you can also put exact value


- Run every Sunday at midnight

```
0 0 * * 1 echo 'Hello' >> /tmp/test.txt
```




- Run every 1st and 15th of every month at midnight

```
0 0 1,15 * * echo 'Hello' >> /tmp/test.txt

```


- Run every 10 minutes every day

```
*/10 * * * * echo 'Hello' >> /tmp/test.txt

```


- Run at midnight every 2 days

```
0 0 */3 * * echo 'Hello' >> /tmp/test.txt
```

- Run every day at midnight, but only through May to August
```
0 0 * 5-8 * echo 'Hello' >> /tmp/test.txt
```

- Run every 30 minutes Mon-Fri just from 9am-5pm
```
*/30 9-17 * * 1-5 echo 'Run during business hours' >> /tmp/test.txt

```

- Make a cron job silent with `-q` or `-qq`
```
0 0 * * * echo -q 'I run quietly' >> /tmp/test.txt
```



- Editing other user's crontabs (if you're a sysadmin)
```
crontab u user2 -e
```

- Editing a crontab that needs to be run as a sudo command
```
sudo crontab -e
```

- Clearing ALL cron jobs from crontab
```
crontab -r
```

- *Note, it's a good practice to add comments*

## Visual breakdown of cron jobs from Corey Shafer
(Corey's Github)[https://github.com/CoreyMSchafer/code_snippets/blob/master/Cron-Tasks/snippets.txt]

```
# ┌───────────── minute (0 - 59)
# │ ┌───────────── hour (0 - 23)
# │ │ ┌───────────── day of month (1 - 31)
# │ │ │ ┌───────────── month (1 - 12)
# │ │ │ │ ┌───────────── day of week (0 - 6) (Sunday to Saturday;
# │ │ │ │ │                                       7 is also Sunday on some systems)
# │ │ │ │ │
# │ │ │ │ │
# * * * * *  command_to_execute



###### Sample crontab ######

# Empty temp folder every Friday at 5pm
0 5 * * 5 rm -rf /tmp/*

# Backup images to Google Drive every night at midnight
0 0 * * * rsync -a ~/Pictures/ ~/Google\ Drive/Pictures/


```
