<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Score des pays</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f0f0f0;
        }
        #country-score {
            margin-top: 20px;
        }
        button {
            font-size: 24px;
            padding: 10px 20px;
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <h1>Score des pays</h1>
    <label for="country-select">Sélectionnez un pays :</label>
    <select id="country-select">
        <option value="USA">États-Unis</option>
        <option value="France">France</option>
        <option value="Allemagne">Allemagne</option>
        <option value="Espagne">Espagne</option>
    </select>
    <button id="increase-score">Augmenter le score</button>
    <div id="country-score">
        <h2>Score actuel :</h2>
        <p id="score">0</p>
    </div>

    <script>
        const countrySelect = document.getElementById('country-select');
        const increaseButton = document.getElementById('increase-score');
        const scoreDisplay = document.getElementById('score');

        function setScore(country, score) {
            localStorage.setItem(country, score);
        }

        function getScore(country) {
            const score = localStorage.getItem(country);
            return score ? parseInt(score) : 0;
        }

        function updateScoreDisplay() {
            const selectedCountry = countrySelect.value;
            const score = getScore(selectedCountry);
            scoreDisplay.textContent = score;
        }

        increaseButton.addEventListener('click', () => {
            const selectedCountry = countrySelect.value;
            const currentScore = getScore(selectedCountry);
            const newScore = currentScore + 1;
            setScore(selectedCountry, newScore);
            updateScoreDisplay();
        });

        window.addEventListener('load', () => {
            updateScoreDisplay();
        });

        countrySelect.addEventListener('change', () => {
            updateScoreDisplay();
        });
    </script>
</body>
</html>

