# Variables

- [Contact fields](#contact-fields)
- [Company Contact fields](#company-contact-fields)
- [Mautic Component tokens](#mautic-component-tokens)
- [Email specific tokens](#email-specific-tokens)
- [Landing Page tokens](#landing-page-tokens)
  - [Preference Center Landing Page tokens](#preference-center-landing-page-tokens)
- [Dynamic Web Content tokens](#dynamic-web-content-tokens)
- [Contact Monitoring](#contact-monitoring)
- [Search filters](#search-filters)
- [Alphabetical list](#alphabetical-list)

> **ProTip**
>
> Default Value
>
> The default value can be specified after the `|` (pipe) character.  Consider this email salutation:
>
> `Hi {contactfield=firstname|there},`
>

## Contact fields

See [managing custom fields][custom fields] for more information.

| **VARIABLE NAME**                                  | **VARIABLE SYNTAX**                         |
| :------------------------------------------------- | :------------------------------------------ |
| Attribution                                        | `{contactfield=attribution}`                |
| Attribution Date                                   | `{contactfield=attribution_date}`           |
| Address Line 1                                     | `{contactfield=address1}`                   |
| Address Line 2                                     | `{contactfield=address2}`                   |
| Country                                            | `{contactfield=country}`                    |
| City                                               | `{contactfield=city}`                       |
| Company                                            | `{contactfield=company}`                    |
| Email                                              | `{contactfield=email}`                      |
| Facebook                                           | `{contactfield=facebook}`                   |
| Fax                                                | `{contactfield=fax}`                        |
| First Name                                         | `{contactfield=firstname}`                  |
| Foursquare                                         | `{contactfield=foursquare}`                 |
| Google+                                            | `{contactfield=googleplus}`                 |
| Instagram                                          | `{contactfield=instagram}`                  |
| IP Address                                         | `{contactfield=ipAddress}`                  |
| Last Name                                          | `{contactfield=lastname}`                   |
| LinkedIn                                           | `{contactfield=linkedin}`                   |
| Mobile Number                                      | `{contactfield=mobile}`                     |
| Phone Number                                       | `{contactfield=phone}`                      |
| Position                                           | `{contactfield=position}`                   |
| Skype                                              | `{contactfield=skype}`                      |
| State                                              | `{contactfield=state}`                      |
| Twitter                                            | `{contactfield=twitter}`                    |
| Title                                              | `{contactfield=title}`                      |
| Website                                            | `{contactfield=website}`                    |
| Zip Code                                           | `{contactfield=zipcode}`                    |

## Company Contact fields

See [Companies][companies] for more information.

| **VARIABLE NAME**                                  | **VARIABLE SYNTAX**                         |
| :------------------------------------------------- | :------------------------------------------ |
| Address Line 1 (Company)                           | `{contactfield=companyaddress1}`            |
| Address Line 2 (Company)                           | `{contactfield=companyaddress2}`            |
| Annual Revenue (Company)                           | `{contactfield=companyannual_revenue}`      |
| City (Company)                                     | `{contactfield=companycity}`                |
| Country (Company)                                  | `{contactfield=companycountry}`             |
| Description (Company)                              | `{contactfield=companydescription}`         |
| Email (Company)                                    | `{contactfield=companyemail}`               |
| Fax (Company)                                      | `{contactfield=companyfax}`                 |
| Industry (Company)                                 | `{contactfield=companyindustry}`            |
| Name (Company)                                     | `{contactfield=companyname}`                |
| Number of Employees (Company)                      | `{contactfield=companynumber_of_employees}` |
| Phone Number (Company)                             | `{contactfield=companyphone}`               |
| State (Company)                                    | `{contactfield=companystate}`               |
| Website (Company)                                  | `{contactfield=companywebsite}`             |
| Zip Code (Company)                                 | `{contactfield=companyzipcode}`             |

## Mautic Component tokens

See [Components][components] and [Manage Pages][manage pages] for more information.

| **VARIABLE NAME**                                  | **VARIABLE SYNTAX**                         |
| :------------------------------------------------- | :------------------------------------------ |
| Asset link for asset id#                           | `{assetlink=25}`                            |
| Focus Item id#                                     | `{focus=4}`                                 |
| Form id#                                           | `{form=83}`                                 |
| Landing Page link for page id#                     | `{pagelink=17}`                             |

## Email specific tokens

See [Manage Emails][manage emails] for more information.

| **VARIABLE NAME**                                  | **VARIABLE SYNTAX**                         |
| :------------------------------------------------- | :------------------------------------------ |
| Signature                                          | `{signature}`                               |
| Subject                                            | `{subject}`                                 |
| Tracking pixel                                     | `{tracking_pixel}`                          |
| Unsubscribe Text                                   | `{unsubscribe_text}`                        |
| Unsubscribe URL                                    | `{unsubscribe_url}`                         |
| Web View Text                                      | `{webview_text}`                            |
| Web View URL                                       | `{webview_url}`                             |

## Landing Page tokens

See [Manage Pages][manage pages] for more information.

| **VARIABLE NAME**                                  | **VARIABLE SYNTAX**                         |
| :------------------------------------------------- | :------------------------------------------ |
| Meta Description                                   | `{pagemetadescription}`                     |
| Title                                              | `{pagetitle}`                               |
| Language bar                                       | `{langbar}`                                 |
| Share Buttons                                      | `{sharebuttons}`                            |
| Success Message                                    | `{successmessage}`                          |

### Preference Center Landing Page tokens

See [customizing preference center][make pref center] for more information.

| **VARIABLE NAME**                                  | **VARIABLE SYNTAX**                         |
| :------------------------------------------------- | :------------------------------------------ |
| Lead Identifier                                    | `{leadidentifier}`                          |
| Category List                                      | `{categorylist}`                            |
| Segment List                                       | `{segmentlist}`                             |
| Preferred Channel                                  | `{preferredchannel}`                        |
| Channel Frequency                                  | `{channelfrequency}`                        |
| Save Preferences                                   | `{saveprefsbutton}`                         |
| Unsubscribe Text                                   | `{unsubscribe_text}`                        |
| Unsubscribe URL                                    | `{unsubscribe_url}`                         |

## Dynamic Web Content tokens

| **VARIABLE NAME**                                  | **VARIABLE SYNTAX**                         |
| :------------------------------------------------- | :------------------------------------------ |
| [Dynamic Content 1]<br>ie: user-defined variable name | `{dynamiccontent="Dynamic Content 1"}`   |

## Contact Monitoring

See [Contact Monitoring][contact monitoring] for more information.

| **VARIABLE NAME**                                  | **VARIABLE SYNTAX**                         |
| :------------------------------------------------- | :------------------------------------------ |
| Language                                           | `{language}`                                |
| ~~Title~~                                          | ~~`{title}`~~                               |
| Page Title                                         | `{page_title}`                              |
| ~~URL~~                                            | ~~`{url}`~~                                 |
| Page URL                                           | `{page_url}`                                |
| Referrer                                           | `{referrer}`                                |
| Tracking pixel                                     | `{tracking_pixel}`                          |
| UTM Campaign                                       | `{utm_campaign}`                            |
| UTM Content                                        | `{utm_content}`                             |
| UTM Medium                                         | `{utm_medium}`                              |
| UTM Source                                         | `{utm_source}`                              |
| UTM Term                                           | `{utm_term}`                                |

## Search filters

See the [Search][search] page for more information.

## Alphabetical list

| **VARIABLE NAME**                                  | **VARIABLE SYNTAX**                         |
| :------------------------------------------------- | :------------------------------------------ |
| Address Line 1                                     | `{contactfield=address1}`                   |
| Address Line 1 (Company)                           | `{contactfield=companyaddress1}`            |
| Address Line 2                                     | `{contactfield=address2}`                   |
| Address Line 2 (Company)                           | `{contactfield=companyaddress2}`            |
| Annual Revenue (Company)                           | `{contactfield=companyannual_revenue}`      |
| Asset link for asset id#                           | `{assetlink=25}`                            |
| Attribution                                        | `{contactfield=attribution}`                |
| Attribution Date                                   | `{contactfield=attribution_date}`           |
| Category List (Preference Center)                  | `{categorylist}`                            |
| Channel Frequency (Preference Center)              | `{channelfrequency}`                        |
| City                                               | `{contactfield=city}`                       |
| City (Company)                                     | `{contactfield=companycity}`                |
| Country                                            | `{contactfield=country}`                    |
| Country (Company)                                  | `{contactfield=companycountry}`             |
| Company                                            | `{contactfield=company}`                    |
| Description (Company)                              | `{contactfield=companydescription}`         |
| [Dynamic Content 1]<br>ie: user-defined variable name | `{dynamiccontent="Dynamic Content 1"}`   |
| Email                                              | `{contactfield=email}`                      |
| Email (Company)                                    | `{contactfield=companyemail}`               |
| Facebook                                           | `{contactfield=facebook}`                   |
| Fax                                                | `{contactfield=fax}`                        |
| Focus Item id#                                     | `{focus=4}`                                 |
| Form id#                                           | `{form=83}`                                 |
| Fax (Company)                                      | `{contactfield=companyfax}`                 |
| First Name                                         | `{contactfield=firstname}`                  |
| Foursquare                                         | `{contactfield=foursquare}`                 |
| Google+                                            | `{contactfield=googleplus}`                 |
| Instagram                                          | `{contactfield=instagram}`                  |
| Industry (Company)                                 | `{contactfield=companyindustry}`            |
| IP Address                                         | `{contactfield=ipAddress}`                  |
| Landing Page link for page id#                     | `{pagelink=17}`                             |
| Language bar                                       | `{langbar}`                                 |
| Last Name                                          | `{contactfield=lastname}`                   |
| Lead Identifier (Preference Center)                | `{leadidentifier}`                          |
| LinkedIn                                           | `{contactfield=linkedin}`                   |
| Meta Description (Landing Page)                    | `{pagemetadescription}`                     |
| Mobile Number                                      | `{contactfield=mobile}`                     |
| Name (Company)                                     | `{contactfield=companyname}`                |
| Number of Employees (Company)                      | `{contactfield=companynumber_of_employees}` |
| Phone Number                                       | `{contactfield=phone}`                      |
| Phone Number (Company)                             | `{contactfield=companyphone}`               |
| Position                                           | `{contactfield=position}`                   |
| Save Preferences (Preference Center)               | `{saveprefsbutton}`                         |
| Segment List (Preference Center)                   | `{segmentlist}`                             |
| Signature                                          | `{signature}`                               |
| Skype                                              | `{contactfield=skype}`                      |
| State                                              | `{contactfield=state}`                      |
| State (Company)                                    | `{contactfield=companystate}`               |
| Subject                                            | `{subject}`                                 |
| Twitter                                            | `{contactfield=twitter}`                    |
| Preferred Channel (Preference Center)              | `{preferredchannel}`                        |
| Share Buttons                                      | `{sharebuttons}`                            |
| Success Message                                    | `{successmessage}`                          |
| Title                                              | `{contactfield=title}`                      |
| Title (Landing Page)                               | `{pagetitle}`                               |
| Unsubscribe Text                                   | `{unsubscribe_text}`                        |
| Unsubscribe URL                                    | `{unsubscribe_url}`                         |
| Website                                            | `{contactfield=website}`                    |
| Website (Company)                                  | `{contactfield=companywebsite}`             |
| Web View Text                                      | `{webview_text}`                            |
| Web View URL                                       | `{webview_url}`                             |
| Zip Code                                           | `{contactfield=zipcode}`                    |
| Zip Code (Company)                                 | `{contactfield=companyzipcode}`             |

<!-- Page links -->

[companies]: <./../companies/>
[components]: <./../components/>
[contact monitoring]: <./../contacts/contact_monitoring.html>
[custom fields]: <./../contacts/manage_fields.html>
[make pref center]: <./../contacts/customize_preference_center.html>
[manage emails]: <./../emails/manage_emails.html>
[manage pages]: <./../pages/manage_pages.html>
[search]: <./../search/>
