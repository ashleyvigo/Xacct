<!DOCTYPE html>
<html>
<head>
    <title>Flashing Button</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: black; /* Initial background */
        }

        #flashButton {
            background-color: red;
            color: white;
            font-size: 24px;
            font-weight: bold;
            padding: 50px 100px;
            border: none;
            cursor: pointer;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <button id="flashButton">You can do it!</button>

    <script>
        const button = document.getElementById('flashButton');
        const colors = ['red', 'blue', 'green', 'yellow', 'purple', 'orange']; // Array of colors

        button.addEventListener('click', function() {
            let intervalId = setInterval(flash, 200); // Flash every 200ms

            function flash() {
                const randomColor = colors[Math.floor(Math.random() * colors.length)];
                document.body.style.backgroundColor = randomColor;
            }

            // Stop flashing after 2 seconds
            setTimeout(function() {
                clearInterval(intervalId);
                document.body.style.backgroundColor = 'black'; // Reset background
            }, 2000);
        });
    </script>
</body>
</html>
