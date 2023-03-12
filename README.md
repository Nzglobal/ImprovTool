# ImprovTool
Practive your improv skills with a basic website which will provide you random topics based on a timer.

This website displays random topics and images every few seconds. It uses two APIs: one to generate random nouns and another to fetch related images from Unsplash. It also has a semi transparent div behind the header and text to make them more legible.

## How to use

To use this website, simply open the index.html file in your browser. You can also change the frequency of updating the topics by adding a query parameter `t` to the URL. For example, if you want to update the topics every 10 seconds, you can use `index.html?t=10`.

## How it works

This website uses HTML, CSS and JavaScript to create a simple webpage with some style and interactivity. The main logic is in the script tag in the head section of the HTML file. It defines two functions: `fetchRandomTopics` and `updateText`.

The `fetchRandomTopics` function uses the Fetch API to get data from a random noun API (https://random-word-form.herokuapp.com/random/noun) and then displays the noun on the webpage using `document.getElementById("topic").innerHTML`. It also uses another Fetch API call to get a random image related to the noun from Unsplash (https://source.unsplash.com/random/?) and then sets it as the background image of the body using `document.body.style.backgroundImage`.

The `updateText` function gets the value of x from the query parameter t using `new URL(window.location.href).searchParams.get("t")`. If x is not a valid number or less than or equal to zero, it uses a default value of 5 seconds. It then calls `fetchRandomTopics` once at the beginning and sets an interval to call it again every x seconds using `setInterval(fetchRandomTopics,x *1000 )`.

The style tag in the head section of the HTML file defines some style for the webpage using CSS. It sets some font properties for the body, h1 and p elements. It also adds a semi transparent div behind the header and text using `position: relative`, `width:80%`, `margin:auto`, `background-color: rgba(255,255,255,0.5)` and some flexbox properties (`display:flex`, `flex-direction:column`, `justify-content:center`, `align-items:center`, `min-height:80vh`).

The body tag in the HTML file contains a div element that wraps around an h1 element with "Random Topics" as its text content and a p element with an id of "topic" that will display the random noun. It also has an onload attribute that calls the updateText function when the page loads.
