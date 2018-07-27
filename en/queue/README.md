# Queue

Improved scalability can be achieved by activating the queuing mechanism for email and page opens.  Use this if you
are getting too much traffic at once from people opening pages or opening emails.

## Activating

You can activate and configure the queuing mechanism by going to configuration:

- Open the admin menu by clicking the cog icon in the top right corner.
- Select the *Configuration* menu item.
- Select the *Queue Settings* tab.
- Switch the *Queue Protocol* to either *RabbitMQ* or *Beanstalkd*.
- Save the configuration.

### RabbitMQ

[RabbitMQ](https://www.rabbitmq.com/features.html) is one of the available queue protocols that Mautic supports.
In order to use it, you must have a RabbitMQ server running.  Instructions on how to install RabbitMQ can be obtained
on their [website](http://www.rabbitmq.com/download.html).  For testing purposes, you can use
you can use [cloudamqp](https://www.cloudamqp.com/) which offers a RabbitMQ as a service.

Once you have setup a RabbitMQ server, you can configure Mautic to use it by using the *Configuration* menu item again.

- Open the admin menu by clicking the cog icon in the top right corner.
- Select the *Configuration* menu item.
- Select the *Queue Settings* tab.
- Switch the *Queue Protocol* to *RabbitMQ*.
- Change the *Host* to the hostname of your RabbitMQ installation.
- Change the *Virtual Host* to the virtual host of your RabbitMQ installation.
- Change the *User* to the username of your RabbitMQ installation.
- Change the *Password* to the password of your RabbitMQ installation.
- Save the configuration.

### Beanstalkd

[Beanstalkd](https://kr.github.io/beanstalkd/) is another available queue protocol that Mautic supports.
In order to use it, you must have a Beanstalkd server running.  Instructions on how to install Beanstalkd can be
obtained on their [website](https://kr.github.io/beanstalkd/download.html).

Once you have setup a Beanstalkd server, you can configure mautic to use it by using the *Configuration* menu item again.

- Open the admin menu by clicking the cog icon in the top right corner.
- Select the *Configuration* menu item.
- Select the *Queue Settings* tab.
- Switch the *Queue Protocol* to *Beanstalkd*.
- Change the *Host* to the hostname of your Beanstalkd installation.
- Save the configuration.

## Processing

Once the queuing mechanism is activated, any page hits and email opens will be queued up to be processed later.
To process them, you will need to run some console commands on a regular basis.

Processing page hits is done by using the following command:

```
php /path/to/mautic/app/console mautic:queue:process --env=prod -i page_hit
```

Processing page hits is done by using the following command:

```
php /path/to/mautic/app/console mautic:queue:process --env=prod -i email_hit
```

When these commands are run, they will continue to run until you stop the program by using the keyboard
combination `Control + C`.  If you want to run them to process only, say, 50 page hits or email hits, you can
run the command like this instead:

```
php /path/to/mautic/app/console mautic:queue:process --env=prod -i page_hit -m 50
```

or

```
php /path/to/mautic/app/console mautic:queue:process --env=prod -i email_hit -m 50
```
