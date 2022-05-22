# Cron

## Schema

<pre>
 .---------------- minute (0 - 59)

 | .-------------- hour (0 - 23)

 | | .------------ day of month (1 - 31)

 | | | .---------- month (1 - 12) OR jan,feb,mar ...

 | | | | .-------- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue ...

 | | | | |

 * * * * * command to be executed
</pre>

## Cron Expressions Allowed Fields and Values

Table A-1 Cron Expressions Allowed Fields and Values

| Name         | Required | Allowed Values     | Allowed Special Characters |
| ------------ | -------- | ------------------ | -------------------------- |
| Seconds      | Y        | 0-59               | , - \* /                   |
| Minutes      | Y        | 0-59               | , - \* /                   |
| Hours        | Y        | 0-23               | , - \* /                   |
| Day of month | Y        | 1-31               | , - \* ? / L W C           |
| Month        | Y        | 0-11 or JAN-DEC    | , - \* /                   |
| Day of week  | Y        | 1-7 or SUN-SAT     | , - \* ? / L C #           |
| Year         | N        | empty or 1970-2099 | , - \* /                   |

Special Characters:

\* any value

\, value list separator

\- range of values

\/ step values

## Examples

\* \* \* \* \* Run cron job every minute

\*/5 \* \* \* \* Run cron job every 5 minutes

\*/30 \* \* \* \* Run cron job every 30 minutes

0 \*/3 \* \* \* Run cron job every hour

0 \*/3 \* \* \* Run cron job every 3 hours

0 13 \* \* \* Run cron job every day at 1pm

30 2 \* \* \* Run cron job every day at 2.30am

0 0 \* \* \* Run cron job every day at midnight

0 0 \* \* 0 Run cron job every Sunday

0 0 \* \* 1 Run cron job every Monday

0 0 1 \* \* Run cron job every first day of every month

0 0 1 1 \* Run cron job every first of January every year
