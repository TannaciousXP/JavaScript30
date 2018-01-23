## JS CLOCK AND CSS

start off with 

```
<div class="clock">
  <div class="clock-face">
    <div class="hand hour-hand"></div>
    <div class="hand min-hand"></div>
    <div class="hand second-hand"></div>
  </div>
</div>
```

one block and three 3 hands

next we wanted to go to the stying of hand

transform-origin:
Allows you to change the position of transformed elements
2D transformations can change like x- and y-axiss of an element. 3D transformations can also change the z-axis of an element.
We want to change it at the X-axis
- transform-origin: 100%;

transform: rotate(90deg);
Want to start the hands at 12PM

transition: all 0.5s;
the amoutn of time to transition

transition-timing-function: cubic-bezier(0.1, 2.7, 0.58, 1);
The transition-timing-function property sepecifies the speed curve of the transition effect

```
const secondHand = document.querySelector('.second-hand');
const minsHand = document.querySelector('.min-hand');
const hourHand = document.querySelector('.hour-hand');
```

grabs the second, mins, hour Hand using dcument.querySelector

```
const d = document;
const secHand = d.querySelector('.second-hand');
const minHand = d.querySelector('.min-hand');
const hourHand = d.querySelector('.hour-hand');

function setDate() {
  const now = new Date();
  const seconds = now.getSeconds();
  const secDegrees = ((seconds / 60) * 360) + 90;
  secHand.style.transform = `rotate(${secDegrees}deg)`
  
  const mins = now.getMinutes();
  const minsDegrees = ((mins / 60) * 360) + ((seconds / 60) * 6) + 90;
  minHand.style.transform = `rotate(${minsDegrees}deg)`;

  const hour = now.getHours();
  const hourDegrees = ((hour / 12) * 360) + ((mins / 60) * 30) + 90;
  hourHand.style.transform = `rotate(${hourDegrees}deg)`;
}

setInterval(setDate, 1000);

```
get the date with const now = new Date()

get the seconds with = now.getSeconds();
get the degree with ((seconds/60) * 360) + 90
[there are 60 seconds in a minute, 360 degress in a full circle, +90 because we offset the starting position]

get the mins with = now.getMinutes();
get the degree with ((mins/60) * 360) + ((seconds/60) * 6) + 90;
[samething as above, but we want to be more accurate so we have seconds/60 * 6 because 360/60 = 6]

get the hours = now.getHours();
get degree with((hours/12) * 360) + ((mins/60) * 30) + 90
same as minutes, but we have (mins/60 * 30) because 360/12 = 30;