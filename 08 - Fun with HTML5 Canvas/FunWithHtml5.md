# Fun with HTML5 Canvas

The new canvas can be render as 3d or 2d;
- First grab the canvas with d.querySelector('#draw')
- Second get the context with canvas.getContext('2d')
- Third, change the canvas size to the width and height of the client

```
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
```

strokeStyle 
  is the color of the stroke

lineCap
  how the endopints of every line are drawn
  there are: butt, round, square

lineJoin
  determines how two connectin segments (of lines, arcs or curves) with non-zero lengths in a shape are joined together

Need to add event listener with
  - mousedown to start and grab the X, Y values and isDrawing true
  - mouseup to change isDrawing to false
  - mouseout => isDrawing to false;
  - mousemove, draw

```
  function draw(e) {
    if (!isDrawing) return;
    ctx.strokeStyle = `hsl(${hue}, 100%, 50%)`;
    ctx.lineStyle = hue;
    ctx.beginPath();
    ctx.moveTo(lastX, lastY);
    ctx.lineTo(e.offsetX, e.offsetY);
    ctx.stroke();
    [lastX, lastY] = [e.offsetX, e.offsetY];
    hue++;
    if (hue >= 360) {
      hue = 0;
    }

    if (ctx.lineWidth >= 100 || ctx.lineWidth <= 1) {
      lineDirection = !lineDirection;
    }

    lineDirection ? ctx.lineWidth++ : ctx.lineWidth--;
  }
```

