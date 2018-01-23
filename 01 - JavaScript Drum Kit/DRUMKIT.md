## First Look

Within the body, the structure is

```
<div class="keys">
  <div data-key="65" class="key">
  <kbd>A</kbd>
  <span class="sound">clap</span>
  </div>
  etc...
</div>
```

- <kbd> is a tag they set up in style.css
- "data-key" is a custom data attributes which are intended to store custom data private to the page or application, for which they are no more appropriate attributes or elements

```
function removeTransition(e) {
  if (e.propertyName !== 'transform') return;
  e.target.classList.remove('playing');
}
```

document.querySelector('')
return the first Element within the document that matches the specified selector, or a group of selectors, or null if no matches are found
- select the div that has the right keyCode (data-key) associated with key pressed

e.propertyName
returns the name of the CSS propety associated with transition, when a transitionevent occurs (read-only)
- if the there is no propertyName "transform" return
- else remove class "playing" with e.target.classList.remove('playing');

```
function playSound(e) {
  const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`);
  const key = document.querySelector(`div[data-key="${e.keyCode}']`);
  if (!audio) return;

  key.classList.add('playing');
  audio.currentTime = 0;
  audio.play();
}
```

audio = get the audio element by the key press with e.keyCode
key = get the div element by the key press with e.keyCode

add the class name playing
audio.currentTime = 0 means set the current playback position in an audio to 0 seconds
audio.play() = starts playing the audio

```
const keys = Array.from(document.querySelectorAll('.key'));
keys.forEach(key => key.addEventListenter('transitionend', removeTransition));
window.addEventListener('keydown', playsound);
```

keys return an array of elements with document querySelectorAll('.key') then you want to loop over it to add an eventListener 