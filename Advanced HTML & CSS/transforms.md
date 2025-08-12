
# CSS Transforms 🚀

The CSS `transform` property lets you modify the coordinate space of the CSS visual formatting model. Essentially, it allows you to **move, rotate, scale, and skew elements** in both two-dimensional and three-dimensional space.

## Syntax and Vendor Prefixes

To ensure broad browser compatibility, especially with older versions, it's a good practice to include vendor prefixes. The standard, unprefixed version should always be declared last to override the prefixed versions once a browser fully supports the property.

```css
div {
  -webkit-transform: scale(1.5); /* Chrome, Safari, newer Opera */
  -moz-transform: scale(1.5);    /* Firefox */
  -o-transform: scale(1.5);      /* Older Opera */
  transform: scale(1.5);         /* Standard syntax */
}
```

-----

## 2D Transforms

2D transforms operate on a flat plane, using the **x-axis (horizontal)** and **y-axis (vertical)**.

### Rotate

The `rotate()` function rotates an element from its `transform-origin` (the center, by default). Positive values rotate clockwise, while negative values rotate counter-clockwise.

  * **HTML**
    ```html
    <figure class="box-1">Box 1</figure>
    <figure class="box-2">Box 2</figure>
    ```
  * **CSS**
    ```css
    .box-1 {
      transform: rotate(20deg);
    }
    .box-2 {
      transform: rotate(-55deg);
    }
    ```

### Scale

The `scale()` function resizes an element. A value greater than `1` makes it larger, while a value between `0` and `1` makes it smaller.

You can scale the axes independently with `scaleX()` and `scaleY()` or together with `scale(X, Y)`.

  * **HTML**
    ```html
    <figure class="box-1">Box 1</figure>
    <figure class="box-2">Box 2</figure>
    <figure class="box-3">Box 3</figure>
    ```
  * **CSS**
    ```css
    .box-1 {
      transform: scaleX(0.5); /* Half the width */
    }
    .box-2 {
      transform: scaleY(1.15); /* 15% taller */
    }
    .box-3 {
      transform: scale(0.5, 1.15); /* Shorthand for both */
    }
    ```

### Translate

The `translate()` function moves an element from its current position without disrupting the normal flow of the document, similar to relative positioning. You can use `translateX()`, `translateY()`, or the `translate(X, Y)` shorthand.

Positive values move the element right and down; negative values move it left and up.

  * **HTML**
    ```html
    <figure class="box-1">Box 1</figure>
    <figure class="box-2">Box 2</figure>
    <figure class="box-3">Box 3</figure>
    ```
  * **CSS**
    ```css
    .box-1 {
      transform: translateX(-10px);
    }
    .box-2 {
      transform: translateY(25%);
    }
    .box-3 {
      transform: translate(-10px, 25%);
    }
    ```

### Skew

The `skew()` function distorts an element along the x and y axes. Values are typically provided in degrees (`deg`).

  * **HTML**
    ```html
    <figure class="box-1">Box 1</figure>
    <figure class="box-2">Box 2</figure>
    <figure class="box-3">Box 3</figure>
    ```
  * **CSS**
    ```css
    .box-1 {
      transform: skewX(5deg);
    }
    .box-2 {
      transform: skewY(-20deg);
    }
    .box-3 {
      transform: skew(5deg, -20deg);
    }
    ```

-----

## Combining Transforms

You can apply multiple transform functions in a single declaration by listing them in order, separated by spaces. The order matters\!

```css
.box-1 {
  transform: rotate(25deg) scale(0.75);
}
.box-2 {
  transform: translateX(20px) skew(10deg, 20deg);
}
```

-----

## Transform Origin

The `transform-origin` property changes the location of the point around which a transformation is applied. The default is `50% 50%` (the center of the element).

It accepts keyword values (`top`, `left`, `bottom`, `right`, `center`) or length/percentage values for the x and y axes.

```css
.box-1 {
  transform: rotate(15deg);
  transform-origin: 0 0; /* Same as 'top left' */
}
.box-2 {
  transform: scale(0.5);
  transform-origin: 100% 100%; /* Same as 'bottom right' */
}
```

**Note:** Since both `transform: translate()` and `transform-origin` can affect an element's position, be mindful of how they might interact or conflict.

-----

## 3D Transforms

3D transforms add a third dimension: the **z-axis**, which represents depth. An element can now be moved closer to or further from the viewer.

### Creating a 3D Space: The `perspective` Property

To activate a 3D space, you must first apply the `perspective` property. This property defines how much "depth" is present. You can apply it to the element being transformed or, more commonly, to its parent element to create a shared 3D space for multiple children.

  * A **lower value** creates a more dramatic, close-up perspective.
  * A **higher value** creates a more subtle, far-away perspective.

<!-- end list -->

```css
/* Applied to a parent container */
.group {
  perspective: 400px;
}
.box {
  transform: rotateX(45deg);
}
```

### Perspective Origin

Just like `transform-origin`, the `perspective-origin` property sets the vanishing point for the 3D scene. The default is `50% 50%`.

```css
.container {
  perspective: 200px;
  perspective-origin: 20px 40px; /* Changes the vanishing point */
}
```

### 3D Rotate

You can rotate an element around any of the three axes using `rotateX()`, `rotateY()`, and `rotateZ()`. `rotateZ()` is equivalent to the standard 2D `rotate()`.

```css
.box-1 {
  transform: perspective(200px) rotateX(45deg);
}
.box-2 {
  transform: perspective(200px) rotateY(45deg);
}
```

### 3D Scale

The `scaleZ()` function scales an element along the z-axis, which can affect its perceived depth when combined with other 3D transforms like rotation.

