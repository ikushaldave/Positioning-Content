## BLOCK-readText

### Positioning Content

Over the last few chapters, we have been creating boxes and manipulating their size and spaces around them. So far we have been only looking at the layouts where contents are flowing vertically, which means single column layouts. But when it comes to creating a real website, the layout can be complex. It's not only about creating boxes or working with a single column layout but more about the place your content in a more digestible way.

To create a layout and represent our content in a more beautiful way CSS provides usability to position our content and elements in any imaginable way. In this chapter, we are going to look into multicolumn layouts. We will be learning how to create reusable layouts.

#### Positioning with inline-block

Usually, to create an outline for any section or division we will be working with block-level elements. And the block-level element always starts from a new line taking whole available width, that we know from the previous chapter. One of the approaches we can take to make block-level elements line up one after another is to overwrite its display property value to `inline-block`. We have already seen how to work with inline-block level elements.

```
  <!-- HTML -->
  <header>..........</header>
  <aside>.........</aside><!--
  --><section>.........</section>
  <footer>............</footer>

  <!-- CSS -->
  header, aside, section, footer {
    background: green;
    padding: 50px;
    box-sizing: border-box;
  }
  section, aside {
    display: inline-block;
    margin: 32px 1.5%;
  }
  aside {
    width: 30%;
  }
  section {
    width: 63%;
  }
```

In this example, we want the header at the top and footer at the bottom of the page. In between, we have a sidebar on the left and a section on the same line. That means we have a two-column layout. So to make aside and section come in a single line we overwritten its display property value to `inline-block`. So that they accept all the box model properties and will line up one after another on the same line.

> ##### The Universal Selector
>
> As you see in the above code I used `border-box` value to the `box-sizing` for every element.
> Generally the best `box-sizing` value to use is `border-box`, this we know from the previous chapter ["Box Model"](https://github.com/AltCampus/AC-STYLE-box-model/blob/master/Ex1-explanation.md).
> The `border-box` value makes our math much easier. And that's the best practice to make every element as `border-box`. This will be helpful while working with the percentage unit.
> To select every element on a document there is universal selector in CSS.
>
> ```
>   *, *:before, *:after {
>     box-sizing: border-box;
>   }
>
> ```
>
> The `*` is a universal selector, which target each and every elemnt in the document.
> The `*:before` and `*:after` is a pseudo element which I have mentioned below.

Remember, in the box model chapter, we have discussed that, there always exists a small space between the inline-block element and how to get rid of that. So do not forget to remove that space. It may disturb the flow of the content on a page.