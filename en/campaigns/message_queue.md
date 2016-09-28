# Campaign Marketing Message Queues

### Message Queues

When a campaign _**marketing**_ email is triggered the email is sent to a queue to be processed and rescheduled if the message was not sent due to a failure or if a frequency rule was met.

###Priority and number of attempts

- You can select priority as High or Normal. All messages with priority high will be put in front of the queue when processing messages for a given date.
- Number of attempts will try to send email again if it has been rescheduled, note that even if an email is pending but if the number of attempts has been reached, the message will not be sent.

### Processing a message queue
Messages are put into the queue with status pending, so all pending messages that have not met their max number of attempts will be processed using this command.

Setup your cron as followed:

`php app/console mautic:campaigns:messagequeue`