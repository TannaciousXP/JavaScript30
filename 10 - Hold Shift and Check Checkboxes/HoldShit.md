# HoldShit

```
const checkboxes = document.querySelectorAll('.inbox input[type="checkbox"]');
```

input[type="checkbox"]
takes grabs the node input and checks to see if the type is equal to checkbox

STEPS:
- get all the checkboxes with querySelectAll('.inbox input[type="checkbox"]')
- have a variable for lastKey
- create a function for handleClick
  * create a variable for inBetween
  * conditional for e.shiftKey && this.checked
    loop over checkboxes
    conditional for check === this or checkbox === lastChecked
    true: inBetween is equal to !inBetween
  * conditional for inBetween
    true: checkbox.checked = true;
- lastKey = this;
- iterate over checboxes and addEventListener('click', function);