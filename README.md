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
