# Reference for devopsdays-theme
# Table of contents
<!-- MDTOC maxdepth:6 firsth1:0 numbering:0 flatten:0 bullets:0 updateOnSave:1 -->

[Fields in YYYY-CITY.yml](#fields-in-yyyy-cityyml)
&emsp;[General Fields](#general-fields)
&emsp;[Date-related Fields](#date-related-fields)
&emsp;[Branding Fields](#branding-fields)
&emsp;[Location Fields](#location-fields)
&emsp;[Navigation Fields](#navigation-fields)
&emsp;[Organizer Fields](#organizer-fields)
&emsp;&emsp;[Team Members](#team-members)
&emsp;&emsp;[Organizer Emails](#organizer-emails)
&emsp;[Sponsor fields](#sponsor-fields)
&emsp;&emsp;[Sponsor Levels](#sponsor-levels)
&emsp;[Program Fields](#program-fields)
&emsp;&emsp;[Program Items](#program-items)
&emsp;&emsp;&emsp;[Program Element Colors](#program-element-colors)
&emsp;&emsp;[Ignite Fields](#ignite-fields)
[Pages and Frontmatter](#pages-and-frontmatter)
&emsp;[General Page Fields](#general-page-fields)
&emsp;[Talk Page Fields](#talk-page-fields)
&emsp;[Speaker Page Fields](#speaker-page-fields)
&emsp;[Program Page Fields](#program-page-fields)
&emsp;[Blog Post Fields](#blog-post-fields)
[Other Settings](#other-settings)
&emsp;[Social Sharing Image](#social-sharing-image)
[Shortcodes](#shortcodes)
&emsp;[google_form](#google_form)
&emsp;[tito_widget](#tito_widget)
&emsp;[cfp_dates](#cfp_dates)
&emsp;[email_organizers](#email_organizers)
&emsp;[event_start](#event_start)
&emsp;[event_end](#event_end)
&emsp;[event_logo](#event_logo)
&emsp;[event_twitter](#event_twitter)
&emsp;[registration_start](#registration_start)
&emsp;[registration_end](#registration_end)
&emsp;[event_map](#event_map)
&emsp;[tix](#tix)
&emsp;[asset](#asset)

<!-- /MDTOC -->


## Fields in main.yml
The `/data/events/YYYY/CITY.main.yml` file is the main configuration file for your event. This is what each field does.

### General Fields

| Field Name         | Type   | Required | Description                                                                                           | Example                                       |
|--------------------|--------|----------|-------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| `name`             | String | Yes      | The name of the event. Four digit year with the city name in lower-case, with no spaces.              | "2017-chicago"                                |
| `year`             | String | Yes      | The year of the event. Make sure it is in quotes.                                                     | "2017"                                        |
| `city`             | String | Yes      | The displayed city name of the event. Capitalize it.                                                  | "Salt Lake City"                              |
| `description`      | String | No       | Overall description of your event. Quotation marks need to be escaped.                                | "It's time for more DevOpsDays at Ponyville!" |
| `ga_tracking_id`   | String | No       | If you have your own Google Analytics tracking ID, enter it here.                                     | "UA-74738648-1"                               |
| `gtm_tracking_id`  | String | No       | If you have your own Google Analytics v4 tracking ID, enter it here.                                  | "G-NCBC4PBEMK"                                |
| `event_group`      | String | No       | If you'd like to group different events together (ie, "australia"), set them to the same "event_group"| "ponyville"                                   |
| `speakers_verbose` | String | No       | Set this to "true" if you want verbose speaker attributes (URLs visible).                             | "true"                                        |
| `cancel`           | String | No       | If your event must be cancelled, add this field with the value of "true" (case-sensitive). This will keep it from being listed in the "upcoming events" views. | "true"  |      

### Date-related Fields
All dates are in unquoted YYYY-MM-DD, like this: `variable: 2016-01-05`, or like `variable: 2016-01-05T23:59:00-06:00`

| Field Name                   | Type       | Required | Description                                                                                                                                                                                                                   | Example                                               |
|------------------------------|------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| `startdate`                  | YYYY-MM-DD | No       | The start date of your event. Leave blank if you don't have a venue reserved yet.                                                                                                                                             | 2016-01-05                                            |
| `enddate`                    | YYYY-MM-DD | No       | The end date of your event. Leave blank if you don't have a venue reserved yet.                                                                                                                                               | 2016-01-05                                            |
| `timeoffset`                 | +/-HHMM    | No       | The offset of the timezone of your event from UTC                                                                                                                                                                             | "-0600"                                               |
| `timezone`                   | String     | No       | The timezone of the event [https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones#List)                                                              | "Europe/London"                                       |
| `cfp_date_start`             | YYYY-MM-DD | No       | The date you will start accepting talk proposals. Can be a blank value.                                                                                                                                                       | 2016-01-05                                            |
| `cfp_date_end`               | YYYY-MM-DD | No       | The date you will close your call for proposals. Can be a blank value. If you set the full datetime string with correct TZ, CFP will display as open until local close time.                                                  | 2016-01-05T23:59:00-06:00                             |
| `cfp_date_announce`          | YYYY-MM-DD | No       | The date you will inform proposers of status. Can be a blank value.                                                                                                                                                           | 2016-01-05                                            |
| `cfp_open`                   | String     | No       | Either "true" or "false". Can be blank. This controls whether or not the "propose" button shows on your event page. *Deprecated field; if you have set `cfp_date_start` and `cfp_date_end` they will serve the same purpose.* | "true"                                                |
| `cfp_link`                   | String     | No       | If you have a custom link for submitting proposals, add it here. This will control the Propose menu item as well as the "Propose" button.                                                                                     | "https://myurlhere" - reference it like "{{< event_link url-key="cfp_link" text="Propose a talk!" >}}" |
| `registration_date_start`    | YYYY-MM-DD | No       | The date you will start accepting registration. If this is set, will make the "Register" button appear on the event's "Welcome" page. Can be a blank value.                                                                   | 2016-01-05                                            |
| `registration_date_end`      | YYYY-MM-DD | No       | The date you will close registration. Controls the appearance of the "Register" button on the "Welcome" page. If you set `registration_date_start` you must set `registration_date_end`. Can be a blank value (unless `registration_date_start` has been set).                                                                                                                                                                   | 2016-01-05                                            |
| `registration_closed`        | String     | No       | Set this to "true" if you need to manually close registration before your registration end date.                                                                                                                              | "true"                                                |
| `registration_link`          | String     | No       | If you have a custom registration link, enter it here. This will control the Registration menu item as well as the "Register" button.                                                                                         | "https://myurlhere" reference it like {{< event_link url-key="registration_link" text="Register to attend the conference!" >}} |                                                                                   |
| `sponsor_link`               | String     | No       | If you have a custom sponsorship link, enter it here. This will control the "Become an X Sponsor!" links. It does NOT change the "Sponsor" button.                                                                            | "https://myurlhere"  |                                                                                   |

### Social Fields
| Field Name              | Type   | Required | Description                                                                                           | Example                                              |
|-------------------------|--------|----------|-------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| `event_social_twitter`  | String | No       | The twitter handle for your event such as "devopsdayschi" or "devopsdaysmsp". Exclude the "@" symbol. | "devopsdaysrox"                                      |
| `event_social_linkedin` | String | No       | The direct URL to your linkedin event or group/company page.                                          | "https://www.linkedin.com/company/devopsdaysrox"     |
| `event_social_youtube`  | String | No       | The Youtube handle for your event such as "devopsdaysrox" or "devopsdayschi". Exclude the "@" symbol. | "devopsdaysrox"                                      |
| `event_social_bsky`     | String | No       | The BlueSky direct URL for your event/group profile. Can link to a custom server.                     | "https://bsky.app/profile/dodrox.bsky.social"        |
| `event_social_mastodon` | String | No       | The Mastodon direct URL for your event/group profile. Can link to a custom server.                    | "https://mastodon.social/@dodrox"                    |
| `event_social_slack`    | String | No       | The invite URL to your slack workspace.                                                               | "https://join.slack.com/t/dodrox/shared_invite/xyz"  |
| `event_social_listserv` | String | No       | The URL to subscribe to your group mailing list.                                                      | "https://lists.devopsdays.org/subscription?f=xyz".   |
| `event_twitter`         | String | No       | Legacy field for the twitter handle. Exclude the "@" symbol. Kept for backward support.               | "devopsdayschi"                                      |

### Branding Fields

| Field Name            | Type   | Required | Description                                                                                                     | Example             |
|-----------------------|--------|----------|-----------------------------------------------------------------------------------------------------------------|---------------------|
| `masthead_background` | String | No       | The image, relative to `static/events/YYYY-CITY` that you want to be the background of the header on your page. | `skyline-night.jpg` |
| `sharing_image` | String | No       | This allows you to set an image that is displayed when posting on social sites (eg: Slack, Twitter, Facebook). This image is used in the `og:image` meta tag field. This image is relative to the `static/events/YYYY-CITY/sharing` directory. It can be either .png or .jpg. Recommended size is 1200 × 630. | `sharing.jpg` |

### Location Fields

| Field Name         | Type   | Required | Description                                                                                                                                     | Example                                         |
|--------------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| ~~`coordinates`~~      | String | Yes      | The coordinates of your city. [Get Latitude and Longitude of a Point](http://itouchmap.com/latlong.html). DEPRECATED. | "41.882219, -87.640530"                         |
| `location`         | String | Yes      | The generator scripts will default to the value of `City`, but you can make it the venue name.                                                  | "Chicago Mart West"                             |
| `location_address` | String | No       | Use the street address of your venue. This will show up on the welcome page if set. Also used by the `event_map` shortcode.                                              | "350 West Mart Center Drive, Chicago, IL 60654" |

### Navigation Fields
These fields are used to control the navigation elements (menu) of your event's page. The syntax for navigation is thus:

```
nav_elements:
  - name: propose
  - name: location
  - name: registration
  - name: program
  - name: speakers
  - name: sponsor
  - name: contact
  - name: conduct
```

If you would like to add a custom/additional navigation to your menu, add another element where you would like it to appear. You will also need to provide the target for the link if it not relative to your event, as so:

```
nav_elements
  - name: propose
  - name: volunteer
  - name: party
    url: http://www.google.com
```
The above example would create a new menu item called "Volunteer" which linked to `devopsdays/events/YYYY-CITY/volunteer`, and another menu item called "party" which would link to `http://www.google.com`

The menu items also take an optional parameter of `icon` where you can set the font-awesome icon that will display on small screens. *Note: This feature is currently deprecated, but it won't break anything if you use this setting* Choose at http://fontawesome.io/icons/. Example:

```
nav_elements
  - name: example
    icon: "map-o"
```

### Organizer Fields

#### Team Members

Remember, the organizers listed are are the same people you have on the mailing list and Slack channel.

Each team member is an element of `team_members`.

| Field Name | Type   | Required | Description                                                                                                                                                | Example                                                                                                                                                                                                                                                                                                             |
|------------|--------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`     | String | Yes      | The person's full name.                                                                                                                                    | "John Doe"                                                                                                                                                                                                                                                                                                          |
| `pronouns` | String | No       | The person's pronouns. Displayed in brackets next to the name.                                                                                             | "he/him"                                                                                                                                                                                                                                                                                                            |
| `role`     | String | No       | The role of the organizer in the team. If not specified, will display "Organizer".                                                                         | "Sponsor Coordinator"                                                                                                                                                                                                                                                                                               |
| `twitter`  | String | No       | The twitter handle of the person, without the `@` symbol                                                                                                   | "johndoe"                                                                                                                                                                                                                                                                                                           |
| `employer` | String | No       | The name of the person's employer.                                                                                                                         | "Acme Anvil Co."                                                                                                                                                                                                                                                                                                    |
| `github`   | String | No       | The GitHub username of the person                                                                                                                          | "johndoe"                                                                                                                                                                                                                                                                                                           |
| `facebook` | String | No       | The full URL to the person's Facebook page                                                                                                                 | "https://www.facebook.com/sally.fields"                                                                                                                                                                                                                                                                             |
| `linkedin` | String | No       | The full URL to the person's LinkedIn page                                                                                                                 | "https://www.linkedin.com/in/sallyfields"                                                                                                                                                                                                                                                                           |
| `website`  | String | No       | The full URL to the person's webpage                                                                                                                       | "https://mattstratton.com"                                                                                                                                                                                                                                                                                          |
| `mastodon` | String | No       | The full URL to the person's Mastodon profile                                                                                                                       | "https://hachyderm.io/@mattstratton"                                                                                                                                                                                                                                                                                          |
| `bluesky` | String | No       | The full URL to the person's Bluesky profile                                                                                                                       | "https://bsky.app/profile/matty.wtf"                                                                                                                                                                                                                                                                                          |
| `image`    | String | No       | The name of the image for this user, located in `static/events/YYYY-CITY/organizers/`. This image must be a JPEG, and should be either 300px square or (optimally) 600px square. | "sally-fields.jpg"                                                                                                                                                                                                                                                                                                  |
| `bio`      | String | No       | The bio for the user. Markdown is supported. Quotation marks must be escaped.                                                                              | "Thought leader paradigm affordances physical computing quantitative vs. qualitative disrupt thought leader disrupt. Venture capital Steve Jobs pitch deck moleskine sticky note agile Steve Jobs pivot disrupt grok driven. Human-centered design bootstrapping agile driven grok food-truck ship it long shadow." |

#### Organizer Emails

| Field Name         | Type   | Required | Description             | Example                                    |
|--------------------|--------|----------|-------------------------|--------------------------------------------|
| `organizer_email` | String | Yes      | Organizer email address | "ponyville@devopsdays.org" |
| `proposal_email`   | String | Yes      | Proposal email address  | "ponyville-proposals@devopsdays.org"  |

### Sponsor fields

Each team member is an element of `sponsors`.

| Field Name | Type   | Required | Description                                                                                                 | Example                           |
|------------|--------|----------|-------------------------------------------------------------------------------------------------------------|-----------------------------------|
| `id`       | String | Yes      | The name of the sponsor; matches to a file in `date/sponsors                                                | arresteddevops                    |
| `level`    | String | Yes      | The level of sponsorship for this sponsor.                                                                  | gold                              |
| `url`      | String | No       | Will override the URL specified in the sponsor file. Useful if you have event-specific URL's for a sponsor. | http://mysponsor.com/?campaign=me |


| Field Name           | Type   | Required | Description                                                               | Example |
|----------------------|--------|----------|---------------------------------------------------------------------------|---------|
| `sponsors_accepted`  | String | No       | Set this to "yes" if you would like the "become a sponsor" link to appear | "yes"   |
| `sponsors_showempty` | String | No       | Set this to "no" to hide the sponsor levels without a sponsor             | "no"    |

#### Sponsor Levels

All sponsorship levels are elements of `sponsor_levels`.

| Field Name | Type   | Required | Description                                                                                                                                                                                                                                 | Example |
|------------|--------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------|
| `id`       | String | Yes      | Identifies the sponsor level as mapped to your list of sponsors. No spaces.                                                                                                                                                                 | gold    |
| `label`    | String | Yes      | How the sponsor level appears on the site. Spaces are allowed.                                                                                                                                                                              | Gold    |
| `max`      | String | No       | The maximum amount of sponsors allowed for this level. Once this has been reached, the "become a sponsor" link for that level will no longer appear. Setting this to "0", or leaving it blank, results in unlimited sponsors for that level | 10      |

### Program Fields

#### Program Items

The elements of your program are set in the `program` section. Example:

```
program:
  - title: "Registration, Breakfast, and Sponsor Booths Open"
    type: custom
    date: 2017-06-16
    start_time: "08:00"
    end_time: "09:00"
    custom_url: "https://example.com/registration"
  - title: "Opening Welcome"
    type: custom
    date: 2017-06-16
    start_time: "09:15"
    end_time: "09:00"
```

| Field Name         | Required | Description                                                                                                                                                                                                                                                 | Example                                                                                                 |
|--------------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| `title`            | Yes      | The name of the program element. If it is a talk, ignite, or workshop, use the name of the talk/ignite/workshop file, minus the `.md` extension.                                                                                                            | "Opening Welcome" or "apple-jack"                                                                       |
| `type`             | Yes      | The type for the program element. Valid choices are `custom`, `talk`, `ignite`, `workshop`, or `open-space`. This defines the color of the program element. `talk`, `ignite`, and `workshop` types will create a link to the program item named in `title`. | talk                                                                                                    |
| `date`             | Yes      | The date of the program element, in YYYY-MM-DD format.                                                                                                                                                                                                      | 2017-06-16                                                                                              |
| `start_time`       | Yes      | The start time of the program element.                                                                                                                                                                                                                      | "08:00"                                                                                                 |
| `end_time`         | Yes      | The end time of the program element.                                                                                                                                                                                                                        | "13:40"                                                                                                 |
| `comments`         | No       | Additional comments/notes about the program types `talk`, `workshop` and `custom` (for example, location of an evening event). Markdown is supported.                                                                                                       | "This will be at the [Pony Club](http://www.mattstratton.com),1005 Ponyville Drive,Ponyville, IL,60612" |
| `background_color` | No       | Allows the ability to override the color of the program element. Only the background color can be changed; please test to make sure the color works with the displayed text colors. Color is expressed in RGB HEX value. Must be in quotes.                 | "#FFFA99"                                                                                               |
| `custom_url`       | No       | Replaces the URL for various program types to link to external URL or a URL of your choosing. Valid for `custom`, `talk`, `ignite`, `workshop`, or `open-space`                                                                                     | "https://example.com"                                                                                   |
| `block`   | No | Ignite section only - if there are multiple ignites in the same day, this allows them to be broken up into multiples | "ignite-1" |

##### Program Element Colors

The current colors for program types (click on a link to see the color):

- custom: [#bfbfc1](http://www.perbang.dk/rgb/BFBFC1/)
- talk: [#0082AB](http://www.perbang.dk/rgb/0082AB/)
- ignite: [#00C342](http://www.perbang.dk/rgb/00C342/)
- workshop: [#99E6FF](http://www.perbang.dk/rgb/99E6FF/)
- open-space: [#FF8300](http://www.perbang.dk/rgb/FF8300/)


#### Ignite Fields

The Ignite elements are set in the `ignites` section. Example:

```
ignites:
  - title: "spike"
    date: 2017-06-16
  - title: "rainbow-dash"
    date: 2017-06-16
    custom_url: "https://example.com/ignites
  - title: "twilight-sparkle"
    date: 2017-06-16
    block: "ignite-1"
```

| Field Name   | Required | Description                                                                                                                                   | Example                                |
|--------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------|
| `title`      | Yes      | The title of the ignite. It should be named after the filename (without the `.md` extension) of a talk | "matt-stratton"                                                                 |
| `date`       | Yes      | The date of the ignite, in YYYY-MM-DD format.                                                                                                 | 2017-06-16                               |
| `custom_url` | No       | Allows linking to URL off-site for various reasons.                                                                                           | "https://example.com/schedule"           |
| `block`      | No       | If there are multiple blocks of ignites in the same day, this specifies which block                                                           | "ignite-1"                               |

## Pages and Frontmatter

The "frontmatter" refers to the TOML fields at the beginning of all `.md` files in your content directory (i.e., `content/events/2017-ponyville/...`). Frontmatter looks like this:

```
+++
Description = "DevOpsDays Ponyville is back for 2017! We will be hanging out and showing off our awesomeness."
Title = "devopsdays Ponyville 2017"
Type = "welcome"
aliases = ["/events/2017-ponyville/welcome"]
+++
```

The content is everything following the last `+++`.

### General Page Fields

All pages have some common frontmatter elements that they share. These include:

| Field Name      | Required | Description                                                                                                                                                                                                                                                                                                  | Example                                                                                          |
|-----------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
| `Description`   | No       | The summary, or description, of the content of the page. It is highly recommended that this is populated on every page, as it is used in social sharing, as well as for SEO purposes.                                                                                                                        | "DevOpsDays Ponyville is back for 2017! We will be hanging out and showing off our awesomeness." |
| `Title`         | Yes      | The title of the page. This is usually prepopulated for you, but it is highly recommended that you do NOT use the default titles; add some flair to set your event apart.                                                                                                                                    | "devopsdays Ponyville 2017"                                                                      |
| `Type`          | Yes      | This is required, but is usually pre-populated. Valid types are "event", "welcome", "program", "speaker", "speakers", and "talk". The type you should use for "regular" pages is "event".                                                                                                                    | "talk"                                                                                           |
| `aliases`       | No       | This creates aliases to the page. For example, if you want your index page to also be accessible as `/welcome` under your event, you would add the alias here.                                                                                                                                               | ["/events/2017-ponyville/welcome"]                                                               |
| `sharing_image` | No       | This allows you to set an image that is displayed when posting on social sites (eg: Slack, Twitter, Facebook). This image is used in the `og:image` meta tag field. This image is relative to the `static/events/YYYY-CITY/sharing` directory. It can be either .png or .jpg. Recommended size is 1200 × 630. | "matt-stratton-card.jpg"                                                                         |

### Talk Page Fields

Pages of the type `talk` (which can include workshops, ignites, or talks) have a few additional frontmatter elements available to them, in addition to the ones mentioned above.

| Field Name    | Required | Description                                                                                                                                                                                                     | Example                                                                             |
|---------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| `speakers`    | Yes      | An array of the names of the speakers (relative to the filenames for the speaker in your `content/events/YYYY-CITY/speakers` directory). Even if there is only one speaker, it should be formatted as an array. | speakers = ["fluttershy", "spike"]                                                  |
| `youtube`     | No       | The ID of the YouTube video (not the full URL).                                                                                                                                                                 | "8ClZXJsgpHY"                                                                       |
| `vimeo`       | No       | The ID of the Vimeo video (not the full URL).                                                                                                                                                                   | "219025568"                                                                         |
| `slideslive`  | No       | The ID of the presentation on SlidesLive                          | "12345678" |
| `speakerdeck` | No       | The URL to the talk on Speakerdeck. Use the full URL.                                                                                                                                                           | "https://speakerdeck.com/mattstratton/shifting-left-securely"                       |
| `slideshare`  | No       | The URL to the talk on Slideshare. Use the full URL                                                                                                                                                             | "http://www.slideshare.net/mattstratton/the-five-love-languages-of-devops-54549536" |
| `googleslides` | No      | The ID of the talk on Google Slides (not the full URL).                                                                                                                                                         | "1QnakgUC8AaNydPZCmKGYYja8gs2WoHbHRSjioIVdD9g" |
| `pdf`          | No      | The URL to the PDF. Use the full URL.                                                                                                                                                                           | "http://www.mattstratton.com/my-slides.pdf" |
| `notist`      | No      | The ID of the deck on Notist, including the username. | "mattstratton/jLwszn" |
| `slides`      | No       | If the slides are available on a service other than Speakerdeck or Slideshare, enter the URL here.                                                                                                              | "http://www.mattstratton.com/my-slides"                                             |

### Speaker Page Fields

Pages of the type `speaker` have a few additional frontmatter elements available to them, in addition to the general ones mentioned above.

| Field Name | Required | Description                                                                                                                                                                                                | Example                                     |
|------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|
| `website`  | No       | The website for the speaker.                                                                                                                                                                               | "https://www.mattstratton.io"               |
| `twitter`  | No       | Speaker's Twitter username, without the @.                                                                                                                                                                 | "mattstratton"                              |
| `facebook` | No       | Speaker's Facebook URL                                                                                                                                                                                     | "https://www.facebook.com/matt.stratton"    |
| `linkedin` | No       | Speaker's LinkedIn URL                                                                                                                                                                                     | "https://www.linkedin.com/in/mattstratton/" |
| `github`   | No       | Speakers' GitHub username.                                                                                                                                                                                 | "mattstratton"                              |
| `gitlab`   | No       | Speakers' GitLab username.                                                                                                                                                                                 | "mattstratton"                              |
| `twitch`   | No       | Speakers' Twitch username.                                                                                                                                                                                 | "mattstratton"                              |
| `mastodon`   | No       | Speakers' Mastodon URL username.                                                                                                                                                                                 | "https://hachyderm.io/@mattstratton"                              |
| `bluesky`   | No       | Speakers' Bluesky profile.                                                                                                                                                                                 | "https://bsky.app/profile/matty.wtf"                              |
| `image`    | No       | The image for the speaker. This image is relative to the `static/events/YYYY-CITY/speakers` directory. It can be either .png or .jpg. It is recommended to be 600px square.  | "matt-stratton.jpg"                         |

### Program Page Fields

The page of type `program` has one additional frontmatter element.

| Field Name | Required | Description                                              | Example |
|------------|----------|----------------------------------------------------------|---------|
| `icons`    | No       | Toggles display of slide/video icons on the program page | "true"  |

### Blog Post Fields

| Field Name      | Required | Description                                                                                                                                                                         | Example                                                                                                                                                                                                                                                                                              |
|-----------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Description`   | No       | The short summary of this post. This is used in various places on the site, as well as for sharing. While it is optional, it is highly recommended to use it. Markdown is allowed.  | "[DevOpsDays Chicago](https://devopsdays.org/events/2016-chicago) took place on August 30th & 31st at Summit West in beautiful downtown Chicago. A sold-out, diverse crowd gathered for keynotes, presentations, lightning talks, and open spaces to learn, discuss, and promote all things DevOps." |
| `Author`        | No       | The name of the person who wrote the blog post.                                                                                                                                     | "Matt Stratton"                                                                                                                                                                                                                                                                                      |
| `title`         | Yes      | The title for the blog post.                                                                                                                                                        | "Chicago 2016 In Review"                                                                                                                                                                                                                                                                             |
| `sharing_image` | No       | The image to use for social sharing. This is a path relative to the `static` directory.                                                                                             | "img/blog/chicago-2016-sharing.jpg"                                                                                                                                                                                                                                                                  |

## Other Settings

### Social Sharing Image
An event can create a sharing image for use on social media (when the url is shared on Facebook, for instance). This image can be either PNG or JPG and must be located in the `static/events/YYYY-CITY/sharing/` directory. It should be a minimum 1200 x 630px, and use ratio: 1.91:1. To set the overall sharing image for the event, set the `sharing_image` field in the `YYYY-CITY.yml` data file. To set a custom sharing image on a per-page basis (for example, on an individual speaker's page), set the `sharing_image` field in the page's frontmatter. 

## Shortcodes

Shortcodes can be used in any of your content (i.e., ".md" files. They provide easy ways to add content without having to write a lot of coding.)

### google_form
This shortcode allows for the embedding of a Google form on a page, in a manner that maintains the responsive, mobile-friendly design of the site. To use it, you only need the URL of your form (not the full embed code) and enter this on your page (substituting the proper URL):
```
{{< google_form "https://docs.google.com/forms/d/e/1FAIpQLScvv-ty_wEBlYkJaEC1OU0qqqbIHjf9JVa-Ptdo5TcHqz5EDA/viewform?usp=sf_link" >}}
```

### tito_widget

Using the tito shortcode enables the embedding of the tito sales widget described on their documentation (https://ti.to/docs/widget). To use it you just need to enter to event path of your tito event which will follow the URL of your event page. For example, if the URL is `https://ti.to/devopsdays-london/2019` your event path would be `devlopsdays-london/2019`. The shortcode also enables the other features described such as the ability to show specific tickets using the examples shown below

```
{{< tito_widget event="devopsdays-london/2019" >}}
```

To show only a specific ticket within the widget:

```
{{< tito_widget event="devopsdays-london/2019" releases="fiaurhghf2k">}}
```

To show discounted tickets on the page (they display as a striked through full-price along with the new price):

```
{{< tito_widget event="devopsdays-london/2019" discount-code="examplediscount" >}}
```

### cfp_dates
This shortcode displays the dates for the CFP. It is used in the default `propose.md` that is generated from the script. 
```
{{< cfp_dates >}}
```

### email_organizers
This shortcode will generate a `mailto` link to the organizer email address. 
```
{{< email_organizers >}}
```

To add a subject to the `mailto` link:
```
{{< email_organizers subject= "Your Subject Here">}}
```

### event_start
Returns the start date of your event
```
{{< event_start >}}
```

### event_end
Returns the end date of your event
```
{{< event_end >}}
```

### event_logo
If you have a `logo.png` or `logo.jpg` in your `static/events/city-yyyy` directory, this will return the HTML for the image. This is mostly suited for use on your `welcome.md` page.
```
{{< event_logo >}}
```

### event_twitter
This returns a twitter follow link, set to either `@devopsdays` if you have not set a Twitter handle in your data file, or whatever is set as your event's Twitter handle in your data file. 
```
{{< event_twitter >}}
```

### registration_start
Returns the start date of registration for your event
```
{{< registration_start >}}
```

### registration_end
Returns the end date of registration for your event
```
{{< registration_end >}}
```
### event_map
If you have `location_address` set in your datafile, this will return a Google Map of that address. Takes two optional parameters (`height` and `width`) to set the dimensions of the map. Both parameters are optional. If not set, the map will default to 450px wide and 250px tall.
```
{{< event_map >}}
```
or
```
{{< event_map width = "600" height="500" >}}
```

### tix
Embeds the DevOpsDays Pretix ticket and registration system
This shortcode requires two parameters, city and year, where the city is typically the organiser city and the year the event year.
Please note this may be differ, please check with in your Pretix for the two names.
To enable the header text, add `info=show` to enable showing of the Event Info section.

```
{{< tix city="belgium" year="antwerp-2024" info="show">}}
```

### asset
Create a links to a file or image from the DevOpsDays assset website.
This shorcode requires the city name `city`, the year `year`, the name `name` being file or image and the link type, being `file` which creates a hyperlink or `image` which embeds the image on the page.

```
{{< asset year="2025" city="chicago" name="prospectus" file="2025-chicago-devopsdays-prospectus.pdf" >}}
```

```
{{< asset year="2025" city="chicago" name="map layout" image="map.png" >}}
```

