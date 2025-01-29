Hi! I had a lot of fun with this week's assignment. This kind of creative writing is always so entertaining. I could've done that part for hours. One challenge I had this week was with figuring out how to reset the button text after you press one of the buttons. With a lot of Googling, I eventually got to what you see in the project. Hooray for research!

I just started my screenwriting class, too, so I have Courier New on the brain. You'll find that here!

Anyways, you can find the ChatGPT version of the homework down below.

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Choose Your Adventure</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div id="app">
    <h1 id="title">Choose Your Own Adventure</h1>
    <p id="story">You stand at a crossroads. Where do you go?</p>
    <div id="choices">
      <button onclick="choosePath(1)">Enter the forest</button>
      <button onclick="choosePath(2)">Follow the river</button>
    </div>
  </div>

  <script>
    function choosePath(choice) {
      const storyElement = document.getElementById('story');
      
      if (choice === 1) {
        storyElement.textContent = "You enter the forest and find a mysterious cabin.";
        document.getElementById('choices').innerHTML = `
          <button onclick="choosePath(3)">Enter the cabin</button>
          <button onclick="choosePath(4)">Walk past it</button>`;
      } else if (choice === 2) {
        storyElement.textContent = "You follow the river and find a small boat.";
        document.getElementById('choices').innerHTML = `
          <button onclick="choosePath(5)">Take the boat</button>
          <button onclick="choosePath(6)">Keep walking</button>`;
      } else {
        storyElement.textContent = "Your adventure ends here.";
        document.getElementById('choices').innerHTML = "";
      }
    }
  </script>
</body>
</html>

As you can see, it certainly gets the job done. It seems a little lacking in terms of choices, and it also doesn't have sound. All of the options seem to lead to the same ending, which I think is kind of boring. It didn't even try with images! I find it ironically hilarious that ChatGPT immediately did with reseting the buttons what I had to read about for two hours. Oh well. I think mine final product is way more fun and detailed!