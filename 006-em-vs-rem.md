# Ems vs Rems

In this post, I'm going to talk about the differences
between two CSS units: **ems** and **rems**. When
used properly, these units are fantastic for easily
creating responsive fonts and scalable layouts. That
being said, applying them incorrectly can lead to some
confusing (and problematic) results.

So, let's get into it so you can start harvesting the
power of ems and rems!

## Sizing fonts with ems and rems

When specifying font-sizes with ems, you are specifying value
that is a scale factor of the element's parent. For example,

```
p {
    font-size: 2em;
}
```

makes paragraphs have a `font-size` twice larger than their
parent (in this case just html). Since the default `font-size`
of `<html>` is `16px`, this results in `<p>` elements having
a `font-size` of `32px`.

Specifying font-sizes with ems can get complicated when you
have nested elements. Let's take a look at this example:

```
...

<div>
    <div>
        <p>Some text</p>
    </div>
</div>

<style>
    div {
        font-size: 1.5em
    }

    div > div {
        font-size: 2em;
    }

    p {
        font-size: 3em;
    }
</style>

...

```

This is where em's unique properties make things a little
tricky. The first `<div>` has a `font-size` of 1.5 times
greater than the `<html>`'s `font-size`. Ok, that's not so
bad.

The nested `<div>` has a `font-size` that is two times bigger
than it's parent. So, it's `font-size` could be
`16px x 1.5 x 2` which works out to be `48px` (assuming the
default of `16px` is used for `<html>`).

Things get even crazier with the `<p>` tag which now has
a `font-size` of `16px x 1.5 x 2 x 3`!

This functionality of em is called **compounding** and can
be a major headache to keep track of when sizing fonts
of nested elements. This is why I *strongly* recommend
against using ems for sizing fonts.

### Enter rems

Using rems turns out to be much more useful, as they get rid
of this compounding problem by scaling fonts to the **root**
(html) `font-size` rather than the parent.

So, in the previous example, all of the elements would be
scaled to the value of `16px`, which is *much* more
predictable.

rems are also extremely useful for responsive font scaling.
If a desktop design required larger fonts than the mobile,
you can scale all of your rem-sized font's with just one
media query that makes the root font size bigger.

It is also more accessible to use rems over a static unit
(like px), because users might specify larger font sizes
in their browser's settings. This would make font sizes
with rems scale to accomidate this preference.

## Layout and Scaling

You can also use both ems and rems for both layout
and scaling (so things like padding, height/width, margin,
etc. are fair game).

Unlike with fonts, ems are a little more predictable as 
they are relative to the element's `font-size`.

For example, I can scale a button fairly easily with ems:

```
.button {
    font-size: 2rem;

    height: 1em;
    width: 2em;
    padding: 1em 2em;
}

.button-lg {
    font-size: 2.5rem;
}

.button-sm {
    font-size: 1.5rem;
}
```

As you can see, items can easily and consistently be scaled
just by changing the `font-size`! For those of you with keen
eyes, I used rems for the `font-size` which would make the
button's `font-size` (and its depending dimmensions) more
consistent but still accessible!

Of course, rems can be used for more rigid sizing as needed.

## In short...

Use rems for font size and whenever you want consistent
dimmensions without sacrificing accessiblity.

Use ems for consistently scaling dimensions.

Hopefully after reading this you will now be able to 
confidently harness the power of ems and rems! This
article would have not been possible without the help
of my good friend Kevin Powell. Watching his videos
helped me learn all of this and more. So, if you're
interested in front-end development, 
[his YouTube channel](https://www.youtube.com/channel/UCJZv4d5rbIKd4QHMPkcABCw) 
will help you fall maddly in love with CSS!