<!DOCTYPE html>
<html>
<head>
    <title>Mini Tower Defense</title>
    <style>
        /* Styles CSS pour la mise en page */
        body {
            text-align: center;
            font-family: Arial, sans-serif;
        }
        #game-board {
            width: 400px;
            height: 400px;
            border: 1px solid black;
            position: relative;
        }
        .tower {
            width: 40px;
            height: 40px;
            background-color: gray;
            position: absolute;
            cursor: pointer;
        }
        .enemy {
            width: 20px;
            height: 20px;
            background-color: red;
            position: absolute;
            animation: moveEnemy 4s linear infinite;
        }
        @keyframes moveEnemy {
            0% { left: 0; top: 0; }
            100% { left: 360px; top: 360px; }
        }
    </style>
</head>
<body>
    <h1>Mini Tower Defense</h1>
    <div id="game-board">
        <!-- Zone de jeu -->
    </div>
    <p>Cliquez sur le tableau pour placer des tours.</p>

    <script>
        // Fonction pour placer une tour au clic
        function placeTower(event) {
            const tower = document.createElement('div');
            tower.className = 'tower';
            tower.style.left = (event.clientX - 20) + 'px'; // 20 pour centrer la tour
            tower.style.top = (event.clientY - 20) + 'px';
            document.getElementById('game-board').appendChild(tower);
        }

        // Ajoutez un gestionnaire d'événement pour placer une tour au clic
        document.getElementById('game-board').addEventListener('click', placeTower);
    </script>
</body>
</html>
