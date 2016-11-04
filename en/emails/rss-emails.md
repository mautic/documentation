# RSS Emails

RSS emails feature allows you to send automatic and recurrent emails generated from a RSS or ATOM feed to a selected segment(s). A great way to nurture your contacts automatically with the content published on your blog!

### Create a RSS email

In the email creation page, you have now (introduced in 2.3) the ability to select a third type of email.
![](/emails/media/rss-email-type.png)

It will generate a new type of email in the email listing in your Mautic menu.
![](/emails/media/rss-email-new.png)

### RSS email configuration

To create your automatic email built from a RSS feed, you must set up the following points:

* The associated segment(s) - same as segment email type
* The RSS feed URL. It also supports ATOM feed
* The number of RSS items you want to display in the body of your email (see the configuration of items in the next paragraph)
* Beginning date of the automatic and recurrent RSS email
* Choose if you want the email to leave on a defined timeframe or a recurrent day(s) of the week.

![](/emails/media/rss-email-setting.png)

### Email Builder

The email builder will help you to build your RSS feed structure. The use of tokens is massively needed to replicate RSS feed name, RSS feed link, item RSS feed name, item RSS feed date, item RSS feed image, etc.
You must keep in mind that we introduce 3 types of tokens:
1. `feedfield`: they concern the feed itself.
2. `looper`: it will help to loop (replicate) the design and content of the feed item to have as much as you set into your email setting.
3. `itemfield`: they are the content itself of the RSS feed, like a blog post. Those one must be duplicated (included in the loop fields) if you want to have 5 blog articles into your email for instance.

#### General tokens
Those tokens concern the feed itself. They can introduce the email for instance.
* `{feedfield=title}` - Feed Title
* `{feedfield=description}` - Feed Description
* `{feedfield=link}` - Feed Link
* `{feedfield=date}` - Feed Date
* `{feedfield=id}` - Feed Public ID
* `{feedfield=date}` - Feed Date

#### Item tokens (to be looped)
Those tokens concern the content of the feed. They will be automatically duplicated depending on the number of RSS items you have set and where you'll place the loppers.
* `{itemfield=title}` - Item Title
* `{itemfield=description}` - Item Description
* `{itemfield=author}` - Item Author
* `{itemfield=summary}` - Item Summary
* `{itemfield=link}` - Item Link
* `{itemfield=date}` - Item Date

#### Looping process
* `{feed=loopstart}` - to be placed on top of the content you want to duplicate. It'll start duplicate content, tokens and design.
* `{feed=loopend}` - to be placed at the end of the content you want to loop.

![](/emails/media/rss-email-builder-tokens.png)

### Email send and preview
The email will start to be generated automatically on the date set.
It'll include the amount of RSS items you have set.

**If the published content in the RSS feed are not a sufficient amount since last email sent to include the amount of RSS items you have set, it'll automatically stop the loop to the last content sent.**

![](/emails/media/rss-email-preview.png)
