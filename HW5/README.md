Hi! This week's homework certainly gave me some trouble! Specifically, I had an absolutely horrid time trying to figure out how to get the images to disappear again if a match wasn't made. With some questions shot towards ChatGPT, I found out that I can actually add classes to to the cards with a click event! So when the images are both clicked, the class "matched" will be added to both if they are the same image source, which will keep them on screen. If this class is not applied (because the images don't match), it will remain in the "hidden" class and disappear. It was very helpful!

When I was finished, I asked ChatGPT to do the assignment. You'll see what it gave me down below. Overall, it's kind of confusing to look at. The for loops confuse me. It works, though! Color-wise, it's boring. Perhaps I'm simply bias to color design, but ChatGPT always generates to most visually boring stuff! Mine is very pink, and has personalized images (Verosika Mayday from Helluva Boss, if you were wondering).

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Memory Matching Game</title>
    <style>
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.game-board {
    display: grid;
    grid-template-columns: repeat(4, 100px);
    grid-gap: 10px;
    justify-content: center;
}

.card {
    width: 100px;
    height: 100px;
    background-color: #ddd;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
}

.card img {
    width: 80%;
    display: none;
}
    </style>
</head>
<body>
    <div class="game-board" id="gameBoard"></div>
    <script
    const images = [
    'image1.jpg', 'image2.jpg', 'image3.jpg', 'image4.jpg', 
    'image5.jpg', 'image6.jpg', 'image1.jpg', 'image2.jpg',
    'image3.jpg', 'image4.jpg', 'image5.jpg', 'image6.jpg'
];

const gameBoard = document.getElementById('gameBoard');

// Shuffle function to randomize image placement
function shuffleArray(array) {
    for (let i = array.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [array[i], array[j]] = [array[j], array[i]];
    }
}

// Create cards and display them on the board
function createGameBoard() {
    shuffleArray(images);
    for (let i = 0; i < images.length; i++) {
        const card = document.createElement('div');
        card.classList.add('card');
        const img = document.createElement('img');
        img.src = images[i];
        card.appendChild(img);
        card.addEventListener('click', () => revealImage(card, img));
        gameBoard.appendChild(card);
    }
}

// Reveal image when the card is clicked
function revealImage(card, img) {
    if (!card.classList.contains('flipped')) {
        img.style.display = 'block';
        card.classList.add('flipped');
    }
}

createGameBoard();
    </script>
</body>
</html>