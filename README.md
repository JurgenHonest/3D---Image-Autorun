# 3D - Image AutoRun
  --https://sumit-3dimagesautorun.netlify.app/

  ## A very basic HTML code using:
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
## The CSS is the main work; without the help of js at all:
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
The :after (or ::after) pseudo-selector inserts content after the content of an element, but it's still inside the element itself.
You can use content: "" to add empty content or insert text using content: "some text".
It’s often used for decorative purposes like adding icons, styling, or underlining effects.
Example:
css
Copy code
h1::after {
  content: "!";
  color: red;
}
In your code, ::after is used to create a stroked outline of the text by duplicating the content with content: attr(data-content) and using -webkit-text-stroke to add an outline.
### 2. -webkit:
-webkit is a CSS vendor prefix that targets WebKit-based browsers (such as Chrome and Safari) to ensure certain styles work properly.
It’s often used for experimental or non-standard features in CSS, like gradients, transitions, or text effects.
Example in your code: -webkit-text-stroke adds an outline to text.
css
Copy code
-webkit-text-stroke: 2px #d2d2d2;
### 3. @keyframes:
@keyframes defines an animation sequence that specifies how elements should change styles at various stages (or "keyframes") of the animation.
You define the start (from) and end (to) or intermediate steps (0%, 50%, etc.), then use the animation name in the element’s CSS to apply the animation.
Example:
css
Copy code
@keyframes rotate {
  from { transform: rotate(0deg); }
  to { transform: rotate(360deg); }
}
In your code, autorun creates a smooth 360-degree rotation of the slider.
### 4. transform:
transform applies transformations to elements such as moving, rotating, scaling, or skewing them.
Transformations don’t affect the document flow and can work in 2D (e.g., rotate(45deg), translateX(100px)) or 3D (e.g., rotateY(360deg), perspective(1000px)).
```
transform: perspective(1000px) rotateY(360deg)
```
This code creates the 3D rotation effect for the slider.

### 5. repeating-linear-gradient:
a. The "repeating-linear-gradient" creates a linear gradient pattern that repeats at a specified interval.<br>
b. You specify the direction (e.g., to right, to bottom), then define color stops that repeat.
```
background-image: repeating-linear-gradient(
      to right,
      transparent 0 100px,
      #25283b22 100px 101px
    );
```
