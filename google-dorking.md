# Google Dorking

Hello again! In this post, I'm going to go over an extremely
useful technique security experts often use to gather 
information and uncover unintentionally exposed resources
by leveraging the power of Google. 

This technique is known as **Google Dorking**. A Google Dork is 
a search query that uses Google's advanced query syntax to 
boost the effectiveness of a normal search.

Even if you're not security-oriented, these techniques can be
extremely useful in your daily Googling life. So, let's get
into it!

## Introducing...Dork Parameters

Before we get into some juicy examples, let's make sense
of some of the most useful query strings. I'm only going
to go over some common ones, but you can take a look
at [this article](https://ahrefs.com/blog/google-advanced-search-operators/)
for information on all 42 of them.

### Basic syntax

The basic syntax of an advanced Google query is as follows:

```
search term [query-parameter]:[value]
```

You can chain as many query parameters as you want together
to make for some complex search results.

In addition to this, Google allows you to chain search results by the
conditional statements `AND` and `OR`.

For example, if I wanted to look up the results of pages that included
information about both dogs and cats I could search for:

```
dogs AND cats
```

And these queries can be chained together and mixed intermittently
offering flexibility and power.

If you want to limit your searches to exact matches, you can optionally
add double quotes to your query.

For example, If I wanted to pull pages that contained the phrase, `Squirtle
is cool` exactly, I could search:

```
"Squirtle is cool"
```

It is also important to remember that query parameters are delimited by
spaces. So, if you wanted to search for pages titled "Index of," you would
have to search

```
intitle:"Index of"
```

rather than

```
intitle:Index of
```

The former would search for pages that had "Index" in their title
and matches for "of."

### Useful Parameters

Now, let's get into some important parameters that could make for some
pretty powerful search results.

#### 1. `site:[value]`

The `site` parameter limits results to a specific domain. So,
if I wanted to limit my searches to facebook.com, I would type:

```
site:facebook.com
```

This can be used to find possible vulnerabilities in a specific company,
or limit results about a target to social media sites.

#### 2. `inurl:[value]`

The `inurl` is pretty self-explanatory: it pulls matches based on
what is in the url of the result. If I wanted to pull up admin
pages that might be publicly available, I could search:

```
inurl:admin
```

This is useful for providing URL matches rather than matches in the
page itself.

#### 3. `filetype:[value]`

This parameter is used to restrict results based on filetype. For
example, if I wanted to search for pdf files, I could search:

```
filetype:pdf
```

This is an especially powerful parameter as log files as well as
configuration files can be scraped using this parameter.

#### 4. `intext:[value]`

Using `intext` allows you to specify matches in the body of a page.
The body of the page is anything rendered between HTML tags. For
example, if I wanted to search for blog articles that were about
pokemon, I could search:

```
inurl:blog intext:pokemon
```

These are only some of the key query parameters allowed by Google, but
as you could imagine, they could be combined in clever ways that can
yield powerful results.

## Exploitation Examples

Now it's time for some juicy examples! There are tons of common Google Dorks
out there that expose common info and of course, you can combine them with
your own custom Dork to find some interesting things. You'd be surprised by
what people can leave exposed to the internet. So, let's get to the examples!

```
intext:"index of" ".sql"
```

This Dork string can be used to find SQL database files in directories
that are traversable. This can potentially expose a number of database
files that you can download and look through on your own machine.

No bueno for people that have this exposed as it can contain user information
or other private information.

```
inurl:viewer/live/index.html
```

This Dork can be used to connect to online devices, such as live-streaming webcams. Many webcams are intentionally made to be public, but some might not be.
If you're a creep, this can be perfect for you!

```
inurl:"admin/default.aspx"
```

Using this Dork, you can find default login portals. Oftentimes, login portals
that are unintentionally exposed will be using default credentials. So, this Dork
can be used to find potentially vulnerable sites. Use at your own discretion!

These are only a few of the many powerful Dorks out there. Exploit DB's 
[Google Hacking Database](https://www.exploit-db.com/google-hacking-database)
has loads of other examples, so I encourage you to experiment with these and 
combine them with your own Dorks.

Obviously, it goes without saying that you can stumble upon private information
and vulnerabilities. So, look don't touch! It's best to contact site owners
to make them aware of this information. But DO NOT do anything illegal
(it's only illegal if you get caught \*wink-wink\*).

Anyways, that's it for this security tutorial. More coming soon!