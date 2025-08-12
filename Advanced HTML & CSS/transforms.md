# Transform
CSS3 transform property allows you to declare the size, position and even change the elements found in setting two-dimensional or three dimensional objects with individual values. How the browser can support these prefixes, especially on Chrome.

## Transform Syntax
The syntax for transform varys depending on the browser/vendor.

div {
-webkit-transform: scale(1.5);
     -moz-transform: scale(1.5);
       -o-transform: scale(1.5);
          transform: scale(1.5);
}
These declarations comes last to overwrite the prefixed versions, should  browser fully support the transform property.

## 2D Transforms
Link: https://www.css3files.com/transform/
Two-dimensional or three dimensional plane. 
Rememeber that while two dimensional works on the x and y axes (horizontal and vertical) Three dimensions use x and y plus a z axes to define the length and width but also the depth.

<h3 style="color:green;"> 2D Rotate </h3>

