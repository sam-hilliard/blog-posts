# CSS Layouts

Hello again! In this post, I'm going to be talking about
two powerful layout tools in CSS that can be used to
easily and efficiently make responsive layouts. 

When I started learning CSS, layouts were created
using `float`, `tables`, and positioning. These methods are
overly complicated and insufficient for making complex,
responsive layouts.

Flex-layouts and grid layouts were then later introduced
into native CSS to make it *much* easier to create web
layouts.
I'm not going to go into too much rigorous detali as there
are docs for that, but this should be enough of an overview
to get anyone started in confidently making responsive
layouts. 

So, without further-a-do, let's get into it!

## Flex-box Basics

Flex-box layouts are used to align content along an
axis. To get started with flex-box, you have to 
designate a **flex-container** by setting it's `display`
property to `flex.`

```
.flex-container {
    display: flex;
}
```

The children inside of this flex-container are called
**flex-items**. By default, flex-items are aligned
horizontally across a **main-axis**. This is the
default of the `flex-direction` property and can be
changed to align vertically by setting it to `column.`
The `column` and `row` values can also be reversed
by setting the `flex-direction` property to `row-reverse`
or `column-reverse`.

```
.flex-container {
    display: flex;
    flex-direction: row | row-reverse | column | column-reverse;
}
```

By default, flex-items will overflow the flex-container. You
can make them wrap around one another as needed. This is 
where the responsiveness of flex-box layouts come into play.

```
.flex-container {
    display: flex;
    flex-wrap: nowrap | wrap | wrap-reverse;
}
```
A short-hand to combine `flex-direction` and `flex-wrap`
is to use the `flex-flow` property.

```
flex-flow: <direction> <wrap>
```

Possibly the most useful aspect of flex-box layouts is its
alignment properties. The `align-items` property aligns
flex-items along the **cross-axis** which is the axis
perpendicular to the main-axis. The `justify-content` property
aligns content to the main-axis. I'm not going to go through
all of the values, but these are extremely useful to me as I
usually use flex-box for aligning content rather than strictly
for layout. For example, I could easily center all content
inside a `div` with `justify-content` and `align-items`:

```
div {
    display: flex;
    justify-content: center;
    align-items: center;
}
```

With just these few lines, content can be easily centered.
Prior to flex-box, it was common to use `margin` or `padding`
to center content but this could end up leading to
inconcistencies and required extra overhead.

The last topic I want to touch briefly on is controlling the
way flex-items occupy free space in their flex-containers.
There are three properties for controlling this and they
are set on the flex-item itself (not the flex-container).

The first property, `flex-grow` specifies how much a flex-item
is allowed to grow to fill empty space. It is assigned a
positive value which is representative of the ration of free
space it is allowed to grow and occupy. For example, if I had
two `divs` in a flex-container and one had a `flex-grow` of 1
and the other had a `flex-grow` of 2, the later flex-item
would be allowed to grow twice as large as the former.

The `flex-shrink` property works in much the same way, except
it controls how fast an item shrinks with its container when
assigned a positive value. The higher the number, the faster
the shrink.

And finally, `flex-basis` sets the initial amount of space
the item is set to occupy before flex shrinking/growing
occurs.

The short-hand for these three properties is the `flex`
property.

```
.flex-item {
    flex: <flex-grow> | <flex-shrink> | <flex-basis>
}
```

Using these properties can be somewhat complex and it takes
some playing around with the values to really understand
how they work. However, there are some popular values
that can be assigned to the `flex` property that are
sufficient for most cases.

`flex: initial` is the same as `flex: 0 1 auto` and resets
the flex-items values to the default.

`flex: auto` is the same as `flex: 1 1 auto` and can be used
to specify items that all grow and shrink at the same rate.

`flex: none` is the same as `flex: 0 0 auto` and creates
a rigid item that will stay the same size.

Finally, `flex: <positive number>` is the same as
`flex: <positive number> 1 0` and creates an item that
will grow and shrink as needed.

And that's all you need to get started with flex-box. Now,
let's move on to grid layouts!

## Grid Layouts