## CSS Variables 

```
<div class="controls">
  <label for="spacing">Spacing:</label>
  <input id="spacing" type="range" name="spacing" min="10" max="200" value="10" data-sizing="px">

  <label for="blur">Blur:</label>
  <input id="blur" type="range" name="blur" min="0" max="25" value="10" data-sizing="px">

  <label for="base">Base Color</label>
  <input id="base" type="color" name="base" value="#ffc600">
</div>
```

NodeList vs Array:

NodeList has less methods on it, Array has the usual higher order functions that we are use to

type="range" is the bar

name="blur" is the variable of the css

data-sizing="px" is an attribute created by the user

```
:root {
  --base: #ffc600;
  --spacing: 10px;
  --blur: 10px
}
```

root highest level of declaration similar to the HTML element
:root {
  --base
  --spacing
  --blur
  are all the variable names with initial values
} 

```
img {
  padding: var(--spacing);
  background: var(--base);
  filter: blur(var(--blur));
}
```

set up the img tag and to use the variable, var() is needed along with --spacing (which is the proper way of declaring it, stanard in CSS)

```
const inputs = document.querySelectorAll('.controls input');

function handleUpdate() {
  const suffix = this.dataset.sizing || '';
  document.documentElment.style.setProperty(`--${this.name}`, this.value + suffix);
}

inputs.forEach(input => input.addEventlistener('change', handleUpdate));
inputs.forEach(input => input.addEventListener('mousemove', handleUpdate));
```

grab all the inputs using the querySelectorAll('.controls input');

create a function for handleUpdate();
- this.dataset is an object that has all the data-<whatever> return so we can have data stored in the element

- document.documentElement returns the element that is the root element of the document
after we set the propety of the style with document.doucmentElement.style.setProperty(`--${this.name}`, this.value + suffix);

afterwards loop over the inputs add and event listner for change, using the handleUpdate
loop over the inputs one more time for mousemove with handleUpdate
