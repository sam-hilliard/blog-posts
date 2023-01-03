# Useful CSS Functions for Responsive Design

When creating responsive websites, we often think of creating
media queries with breakpoints that fit the most popular 
desktop, mobile, and tablet screen sizes. However, with the
huge variety of devices out there, simply writing a few media
queries. Moreover, (in my opinion) media queries are messy and
cause code readability and extendability to suffer the more
you write. Thus, I think they should be avoided whenever
possible.

Luckily, modern CSS functions allow us to create responsive
elements without using media queries. So, without further-a-do,
here are a few life-saving CSS functions that will make your
responsive designs cleaner and more flexible.


## `min()`

Number one on the list is the `min()` function. This function
accepts two (or more) parameters and returns the value of the
parameter that is the smallest (pretty self explanatory,
right?).

While simple in design, it's uses can be pretty powerful.

For example, it can turn this two liner:

```
div {
    width: 100vw;
    max-width: 1000px;
}
```

into this:

```
div {
    width: min(1000px, 100vw);
}
```

Even though this is a simple (and common) use-case, `min()` is
not only limited to widths and heights, but paddings, margins,
and font-sizes as well!

You can also pass in calculations without having to call the
`calc()` function like this:

```
div {
    padding: min(25px, 10vh + 1rem);
}
```

## `max()`

`min()`'s opposite, `max()` functions in exactly the same way,
except it returns the maximum value of it's passed parameters.

Whereas the `min()` function is useful for limiting the growth
of an element, the `max()` function can be used to limit the
shrinking of an element.

```
div {
    padding: max(1rem, 3vh + 1rem);
}
```

In the preceding example, a div is created whos padding will
grow depending on the viewport height, but will not shrink
past `1rem`. This is great if you want to avoid responsive
units from squishing your elements too much.

## `clamp()`

The last function, `clamp()`, takes the best of both worlds
from the previous functions. It bounds a value between a
minimum and a maximum. 

The syntax is as follows:

```
clamp(<minimum>, <base>, <maximum>)
```

Where `clamp()` is most useful is for creating responsive font
scales.

Take this example:

```
body {
    font-size: clamp(1rem, calc(1rem + 0.25vw), 1.25rem);
}
```

This creates a body font that gets no smaller than 1rem but
never exceeds 1.25rem as the viewport width increases.

It's kind of complex to come up with a responsive type-scale
on your own, so here's a super [handy generator](https://utopia.fyi/type/calculator/)
to make things way easier.

And that's a wrap on these simple but powerful functions.
I highly encourage them to use them whenever you can to
make your code better and more responsive.