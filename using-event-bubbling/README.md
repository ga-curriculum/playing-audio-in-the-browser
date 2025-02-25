<h1>
  <span class="headline">Playing Audio in the Browser</span>
  <span class="subhead">Using Event Bubbling</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to effectively apply JavaScript classes and event bubbling concepts to enhance interactivity in web applications.

In the **`💪 You Do`** in this lesson, you were tasked with using the JavaScript built-in `Audio` class to add sounds to the remaining images.

You could have repeated the same process by hard-coding cached element references for each and every image on the page, but that wouldn't be very **DRY**.

Let's use what we've learned about DOM manipulation to have JavaScript do all the work for us!

Start by adding a cached element reference for the  **`<div id="notCat">` 'container' element**:

```js
const notCatDiv = document.querySelector("#not-cat")
```

Then, we'll add an event listener to it! Because of *event-bubbling*, if we attach an event handler to an element, any time we click *any* of the elements within, our callback function will be executed!  

```js
notCatDiv.addEventListener("click", (evt) => {
  if (evt.target.id !== "cat") {
    const audioElement = new Audio(`../assets/audio/${evt.target.id}.mp3`)
    audioElement.volume = .05
    audioElement.play()
  }
})
```

> 🧠 The reason we're able to do this is because we named the audio files using the same exact spelling/casing as the `id` values for each of the images! As a result, we're able to dynamically associate the two. 

