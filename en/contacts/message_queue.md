## Message Queues

When a campaign _**marketing**_ email is triggered or an email broadcast (segment email) and either a contact has a frequency rule defined or there is a default set in Configuration, the email may be sent to a queue to be processed.

### Priority and number of attempts

![](media/marketing-email.png)

- You can select priority as High or Normal. All messages with priority high will be put in the front of the queue when processing messages for a given date. Broadcasts are always injected as normal priority.
- Number of attempts will try to send email again if it has been rescheduled, note that even if an email is pending but if the number of attempts has been reached, the message will not be sent.

### Processing a message queue
Messages are put into the queue with status pending, so all pending messages that have not met their max number of attempts will be processed using this command.

Setup your cron as followed:

`php app/console mautic:messages:send`