```css
.box-1 {
  transform: perspective(200px) scaleZ(2) rotateX(45deg);
}
```

### 3D Translate

The `translateZ()` function moves an element along the z-axis. A **positive value pulls it closer** (making it appear larger), and a **negative value pushes it away** (making it appear smaller).

```css
.box-1 {
  transform: perspective(200px) translateZ(-50px); /* Pushes away */
}
.box-2 {
  transform: perspective(200px) translateZ(50px);  /* Pulls closer */
}
```

**Note:** Skew is exclusively a 2D transform; you cannot `skewZ()`.

-----

## Advanced 3D Properties

### `transform-style`

When you have a transformed element nested inside another transformed element, the `transform-style` property is crucial. It must be placed on the parent element.

  * `flat` (default): Nested elements are flattened into the parent's 2D plane.
  * `preserve-3d`: Allows nested elements to exist in their own 3D space, creating a true hierarchical 3D scene.

<!-- end list -->

```css
.parent {
  perspective: 500px;
  transform: rotateY(45deg);
  transform-style: preserve-3d; /* Allows child to be 3D */
}
.child {
  transform: rotateX(15deg) translateZ(20px);
}
```

### `backface-visibility`

By default, when you rotate an element 180 degrees, you see its "back side," which is a mirrored version of its front. The `backface-visibility` property allows you to control this.

  * `visible` (default): The back side is visible.
  * `hidden`: The element becomes invisible when its back is facing the viewer.

<!-- end list -->

```css
.card-flipper {
  backface-visibility: hidden;
  transform: rotateY(180deg);
}
```

-----

## Demo: Building a 3D Cube

This example combines `perspective`, `translateZ`, `rotateX`, `rotateY`, and `transform-style` to create a 3D cube.

  * **HTML**
    ```html
    <div class="cube-container">
      <div class="cube">
        <figure class="side front">1</figure>
        <figure class="side back">2</figure>
        <figure class="side left">3</figure>
        <figure class="side right">4</figure>
        <figure class="side top">5</figure>
        <figure class="side bottom">6</figure>
      </div>
    </div>
    ```
  * **CSS**
    ```css
    .cube-container {
      width: 200px;
      height: 200px;
      perspective: 600px;
    }
    .cube {
      width: 100%;
      height: 100%;
      position: relative;
      transform-style: preserve-3d;
      transform: translateZ(-100px); /* Pushes the cube's center back */
    }
    .side {
      position: absolute;
      width: 200px;
      height: 200px;
      border: 2px solid #2db34a;
      background: rgba(45, 179, 74, .3);
    }
    .front  { transform: rotateY(0deg) translateZ(100px); }
    .back   { transform: rotateY(180deg) translateZ(100px); }
    .right  { transform: rotateY(90deg) translateZ(100px); }
    .left   { transform: rotateY(-90deg) translateZ(100px); }
    .top    { transform: rotateX(90deg) translateZ(100px); }
    .bottom { transform: rotateX(-90deg) translateZ(100px); }
    ```

-----

## Revision: Q\&A 🧠

Here are some questions to test your knowledge.

\<details\>
\<summary\>\<strong\>Q1:\</strong\> What is the main purpose of the CSS \<code\>transform\</code\> property?\</summary\>
\<strong\>A:\</strong\> To move, rotate, scale, and skew elements in 2D or 3D space without affecting the document's layout flow.
\</details\>

\<details\>
\<summary\>\<strong\>Q2:\</strong\> Why should the standard \<code\>transform\</code\> property be listed last after vendor-prefixed versions?\</summary\>
\<strong\>A:\</strong\> To ensure that if a browser supports the standard syntax, it will override the older, prefixed versions. It's a best practice for forward compatibility.
\</details\>

\<details\>
\<summary\>\<strong\>Q3:\</strong\> What is the difference between \<code\>transform: rotate(45deg)\</code\> and \<code\>transform: rotate(-45deg)\</code\>?\</summary\>
\<strong\>A:\</strong\> \<code\>rotate(45deg)\</code\> rotates the element 45 degrees clockwise. \<code\>rotate(-45deg)\</code\> rotates it 45 degrees counter-clockwise.
\</details\>

\<details\>
\<summary\>\<strong\>Q4:\</strong\> An element has \<code\>transform: scale(2)\</code\>. How does this differ from \<code\>transform: scale(0.5)\</code\>?\</summary\>
\<strong\>A:\</strong\> \<code\>scale(2)\</code\> doubles the size of the element. \<code\>scale(0.5)\</code\> reduces the size of the element by half.
\</details\>

\<details\>
\<summary\>\<strong\>Q5:\</strong\> What is the default \<code\>transform-origin\</code\> of an element?\</summary\>
\<strong\>A:\</strong\> The default is \<code\>50% 50%\</code\>, which is the exact center of the element.
\</details\>

\<details\>
\<summary\>\<strong\>Q6:\</strong\> To create a 3D scene, what CSS property is essential?\</summary\>
\<strong\>A:\</strong\> The \<code\>perspective\</code\> property. It must be applied either to the transformed element or its parent to create a 3D space and give a sense of depth.
\</details\>

\<details\>
\<summary\>\<strong\>Q7:\</strong\> What does \<code\>transform-style: preserve-3d;\</code\> accomplish?\</summary\>
\<strong\>A:\</strong\> It allows a transformed child element to exist in its own 3D space, relative to its parent. Without it, the child element would be flattened into the parent's 2D plane.
\</details\>

\<details\>
\<summary\>\<strong\>Q8:\</strong\> How would you make an element disappear when its back is facing the camera?\</summary\>
\<strong\>A:\</strong\> By applying \<code\>backface-visibility: hidden;\</code\> to the element.
\</details\>
