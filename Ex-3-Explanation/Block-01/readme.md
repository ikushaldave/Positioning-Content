## BLOCK-readText

### Uniquely Positioning Element

Sometimes you may need more control over the position of an element. You may want to precisely position an element on a page. The `inline-block and float positioning` which is used to create columns, won't do the trick.

Sometime we may want to position an element very precisely anywhere in the window, which may be exactly at the center or top corner of the page or right bottom corner of the page.

In such cases `position` property comes into play. The `position` property accepts four different values, `static, relative, absolute, fixed`.

The position property works in connection with `box-offset` properties - `top, right, left, and bottom`. The `box-offset` properties exactly position an element by moving it in different directions.

#### Position Static

By default, every element in a document is a `static` element and does not accept any `box-offset` properties. It will be in the normal flow of the page, won't be repositioned.

However, the default `static` value for `position` property can be overwritten with either `relative or absolute or fixed`.

#### Position Relative

The `relative` value is somewhat different from `static` one because it accepts all the box-offset properties. We can precisely position the element by shifting it from its default position in any direction(top, right, bottom, or left).

```
  .box {
    position: relative;
    left: 60px;
    top: 60px;
  }
```

In the above example, the box will be shifted from the left towards the right by `60px`. Similarly from the top towards the bottom by `60px`.

> #### Box Offset Properties
>
> The four box offset properties, top, right, bottom, and left specify how an element will be positioned and in which direction.
> These box offset properties only work with a relative, absolute, and fixed positioned element.
> With static elements, box offset properties do not work.

Although the `relative` position accepts `box-offset` properties, still it will be in the normal flow of the page. The relatively positioned element will be shifted from its original position, without disturbing another element on the page.

The original place of a relatively positioned element won't be taken by any element, it will remain empty. However, the relatively positioned element can overlap or underlap other elements, without disturbing their original positions. It won't push or shifts other elements on the page.

For example let's position an element relatively:

```
  <div class="box box-1">......</div>
  <div class="box box-2">......</div>
  <div class="box box-3">......</div>

  .box {
    width: 100px;
    height: 100px;
    background: green;
  }
  .box-2 {
    position: relative;
    top: 60px;
    left: 60px;
  }
```

There are three boxes and each box is having the same styles. But we only position the second box relatively. The second box will shift from the top towards the bottom and left towards the right by `60px`. But it won't disturb the position of the other two boxes on the page. Also, the original position of the element will be maintained.

If for the relatively positioned element, suppose both `top` and `bottom` `box-offset` properties are declared. The `top` property will take priority. For the `left` and `right` offsets depends upon the language which will take priority. For example, if the page is English, the `left` offset will be having priority and for Arabic pages `right` offset will be given priority.

#### Position Absolute

The `absolute` value for position property is different from `relative`. The absolutely positioned elements accept all the `box-offsets` however they are removed from the normal flow of the page. Upon removing from the normal of the page the elements lose its original position. And that lost position will be taken by the upcoming element.

```
  .box {
    position: absolute;
    right: 60px;
    bottom: 60px;
  }
```

As the element is removed from the normal flow it can position in relation to its parent element which is already relatively or absolutely positioned. If the parent element is not relatively or absolutely positioned then the element will be positioned in relation to the `body` of the page.

The `display` property may also change if the element is absolutely positioned. A `block-level` elements will start taking space according to the content. At the same time, an inline-level element may start accepting the width and height.

If no `box-offset` properties are specified for absolute elements, the element will remain absolutely positioned in its original position but on the `Z-axis`. The `X` and `Y` plane will be lost. Therefore the next element will take the original position of the absolute element and the absolute element will be on top of it.

```
  <div class="box box-1">......</div>
  <div class="box box-2">......</div>
  <div class="box box-3">......</div>

  box {
    width: 100px;
    height: 100px;
    background: green;
  }
  .box-2 {
    position: absolute;
  }
```

In the above example the `box-2` is absolutely positioned, so the original position of box-2 on `X-Y` plane will be covered by the `box-3`, and box-2 will be on top box-3.

As discussed above the absolute element can be positioned in relation to its `parent` or the `body` of the page. To position an element absolutely in relation to its parent the parent element must be either relatively or absolutely positioned.

```
  <div class="box box-1">......</div>
  <section class="parent-box">
    <div class="box box-2">......</div>
  </section>
  <div class="box box-3">......</div>


  box {
    width: 100px;
    height: 100px;
    background: green;
  }
  .parent-box {
    position: relative;
  }
  .box-2 {
    position: absolute;
    right: 0;
    bottom: 0;
  }
```

Here, the `box-2` is absolutely positioned with relative to its parent, because the `parent-box` has been relatively positioned. Therefore the box-2 will sit at the right bottom corner of the parent-box.

If the parent element would not have relatively positioned the element would be sitting right bottom corner of `body` of the page.

If the absolute elements have fixed `width` and `height`, and both `top` and `bottom` offset properties are applied, the top will take priority. For `left` and `right` offset properties, it depends upon the language which will be given priority.

However, if the element does not have any specific `width` and `height`, then the element will start from both `top` and `bottom` side. As a result, covering the specified height of the relative parent or else covering the whole height of the body. The same goes for the `left` and `right` offset. The element takes the whole specified width. Combining all the four `box-offset` the element takes the specified width and height.

#### Position Fixed

Position `fixed` is similar to `absolute` positioning. However, the `fixed` positioning will be always relative to the browser viewport. The `fixed` positioned elements do not scroll with the page. Its position will be fixed relative to the browser viewport no matter where you stand on the page.

```
  .box {
    position: fixed;
    right: 60px;
    bottom: 60px;
  }
```

Similar to the absolute element, the display property for the fixed element may also change. Fixed `block-level` elements may take space according to the content it wraps. At the same time, an inline-level element may start accepting width and height.

#### Z-index Property

Normally all the elements on a page are displayed on `x` and `y` plane. By default element stack on top each other or line up one after other depending upon the display property. However, when you start positioning elements using `position` property, an element may be placed on top of another. Using `z-index` property you can decide the order of an element, which will be on top and which will be at the bottom.

The z-index property only works with `relative`, `absolute`, and `fixed` elements. By default, every element has `0` value for the `z-index` property. The element with the highest `z-index` value will appear on top and with the lowest value will at the bottom.

```
  <section class="parent-box">
    <div class="box box-1">1</div>
    <div class="box box-2">2</div>
    <div class="box box-3">3</div>
  </section>

  .parent-box {
    height: 200px;
    background: #bada55;
    position: relative
  }
  .box {
    width: 100px;
    height: 100px;
    position: absolute;
  }
  .box-1 {
    left: 10px;
    top: 10px;
    background: red;
    z-index: 1;
  }
  .box-2 {
    left: 30px;
    top: 30px;
    background: blue;
    z-index: 2;
  }
  .box-3 {
    left: 50px;
    top: 50px;
    background: green;
    z-index: 3
  }
```

Here, the `box-3` is having the highest `z-index` value, therefore, it will be on top and `box-1` is having the lowest `z-index` value so it will be at the bottom.

Usually, you won't need `position` property to build a layout. The layouts are made using other position properties like, `float, inline-block, flex or Grid`. But in certain cases when you need to uniquely position an element on a page, then only `position` property comes into play.