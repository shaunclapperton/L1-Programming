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
