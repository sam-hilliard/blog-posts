CSS Layouts
===========

Hello again! In this post, I'm going to be talking about two powerful layout tools in CSS that can be used to easily and efficiently make responsive layouts.

When I started learning CSS, layouts were created using float, tables, and positioning. These methods are overly complicated and insufficient for making complex, responsive layouts.

Flex-layouts and grid layouts were then later introduced into native CSS to make it _much_ easier to create web layouts. I'm not going to go into too much rigorous detail as there are docs for that, but this should be enough of an overview to get anyone started in confidently making responsive layouts.

So, without further ado, let's get into it!

Flex-box Basics
---------------

Flex-box layouts are used to align content along an axis. To get started with flex-box, you have to designate a **flex-container** by setting its `display` property to `flex.`

    .flex-container {
        display: flex;
    }
    

The children inside this flex-container are called **flex-items**. By default, flex-items are aligned horizontally across a **main-axis**. This is the default of the `flex-direction` property and can be changed to align vertically by setting it to `column.` The `column` and `row` values can also be reversed by setting the `flex-direction` property to `row-reverse` or `column-reverse`.

    .flex-container {
        display: flex;
        flex-direction: row | row-reverse | column | column-reverse;
    }
    

By default, flex-items will overflow the flex-container. You can make them wrap around one another as needed. This is where the responsiveness of flex-box layouts comes into play.

    .flex-container {
        display: flex;
        flex-wrap: nowrap | wrap | wrap-reverse;
    }
    

A short-hand to combine `flex-direction` and `flex-wrap` is to use the `flex-flow` property.

    flex-flow: <direction> <wrap>
    

Possibly the most useful aspect of flex-box layouts is their alignment properties. The `align-items` property aligns flex-items along the **cross-axis** which is the axis perpendicular to the main-axis. The `justify-content` property aligns content to the main-axis. I'm not going to go through all of the values, but these are extremely useful to me as I usually use flex-box for aligning content rather than strictly for layout. For example, I could easily center all content inside a `div` with `justify-content` and `align-items`:

    div {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    

With just these few lines, content can be easily centered. Before flex-box, it was common to use `margin` or `padding` to center content but this could end up leading to inconsistencies and required extra overhead.

The last topic I want to touch briefly on is controlling the way flex-items occupy free space in their flex-containers. There are three properties for controlling this and they are set on the flex-item itself (not the flex-container).

The first property, `flex-grow` specifies how much a flex-item is allowed to grow to fill space. It is assigned a positive value which is representative of the ratio of free space it is allowed to grow and occupy. For example, if I had two `divs` in a flex-container and one had a `flex-grow` of 1 and the other had a `flex-grow` of 2, the later flex-item would be allowed to grow twice as large as the former.

The `flex-shrink` property works in much the same way, except it controls how fast an item shrinks with its container when assigned a positive value. The higher the number, the faster the shrink.

And finally, the `flex-basis` sets the initial amount of space the item is set to occupy before flex shrinking/growing occurs.

The shorthand for these three properties is the `flex` property.

    .flex-item {
        flex: <flex-grow> | <flex-shrink> | <flex-basis>
    }
    

Using these properties can be somewhat complex and it takes some playing around with the values to understand how they work. However, there are some popular values that can be assigned to the `flex` property is sufficient for most cases.

`flex: initial` is the same as `flex: 0 1 auto` and resets the flex-items values to the default.

`flex: auto` is the same as `flex: 1 1 auto` and can be used to specify items that all grow and shrink at the same rate.

`flex: none is the same as`flex: 0 0 auto\` and creates a rigid item that will stay the same size.

Finally, `flex: <positive number>` is the same as `flex: <positive number> 1 0` and creates an item that will grow and shrink as needed.

And that's all you need to get started with flex-box. Now, let's move on to grid layouts!

Grid Layouts
------------

Much like with flex-box layouts, you start out creating a **grid-container** by setting `display: grid/inline-grid`. From there, you can structure your grid by defining the size and number of its rows and columns. To do this, you would use` grid-template-rows`and`grid-template-columns`.

    .grid {
        display: grid;
        grid-template-rows: repeat(4, 1fr);
        grid-template-columns: repeat(3, 1fr);
    }
    

This creates a 4x3 grid with even evenly divided cell areas depending on the size of the grid. The **fr** unit is introduced in grid layouts to denote a fraction of available space. `1fr` is commonly used to define cell widths/height as this will result in evenly distributed cell areas that are responsive to the size of the grid container. You can also use static values in `px` for example as well, but `1fr` works for most applications. The `repeat()` function is also used to make the values more concise.

To make your code more semantic, you can use the `grid-template-areas` in conjunction with your `grid-template-rows/columns` specifications.

    .grid-container {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        grid-template-rows: auto;
        grid-template-areas:
            "header header header header"
            "about. pfp"
            "footer footer footer footer"
    }
    
    header {
        grid-area: header;
    }
    
    .about-section {
        grid-area: about;
    }
    
    .profile-pic {
        grid-area: pfp;
    }
    
    footer {
        grid-area: footer;
    }
    

This creates a 5 column grid with rows depending on the size of the content in them. The header and footer sections would span all of the columns, while the about section would span two columns and the profile pic would span 1. The `.` specifies that nothing will fill the column between the about section and the profile pic. It is essentially empty space.

The `grid` property is a short-hand for `grid-template-rows/columns`, `grid-template-areas` and `grid-auto-rows/columns/flow`. I won't cover grid-auto layouts in this post, but the shorthand is super handy and its basic syntax is as follows:

    .grid-container {
        display: grid;
        grid: <grid-template-rows> / <grid-template-columns>
    }
    

You can mix in the other attributes mentioned above, but I prefer to separate my `grid-template-rows/columns` from my`grid-template-areas`because it's more readable for me. Of course, you can define where content is positioned on the grid using`grid-row/column-start/end` properties on the grid items, but I think that grid-template-area is better for readability and requires less code when creating responsive layouts. Feel free to go over the docs about these properties as they are still worth learning.

The grid layout also has similar alignment properties as flex-box. `justify/align-items` can be used to align items along the main/cross-axis of grid cells, while `justify/align-content` aligns the entire grid container. I'm not going to go over the specific properties as they are so similar to flex-box alignment that I would feel as though I'm repeating myself on that topic.

When to use Flex-box vs Grid
----------------------------

This is a widely debated and controversial topic in the realm of web development, but for me, I believe the answer is fairly simple: **use flex-box for simple alignment and grid for the overall layout**. Although they are both tools for layout, I personally just use a flex-box if I need to tidy things up after creating the main layout. Grid, in my opinion, is just far-superior in getting content where I want it. In the past, I used to use a flex-box for nearly everything which caused me so much headache and overhead. So, I advise you to use **grid** for the **big picture** and **flex-box** for **fine-tuning**.

And there you have it! Two of the most powerful layout tools are now at your disposal! I wish these were available when I first started.