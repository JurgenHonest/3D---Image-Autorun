
# 3D - Image AutoRun
  --https://sumit-3dimagesautorun.netlify.app/<br><bt>
#### The Image Autorun project is bring together only with the help of HTML and CSS without javascript at all.
  ## A very basic HTML code is used:
  ```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>3D - Image Slider</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="main">
      <div class="slider" style="--quantity: 10">
        <div class="items" style="--position: 1">
          <img src="./images/cinder.jpg" alt="" />
        </div>
        <div class="items" style="--position: 2">
          <img src="./images/akuma.jpg" alt="" />
        </div>
        <div class="items" style="--position: 3">
          <img src="./images/berserk.jpg" alt="" />
        </div>
        <div class="items" style="--position: 4">
          <img src="./images/casca.jpg" alt="" />
        </div>
        <div class="items" style="--position: 5">
          <img src="./images/darksouls.jpg" alt="" />
        </div>
        <div class="items" style="--position: 6">
          <img src="./images/tekken8.jpg  " alt="" />
        </div>
        <div class="items" style="--position: 7">
          <img src="./images/souls.webp" alt="" />
        </div>
        <div class="items" style="--position: 8">
          <img src="./images/wallpaper.webp" alt="" />
        </div>
        <div class="items" style="--position: 9">
          <img src="./images/guts.jpg" alt="" />
        </div>
        <div class="items" style="--position: 10">
          <img src="./images/goblin slayer.jpg" alt="" />
        </div>
      </div>
      <div class="container">
        <h1 data-content="Dark Potrayal">Dark Potrayal</h1>
        <div class="artist">
          <h2>Sumit Chhetri</h2>
          <p><b>Dastardly Colossal</b></p>
        </div>
        <div class="model"></div>
      </div>
    </div>
  </body>
</html>
```
## The CSS is the main work:
```

@import url("https://fonts.cdnfonts.com/css/ica-rubrik-black");
@import url("https://fonts.cdnfonts.com/css/poppins");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  height: 100%;
  width: 100%;
  background-color: #dadada;
  background-image: repeating-linear-gradient(
      to right,
      transparent 0 100px,
      #25283b22 100px 101px
    ),
    repeating-linear-gradient(
      to bottom,
      transparent 0 100px,
      #25283b22 100px 101px
    );
}
.main {
  width: 100%;
  height: 100vh;
  text-align: center;
  text-align: center;
  overflow: hidden;
  position: relative;
}
.main .slider {
  position: absolute;
  width: 180px;
  height: 220px;
  top: 10%;
  left: calc(50% - 100px);
  transform-style: preserve-3d;
  transform: perspective(1000px);
  animation: autorun 20s linear infinite;
  z-index: 9;
}
@keyframes autorun {
  from {
    transform: perspective(1000px) rotateX(-10deg) rotateY(0deg);
  }
  to {
    transform: perspective(1000px) rotateX(-10deg) rotateY(360deg);
  }
}
.main .slider .items {
  position: absolute;
  inset: 0 0 0 0;
  transform: rotateY(
      calc((var(--position) - 1) * (360 / var(--quantity)) * 1deg)
    )
    translateZ(550px);
}
.main .slider .items img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}
.main .container {
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: min(1400px, 100vw);
  height: max-content;
  padding-bottom: 100px;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
}
.main .container h1 {
  font-family: "Ica Rubrik";
  font-size: 8.5rem;
  line-height: 1.5rem;
  color: #252838;
  position: relative;
}
.main .container h1::after {
  position: absolute;
  inset: 0 0 0 0;
  content: attr(data-content);
  z-index: 3;
  -webkit-text-stroke: 2px #d2d2d2;
  color: transparent;
}
.main .container .artist {
  font-family: Poppins;
  text-align: right;
  max-width: 200px;
}
.main .container h2 {
  font-size: 1.5rem;
}
.main .container .model {
  background-image: url(./images/Alexander.png);
  width: 100%;
  height: 80vh;
  position: absolute;
  bottom: 0;
  left: 0;
  background-size: auto 130%;
  background-repeat: no-repeat;
  background-position: top center;
}

```
## Very confusing or bewitching features of CSS:
### 1. :after Pseudo-Selector:
a.&nbsp; The :after (or ::after) pseudo-selector inserts content after the content of an element, but it's still inside the element itself.<br>
b.&nbsp; You can use content: "" to add empty content or insert text using content: "some text".
c.&nbsp; It’s often used for decorative purposes like adding icons, styling, or underlining effects.
```
h1::after {
  content: "";
  color: red;
}
```
In the above code,&nbsp; ::after is used to create a stroked outline of the text by duplicating the content with content: attr(data-content) and using -webkit-text-stroke to add an outline.
### 2. -webkit:
a.&nbsp; The "-webkit" is a CSS vendor prefix that targets WebKit-based browsers (such as Chrome and Safari) to ensure certain styles work properly.<br>
b.&nbsp; It’s often used for experimental or non-standard features in CSS, like gradients, transitions, or text effects.
"-webkit-text-stroke" adds an outline to text.
```
   -webkit-text-stroke: 2px #d2d2d2;
```
### 3. @keyframes:
a.&nbsp; "@keyframes" defines an animation sequence that specifies how elements should change styles at various stages (or "keyframes") of the animation.<br>
b.&nbsp; You define the start (from) and end (to) or intermediate steps (0%, 50%, etc.), then use the animation name in the element’s CSS to apply the animation.
```
@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
```
In above code, autorun creates a smooth 360-degree rotation of the slider.
### 4. transform:
a.&nbsp; The "transform" applies transformations to elements such as moving, rotating, scaling, or skewing them.<br>
b.&nbsp; Transformations don’t affect the document flow and can work in 2D (e.g., rotate(45deg), translateX(100px)) or 3D (e.g., rotateY(360deg), perspective(1000px)).
```
   transform: perspective(1000px) rotateY(360deg)
```
This code creates the 3D rotation effect for the slider.

### 5. repeating-linear-gradient:
a.&nbsp; The "repeating-linear-gradient" creates a linear gradient pattern that repeats at a specified interval.<br>
b.&nbsp; You specify the direction (e.g., to right, to bottom), then define color stops that repeat.
```
    background-image: repeating-linear-gradient(
      to right,
      transparent 0 100px,
      #25283b22 100px 101px
    );
```
### 6. i. The attr() function:
a.&nbsp; It is used to access an HTML attribute value and insert it into the CSS.<br>
b.&nbsp; It is commonly applied within the content property of ::before or ::after pseudo-elements.<br>
c.&nbsp; This is useful when you want to display the content of a custom attribute (e.g., data-* attributes) in your CSS without modifying the HTML directly.
```
  content: attr(data-content);
```
### 6. ii. data-content Attribute:
a.&nbsp; "data-" attributes are custom attributes that developers can add to any HTML element to store extra data that can be accessed via JavaScript or CSS.<br>
b.&nbsp; In above case, data-content="Dark Portrayal" is added to an HTML element like h1 to store the text "Dark Portrayal".
```
.main .container h1::after {
  content: attr(data-content);
  z-index: 3;
  -webkit-text-stroke: 2px #d2d2d2;
  color: transparent;
}
```
