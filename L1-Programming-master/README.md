<!doctype html>



<head>

    <title>Canvas</title>

</head>



<body>

    <canvas id="gameCanvas" width="600" height="900"></canvas>



    <script>
        var name = '';
        while (name == '' || name == null) {
            name = prompt('what is your name?') || ''; //this is the prompt that asks you for your name at the start of the game.

        }


        var difficulty = '';

        while (difficulty != 'easy' && difficulty != 'medium' && difficulty != 'hard') {
            difficulty = prompt('choose difficulty, Easy, Medium or Hard') || '';
            difficulty.toLowerCase();
            console.log(difficulty); //this is the prompt that chooses the difficulty of the game.
        }





        var canvas, canvasContext;



        window.onload = function() {

            canvas = document.getElementById('gameCanvas');

            canvasContext = canvas.getContext('2d');



            document.addEventListener('keydown', keyPressed);

            document.addEventListener('keyup', keyReleased);





            setInterval(mainloop, 1000 / 50);

        }

        // player variables

        var playerXpos = 10;

        var playerYpos = 10;

        var playerXspeed = 7;

        var playerYspeed = 7;

        var playerSize = 25;



        // key codes

        const UP_KEY = 38;

        const LEFT_KEY = 37;

        const RIGHT_KEY = 39;

        const DOWN_KEY = 40;

        var upKeyPressed = false;

        var leftKeyPressed = false;

        var downKeyPressed = false;

        var rightKeyPressed = false;







        function mainloop() { // loop runs code 50 times per secound

            colorRect(0, 0, canvas.width, canvas.height, 'green'); //bg
            colorRect(0, 100, canvas.width, canvas.height, 'gray');
            colorRect(0, 200, canvas.width, canvas.height, 'green');
            colorRect(0, 300, canvas.width, canvas.height, 'gray');
            colorRect(0, 400, canvas.width, canvas.height, 'green');
            colorRect(0, 500, canvas.width, canvas.height, 'gray');
            colorRect(0, 600, canvas.width, canvas.height, 'green');
            colorRect(0, 700, canvas.width, canvas.height, 'gray');
            colorRect(0, 800, canvas.width, canvas.height, 'green');


            colorRect(playerXpos, playerYpos, playerSize, playerSize, 'yellow')



            playermove();

            objectdraw();

        }







        function keyPressed(evt) {

            if (evt.keyCode == UP_KEY) {

                upKeyPressed = true;

            }

            if (evt.keyCode == LEFT_KEY) {

                leftKeyPressed = true;

            }

            if (evt.keyCode == DOWN_KEY) {

                downKeyPressed = true;

            }

            if (evt.keyCode == RIGHT_KEY) {

                rightKeyPressed = true;

            }

        }





        function keyReleased(evt) {

            if (evt.keyCode == UP_KEY) {

                upKeyPressed = false;

            }

            if (evt.keyCode == LEFT_KEY) {

                leftKeyPressed = false;

            }

            if (evt.keyCode == DOWN_KEY) {

                downKeyPressed = false;

            }

            if (evt.keyCode == RIGHT_KEY) {

                rightKeyPressed = false;

            }

        }





        //player movement

        function playermove() {
            if (rightKeyPressed && playerXpos < canvas.width - playerSize) {
                playerXpos += playerXspeed;
                if (playerXpos < 0 - playerSize) {
                    playerXpos = canvas.width - playerSize / 2;
                }
            }



            if (leftKeyPressed && playerXpos > 0) {
                playerXpos -= playerXspeed;
                if (playerXpos < 0 - playerSize) {
                    playerXpos = canvas.width - playerSize / 2;
                }
            }
            if (upKeyPressed && playerYpos > 0) {
                playerYpos -= playerYspeed;
            }

            if (downKeyPressed && playerYpos < canvas.height - playerSize) {
                playerYpos += playerYspeed;
            }



        }









        //func to draw colored rects on canvas

        function colorRect(x, y, w, h, c) {

            canvasContext.fillStyle = c;

            canvasContext.fillRect(x, y, w, h);





        }

    </script>



</body>

