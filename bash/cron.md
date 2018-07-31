cron
=====

- a time-based job scheduler in Unix-like systems
- ppl  use cron to schedule jobs (commands, shell scripts)

how
----
- cron is driven by a crontab (cron table), a config file specifying the shell
  commands to run at specified times
- each line of a crontab file represents a job:

```
┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of month (1 - 31)
│ │ │ ┌───────────── month (1 - 12)
│ │ │ │ ┌───────────── day of week (0 - 6) (Sunday to Saturday;
│ │ │ │ │                                       7 is also Sunday on some systems)
│ │ │ │ │
│ │ │ │ │
* * * * *  command to execute
```
- * means 'first - last' (i.e. every)

e.g.
```
1 0 * * * printf > /var/log/apache/error_log
```
- clears the Apache error log at one minute past midnight (00:01) every day,

- ranges of numbers are allowed, separated by a hyphen (ranges are inclusive)
- lists are allowed, comma separated
- lists and ranges can be combined
- step values can be used with ranges, denoted by `/<number>`. e.g. `0-23/2` in
  the hours field means every other hour.
  
