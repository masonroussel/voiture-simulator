# voiture-simulator
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jeu de Course</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
        }
        canvas {
            border: 2px solid black;
            background-color: lightgray;
        }
        #menu {
            margin-bottom: 20px;
        }
    </style>
</head>
<body>
    <h1>Jeu de Course</h1>
    <div id="menu">
        <label for="voiture">Choisissez votre voiture :</label>
        <select id="voiture">
            <option value="red">Voiture Rouge</option>
            <option value="blue">Voiture Bleue</option>
            <option value="green">Voiture Verte</option>
        </select>
        <button onclick="demarrerCourse()">Démarrer la Course</button>
    </div>
    <canvas id="gameCanvas" width="800" height="400"></canvas>
    
    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        let voiture;
        let x = 50;
        let vitesse = 5;
        
        function demarrerCourse() {
            const choixVoiture = document.getElementById('voiture').value;
            voiture = choixVoiture;
            x = 50;
            animer();
        }
        
        function animer() {
            if (x < canvas.width - 100) {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                ctx.fillStyle = voiture;
                ctx.fillRect(x, 150, 100, 50);
                x += vitesse;
                requestAnimationFrame(animer);
            } else {
                alert('Course terminée ! Vous avez gagné !');
            }
        }
    </script>
</body>
</html>
