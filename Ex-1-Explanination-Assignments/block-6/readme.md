## BLOCK-readText

#### Creating Reusable and Flexible Layouts

To build layouts whether you take `inline-block` or `float` positioning, it's open to you. Take any method whatever works better for you.

However, there is some new CSS specification to position content. For example Flex and Grid`based properties. But I want you to first learn about the foundation part, that's why we discussed`floats and inline-block` positioning.

Anyway whatever approach you take to position the content, your layout must be reusable and flexible.

##### Reusable Layout

A reusable layout consists of modular classes, and that classes can be reused again and again. We have already learned to take the same class on multiple elements, also multiple class on the same element in the chapter [Getting-to-know-more-about-html-and-css](https://github.com/AltCampus/AC-STYLE-getting-to-know-more-about-html-and-css/edit/master/Ex3-explanation2.md). It is always best practice to write modular styles and reuse it again and again. We will see an example to create a reusable layout. But before that, we will learn about flexible layout, flexible container. Thereafter we will combine all these things to create a reusable and flexible layout.

##### Flexible Layout

A flexible layout consists of flexible units(relative units such as percentage). The benefit of flexible layouts is that it adjusts its size according to the size of the screens.

At some point, we need to make our layout responsive, that we will learn "Responsive Web Design". And the foundation of "Responsive Web Desing" is based on flexible layouts. So why not start the foundation part from here only.

In a flexible layout usually, there is `flexible container` and the columns are created using percentage. Therefore the layout can have flexibility in every size of the screen.

#### Working With Percentages

Percentages are a relative unit in CSS represented by % unit notation one of the most helpful units to create flexible layouts. Percentage unit work in relation to another object in a layout. For example, let's say we have a column of width 50% on our page.

```

  <section>
    <div class="column">......</div>
  </section>

  section {
    width: 1200px;
  }
  .column {
    width: 50%;
  }

```

Here, the column's width is 50%, so it will look for its parent width in which it is nested and then it's width will be calculated. The section's width is 1200px, so the column width will be 600px. If the section's width decreases or increases accordingly the column's width will also decrease or increase but it will always remain 50% of its parent.

Percentage units are always based on the parent element's size. So whenever we define the things in percentage it will always look for its parent.

#### Creating a flexible container

Container sometimes also known as wrapper and sometimes container and wrapper are considered as different two different elements on a page. It's a debatable topic, depends upon the developer how they take it. But according to my understanding, a container or a wrapper is an element that wraps everything else on the page.

We define a class with a container or wrapper with some set of rules which will wrap the content on the page.

Here is an example of a container.

```

  .container {
    max-width: 990px;
    margin: 0 auto;
    padding: 0 30px;
  }

```

##### Width Vs Max-Width

The container element will take some specified width. And the content will remain within the specified width.

Here instead of using `width`, we used `max-width` property. The `max-width` property will keep the container flexible, so when the browser window is narrower the layout will automatically adjust according to the device size. It is important for making a site usable for smaller devices.

Using just `width` property, you will get a horizontal scroll bar when the browser window is narrower. For example:

```

  .container {
    width: 990px;
    margin: 0 auto;
    padding: 0 32px;
  }

```

The `margin: 0 auto` value will keep the container horizontally center of the window. This keeps the alignment of content in sections uniform. The `0` value provides top and bottom margin 0. The `auto` value is for auto margin from left and right, thus the container remains horizontally center.

We also applied `padding: 0 30px` on container. It is to provide breathing space from left and right to our content. This doesn't make much sense for larger devices. But good for mobile devices. So, whenever our layout opens in smaller devices the content will not exactly stick to the edges of the screen with no breathing space.

The container class can be applied to sections.

```
  <!-- HTML -->
  <body>
    <section>
      <div class="container">......</div>
    </section>
    <section>
      <div class="container">......</div>
    </section>
  </body>
```

The container class can be used on any element. Usually, we apply container class on sections or the div inside the container. If each section on a page is having different background-color and the background-color is flowing from the left edge to the right edge of the window, then you should define container class on div nesting inside the section.

#### Reusable and Flexible Layouts in Practice

Now that we know a flexible layout and flexible container, it's time to combine them and create a reusable layout.

As we know a reusable layout consists of modular classes. Let's create a three-column layout and each column the same width with similar styles.

```
  <!-- HTML -->
  <section class="container clearfix">
    <div class="col-1-3">......</div>
    <div class="col-1-3">......</div>
    <div class="col-1-3">......</div>
  </section>

  <!-- CSS -->
  .container {
    max-width: 992px;
    margin: 0 auto;
    padding: 0 30px;
  }
  .col-1-3 {
    float: left;
    width: 30%;
    margin: 1.5%;
  }
  .clearfix:before, .clearfix:after {
    content: "";
    display: table;
  }
  .clearfix:after {
    clear: both;
  }
```

To create three columns we have taken `col-1-3` a modular and applied on three `divs` inside a section. The `col-1-3` class will apply similar styles on each divs (`float: left; width: 30%; margin: 1.5%;`). That is what is known as a modular class, with just one class we set the styles for three divisions. The `container` class on the section will wrap all three divisions inside it and `clearfix` will contain float inside it.

Now if need another section having three columns similar to above on our page we can use the same code again.

```
  <body>
    <section class="container clearfix">
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
    </section>
    ......
    <section class="container clearfix">
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
      <div class="col-1-3">......</div>
    </section>
  </body>
```

This is the benefit of creating a reusable layout, you can use it as many times as you want. This will help you in saving your time as well as will prevent you from repeating.

Learning positioning content on a page is one of the great challenges, and we did it. I know there might confusion but that's fine. To master the topic just need a few times of practice.
Mastering the topic will be a huge step towards mastering the two languages(HTMl & CSS).


