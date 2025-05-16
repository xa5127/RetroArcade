<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Retro Arcade</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Press Start 2P', cursive;
        }

        body {
            background-color: #1a1a1a;
            color: #fff;
            display: flex;
            min-height: 100vh;
        }

        .sidebar {
            width: 250px;
            background-color: #000;
            padding: 20px;
            border-right: 3px solid #ff00ff;
            box-shadow: 0 0 15px #ff00ff;
        }

        .sidebar h1 {
            color: #00ff00;
            text-shadow: 0 0 10px #00ff00;
            font-size: 1.2em;
            margin-bottom: 30px;
            text-align: center;
        }

        .nav-links {
            list-style: none;
        }

        .nav-links li {
            margin: 20px 0;
        }

        .nav-links a {
            color: #fff;
            text-decoration: none;
            font-size: 0.8em;
            padding: 10px;
            display: block;
            border: 2px solid #ff00ff;
            border-radius: 5px;
            transition: all 0.3s;
        }

        .nav-links a:hover {
            background-color: #ff00ff;
            box-shadow: 0 0 15px #ff00ff;
            transform: scale(1.05);
        }

        .main-content {
            flex: 1;
            padding: 20px;
        }

        .welcome-screen {
            text-align: center;
            padding: 50px;
        }

        .welcome-screen h2 {
            color: #00ff00;
            font-size: 2em;
            margin-bottom: 30px;
            animation: glow 1.5s ease-in-out infinite alternate;
        }

        .welcome-screen p {
            color: #fff;
            font-size: 0.8em;
            line-height: 1.6;
            margin-bottom: 30px;
        }

        .game-container {
            display: none;
            width: 100%;
            height: calc(100vh - 80px); /* Adjusted for buttons */
        }

        @keyframes glow {
            from {
                text-shadow: 0 0 10px #00ff00;
            }
            to {
                text-shadow: 0 0 20px #00ff00, 0 0 30px #00ff00;
            }
        }
    </style>
</head>
<body>
    <div class="sidebar">
        <h1>RETRO ARCADE</h1>
        <ul class="nav-links">
            <li><a href="#" onclick="showHome()">Home</a></li>
            <li><a href="#" onclick="showPacman()">Pac-Man</a></li>
            <li><a href="#" onclick="showFlappyBird()">Flappy Bird</a></li>
        </ul>
    </div>

    <div class="main-content">
        <div id="welcome" class="welcome-screen">
            <h2>Welcome to Retro Arcade!</h2>
            <p>Step into the golden age of gaming with our classic collection.<br>
               Choose your game from the sidebar and relive the magic!</p>
        </div>
        <div id="pacman-game" class="game-container">
            <iframe id="pacman-frame" src="https://pacman.js.org/" width="100%" height="100%" frameborder="0"></iframe>
        </div>
        <div id="flappybird-game" class="game-container">
            <iframe id="flappybird-frame" src="https://flappybird.io/" width="100%" height="100%" frameborder="0"></iframe>
        </div>
    </div>

    <script>
        function showHome() {
            document.getElementById('welcome').style.display = 'block';
            document.getElementById('pacman-game').style.display = 'none';
            document.getElementById('flappybird-game').style.display = 'none';
        }

        function showPacman() {
            document.getElementById('welcome').style.display = 'none';
            document.getElementById('pacman-game').style.display = 'block';
            document.getElementById('flappybird-game').style.display = 'none';
            resetGame('flappybird'); // Reset Flappy Bird game
        }

        function showFlappyBird() {
            document.getElementById('welcome').style.display = 'none';
            document.getElementById('pacman-game').style.display = 'none';
            document.getElementById('flappybird-game').style.display = 'block';
            resetGame('pacman'); // Reset Pac-Man game
        }

        function resetGame(game) {
            if (game === 'pacman') {
                document.getElementById('pacman-frame').src = "https://pacman.js.org/"; // Reload Pac-Man
            } else if (game === 'flappybird') {
                document.getElementById('flappybird-frame').src = "https://flappybird.io/"; // Reload Flappy Bird
            }
        }

        // Show Pac-Man game by default
        showPacman();
    </script>
</body>
</html>
