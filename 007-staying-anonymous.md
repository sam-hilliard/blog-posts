# Staying Anonymous

This is a hot topic for a lot of people. How do hackers avoid
getting caught? There are a lot of misconceptions surrounding
this topic and while I'm certainly not an expert, I'll do my
best to shed some light on how to hide.

## Obscuring your location

When people first think of hiding themselves online, one of
the first strategies that come to mind is spoofing your IP
address. This helps make it harder for anyone tracking you
to pinpoint your location.

Most people immediately think of proxies and VPNs when it
comes to IP spoofing. A **proxy** is just a server that
forwards your traffic and sits in the middle of you and whatever
your final destination is (a web server for example). This makes
it seem like you are making requests from whatever IP address your
proxy is located at. **VPNs** take this process one step further
by adding a layer of encryption to the communication. In my opinion,
this isn't all that necessary as HTTPS's encryption standards are more
than enough to do the job.

To further obscure your location by chaining multiple VPNs and proxies
together so that your traffic hops through a series of these servers.
This would make it even harder for someone to trace traffic back to you.

A similar approach to chaining would be to route your traffic through
the **Tor** network, which is essentially a network of volunteer relays,
called **nodes**, that dynamically route your traffic with an added layer
of encryption.

Of course, the simplest thing you could do is connect to a network that
is not associated with you, like public WiFi.

## Is this enough?

However, connecting to proxies, VPNs, and even the Tor network does not guarantee
anonymity. Connecting to any server that isn't yours means there is no guarantee
that the footprints you leave behind in logs won't remain private. Even if a VPN
server claims that they don't log information and won't share your information,
under certain circumstances they could be required by law to fork over the goods.
A similar situation would be when the [Hydra Marketplace](https://www.bbc.com/news/technology-61002904)
was seized by German Police. Even though it was hosted on a "bulletproof hosting" 
company that does not snitch on their customers, they ultimately had to shut down
the site.

## The bottom line

So, how do good hackers get away with crime? They make sure *nothing* can be traced
back to them. Not only do they use the location masking techniques outlined above,
but if they are using tools or services that require an account (like signing up
for a hosting service or creating an email account for spoofing) they make sure
that no information is linked to them. Using an email account or a browser session
stained with cookie data and other tracking information can create a trail
that could potentially lead back to you. A successful hacker might leave a trail
(it's almost impossible not to these days), but one that leads to dead ends.

Therefore, it comes down to being untraceable more so than just simply
connecting to a VPN.

And even then, it's worth noting that in many cases hackers get away with
the crimes they commit because victims usually don't have the resources
or simply don't want to spend time tracking down the hacker. The average
person might be more concerned with removing malware and companies usually
focus their efforts on patching their systems or getting servers back online.
Unless it is a large, persistent crime (like the Hydra marketplace), it is likely
that a pursuit isn't worth it. This is one of the main reasons why cyber
crime is such a big issue.

Anyways, thanks for sticking around and reading a more opinionated article. Again,
I'm no expert and this is just my take. :)