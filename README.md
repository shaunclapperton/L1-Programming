<!doctype html>

<head>
    <title>game</title>
</head>

<body>
    <canvas id="gameCanvas" width="400" height="400"></canvas>
    <script>
        var canvas, canvasContext;

        window.onload = function() {
            canvas = document.getElementById('gameCanvas');
            canvasContext = canvas.getContext('2d');

            for (var i = 0; i < brickCount; i++) {

            }

            document.addEventListener('keydown', keyPressed);
            document.addEventListener('keyup', keyReleased);

            setInterval(mainloop, 1000 / 50);
        }

        // player vars 
        var playerXpos = 0;
        var playerYpos = 0;
        var playerXspeed = 8;
        var playerYspeed = 8;
        var playerSize = 20;

        var brickCount = 10;

        var score = 0;

        var bricks = [];

        const LEFT_KEY = 37;
        const RIGHT_KEY = 39;
        const UP_KEY = 38;
        const DOWN_KEY = 40;
        var leftKeyPressed = false;
        var rightKeyPressed = false;
        var upKeyPressed = false;
        var downKeyPressed = false;

        function mainloop() {
            colorRect(0, 0, canvas.width, canvas.height, 'black'); // bg
            colorRect(playerXpos, playerYpos, playerSize, playerSize, 'red'); // player

            playerMove();
            bricksDraw();
            bricksMove();
        }
