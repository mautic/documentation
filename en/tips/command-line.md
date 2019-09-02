# Mautic Command Line Interface (CLI) commands

Sometimes you may need to use the command line with Mautic.  Here follows a list of the CLI commands that can be used.
 
You can find this list (and others - for example commands relating to Doctrine and other vendors) by typing 

`app/console`
`
at the command line in your Mautic directory.

Usage:
  command [options] [arguments]

Options:
  -h, --help               Display this help message
  -q, --quiet              Do not output any message
  -V, --version            Display this application version
      --ansi               Force ANSI output
      --no-ansi            Disable ANSI output
  -n, --no-interaction     Do not ask any interactive question
  -s, --shell              Launch the shell.
      --process-isolation  Launch commands from shell as a separate process.
  -e, --env=ENV            The Environment name. [default: "prod"]
      --no-debug           Switches off debug mode.
  -v|vv|vvv, --verbose     Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug

## Mautic commands

These are the commands you may need to use in relation to your Mautic instance.  They should be preceded by app/console.

| Command  | Description  |
|---|---|
| mautic:assets:generate  |  Combines and minifies asset files from each bundle into single production files |
| mautic:broadcasts:send  | Process contacts pending to receive a channel broadcast.  |
| mautic:campaigns:execute  | Execute specific scheduled events.  |
| mautic:campaigns:messagequeue  | Process sending of messages queue.  |
| mautic:campaigns:messages   | Process sending of messages queue.  |
| mautic:campaigns:rebuild   | Rebuild campaigns based on contact segments.  |
| mautic:campaigns:trigger  | Trigger timed events for published campaigns.  |
| mautic:campaigns:update  | Rebuild campaigns based on contact segments.  |
| mautic:campaigns:validate  | Validate if a contact has been inactive for a decision and execute events if so.  |
| mautic:citrix:sync  | Synchronizes registrant information from Citrix products  |
| mautic:contacts:deduplicate  | Merge contacts based on same unique identifiers  |
| mautic:email:fetch  | Fetch and process monitored email.  |
| mautic:emails:send   | Processes SwiftMail's mail queue  |
| mautic:import  | Imports data to Mautic  |
| mautic:install:data   | Installs Mautic with sample data  |
| mautic:integration:fetchleads  | Fetch leads from integration.  |
| mautic:integration:pipedrive:fetch  | Pulls the data from Pipedrive and sends it to Mautic  |
| mautic:integration:pipedrive:push  | Pushes the data from Mautic to Pipedrive  |
| mautic:integration:pushactivity  | Push lead activity to integration.  |
| mautic:integration:pushleadactivity  | Push lead activity to integration.  |
| mautic:integration:synccontacts  | Fetch leads from integration.  |
| mautic:iplookup:download  | Fetch remote datastores for IP lookup services that leverage local lookups  |
| mautic:maintenance:cleanup  | Updates the Mautic application  |
| mautic:messages:send  | Process sending of messages queue.  |
| mautic:migrations:generate  | Generate a blank migration class.  |
| mautic:plugins:install  | Installs, updates, enable and/or disable plugins.  |
| mautic:plugins:reload  | Installs, updates, enable and/or disable plugins.   |
| mautic:plugins:update  | Installs, updates, enable and/or disable plugins.  |
| mautic:queue:process   | Process queues  |
| mautic:reports:scheduler  | Processes scheduler for report's export  |
| mautic:segments:check-builders  | Compare output of query builders for given segments  |
| mautic:segments:rebuild  | Update contacts in smart segments based on new contact data.  |
| mautic:segments:update   | Update contacts in smart segments based on new contact data.  |
| mautic:social:monitoring  | Looks at the records of monitors and iterates through them.   |
| mautic:theme:json-config   | Converts theme config to JSON from PHP  |
| mautic:unusedip:delete   | Deletes IP addresses that are not used in any other database table  |
| mautic:update:apply  | Updates the Mautic application  |
| mautic:update:find  | Fetches updates for Mautic  |
| mautic:webhooks:process  | Process queued webhook payloads  |
| social:monitor:twitter:hashtags  | Looks at our monitoring records and finds hashtags  |
| social:monitor:twitter:mentions  | Searches for mentioned tweets   |
