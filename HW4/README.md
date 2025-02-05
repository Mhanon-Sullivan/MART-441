Like last week, I'm having so much fun with this whole "choose your own adventure" thing. Putting it together has been challenging, but in the most fun way you can imagine. I enjoyed switching up the color palette and some of the pictures, as well as updating the story a bit.

ChatGPT was very handy in helping me fix a few bugs this week. In the middle of working, my DOM just completely stopped updating itself after making choices and I had no idea why. As it turns out, I accidentally deleted the single line of code that resets the DOM and I didn't even realize. ChatGPT saved me hours of panicking, hooray!

I'd also like to not that I have a function with a for loop - it logs something in the console everytime you hit the restart button -- and I'm pretty sure that satisfies both the "have at least one function return a value" and the "use a loop" requirements. If it doesn't please let me know! I really didn't know what else to do for those.

It also helped me with a minor issue I was having with input capitalization. I wanted the user to always enter lowercase so the code would accept it, but that seemed inconvenient to the user. As it turns out, there's a little tag (.value.toLowerCase()) that I can put on the end of the input code that automatically turns any character inputed into lowercase, so I don't have to worry about it! You can use whatever casing an it will still work. That will be very useful in future projects. I wish I'd known about it sooner!

Once I was done with my project, I asked it to create a similar piece using the instructions from weeks 3 and 4. It put out what you see down below. I think it's a little complicated, but it certainly did what it was asked! However, I can't actually open it in a browser to test it because it seems to be filled with errors. Whether that's due to me not having everything organized into separate text files or what, it seems very broken. Mine isn't, though! Yay!

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Choose Your Adventure</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f0f8ff;
            color: #333;
            text-align: center;
            padding: 20px;
        }

        h1 {
            color: #8b0000;
        }

        #story {
            margin: 20px 0;
        }

        #choices {
            display: flex;
            justify-content: center;
            gap: 10px;
        }

        button {
            padding: 10px 20px;
            background-color: #8b0000;
            color: white;
            border: none;
            cursor: pointer;
        }

        button:hover {
            background-color: #a52a2a;
        }
    </style>
</head>
<body>
    <h1>Choose Your Adventure</h1>
    <div id="story"></div>
    <div id="choices"></div>
    <button onclick="restartStory()">Restart</button>

    <script>
        let storyState = {};

        function startStory() {
            storyState = {
                step: 1
            };
            showStory();
        }

        function showStory() {
            const storyElement = document.getElementById('story');
            const choicesElement = document.getElementById('choices');
            choicesElement.innerHTML = '';

            if (storyState.step === 1) {
                storyElement.innerText = 'You find yourself in a dark forest. There are two paths ahead.';
                createChoice('Take the left path', () => {
                    storyState.step = 2;
                    showStory();
                });
                createChoice('Take the right path', () => {
                    storyState.step = 3;
                    showStory();
                });
            } else if (storyState.step === 2) {
                storyElement.innerText = 'You encounter a wild bear! Do you fight or run?';
                createChoice('Fight', () => {
                    storyState.step = 4;
                    showStory();
                });
                createChoice('Run', () => {
                    storyState.step = 5;
                    showStory();
                });
            } else if (storyState.step === 3) {
                storyElement.innerText = 'You find a treasure chest. Do you open it or leave it?';
                createChoice('Open it', () => {
                    storyState.step = 6;
                    showStory();
                });
                createChoice('Leave it', () => {
                    storyState.step = 7;
                    showStory();
                });
            } else if (storyState.step === 4) {
                storyElement.innerText = 'You fight the bear and win!';
                createChoice('Restart', restartStory);
            } else if (storyState.step === 5) {
                storyElement.innerText = 'You run away safely.';
                createChoice('Restart', restartStory);
            } else if (storyState.step === 6) {
                storyElement.innerText = 'The chest is full of gold!';
                createChoice('Restart', restartStory);
            } else if (storyState.step === 7) {
                storyElement.innerText = 'You walk away, never knowing what was inside.';
                createChoice('Restart', restartStory);
            }
        }

        function createChoice(text, action) {
            const choiceButton = document.createElement('button');
            choiceButton.innerText = text;
            choiceButton.onclick = action;
            document.getElementById('choices').appendChild(choiceButton);
        }

        function restartStory() {
            startStory();
        }

        startStory();
    </script>
</body>
</html>
