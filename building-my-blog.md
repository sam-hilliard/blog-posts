Hello again! This is going to be my first legitimate post 
on this page so hope you're as excited as I am! Today's post
is going to be about how I built this blog from scratch and
100% **for free**. And this is something anyone can do. So, 
let's get into it!

If you want to skip this section and go straight to the tutorial,
click [here](#tutorial).

## Deciding on a solution

I had two basic requirements for this blog:
1. It had to be headless
2. Be as low cost as possible

Wait, what's up with this headless stuff?

Well, a **headless** blog would be able to operate
without a front-end, meaning, I want to be able to interact
with it (publish posts, delete posts, etc.) without having to
interact with a UI. 

This allows me to edit posts locally by 
just interacting with the backend and then those changes would
automatically be reflected wherever I render the posts
offering me tons of flexibility in how I choose to present 
posts. And these posts can be rendered from *any site*.

In my case, I needed the blog to be headless because my 
portfolio website is hosted on GitHub, which only allows
statically hosted sites (no back-end or database). 
If I wanted a backend, I would have to host that seperately on another server.

## Candidate solutions

Initially, I considered using Wordpress as the framework for 
my headless blog. Wordpress has a strong community behind it
and tons of documentation, so it wouldn't be too hard to spin
up a blog quickly and get to posting. Plus it's open-source. ^_^

That being said, Wordpress is kind of overkill for my purposes
as it's main purpose is to serve styled content to websites in
order to provide a full build.

So, I looked elsewhere and came across [Strapi](https://strapi.io/). With Strapi, I had much more flexibility and
they had a configuration readily available to support
blogging. To get started, all I would have to do is build it 
with the blogging template and I would have access to a clean
UI that stores blogs posts on a database of my choosing.

Like Wordpress, Strapi has to be hosted, so I 
would have to find a platform to host my web app. Although there are numerous cloud hosting platforms that offer 
inexpensive web application hosting (AWS offers hosting on
lambda as little as $5 a month), these platforms usually
offer small resources unless you fork over some extra dough.

Being the cheapskate that I am, I wanted to do this for *free*,
so popular cloud hosting platforms were out the window. 
Unfortunately, not a lot of platforms offer a free option,
especially in the wake of hackers 
(such as [Purpleurchin](https://www.theregister.com/2022/10/27/purpleurchin_cryptomining_github_accounts/))
abusing these free resources to mine crypto. This is the
main reason why hosting platforms, like Heroku, don't offer
free web app hosting anymore :(.

So, I tried looking for headless cloud content management services (CMS) that offered free hosting and stumbled upon
[Cosmic.js](https://www.cosmicjs.com/). They offered a free 
tier subscription. I started using it and was very pleased.
They had an easy to use UI and making objects for content was
pretty straight forward. However, a free subscription
was limited to only 1GB of storage. I liked it so much that
I planned on using it for displaying projects and testimonials
but continued my search for blog hosting.

I finally came across the concept of using Google Sheets as a
database and using the Google Cloud API to interact with it.
At first, this seemed ridiculous. Using a spread sheet as a 
database seemed tacky and stupid. But it would actually be
perfect for my needs. I'm not going to store huge amounts
of data and with a fresh Google Account I'd have access to
**15 GB** of free storage. This would be more than enough
than I'll ever need! With the added bonus of this being hosted
**for free** for me on the cloud, what more could I ask for?!

And that's how I came to the decision of hosting my blog 100%
**for free** with Google Sheets. Now, let's get into the nitty
gritty details of how I actually did it.

## How to host a blog with Google Sheets{#tutorial}

To make a blog with Sheets, you'll need a Google Account (obviously),
a new Sheets doc (to store your blog entries),
and Google Sheets enabled on the Google Cloud API.

### Configuring the Google Cloud API

1. Go to the [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project under the "Select a project" dropdown
3. After filling out basic details, search for "Google Sheets API" in the search bar at the top and click "Enable" on the first result

### Creating a Service Account

1. In the credentials section click "Create Credentials" at the top.
2. Select the "Service account option"
3. Add a name and click "Create and Continue"
4. Configure the role as Project -> Editor, then click "Done"
5. Back in the "Credentials" tab, select the new service account
6. Select Keys -> Add Key -> Create new key
7. Select JSON in the popup and click "Create" (keep this file handy as we'll use this to authenticate with the API)

And that's it! All that needs to be done now is to give edit
permissions to the service account in the Sheet.

To make this usable, I made a [web UI](https://github.com/sam-hilliard/sheets-blog-ui)
that makes it easy to create, edit, and delete posts. Once I
create posts, all I have to do is render them by requesting
the Google Sheet in csv format with [Papa Parse](https://www.papaparse.com/).

And that's how I hosted my blog **for free** using Google Sheets! Thanks for making it this far and stay tuned
for more tutorials and posts! :)