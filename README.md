<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MindfulSpace - Improve Your Mental Health</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #8ecae6, #023047);
            color: #fff;
        }
        header {
            text-align: center;
            padding: 50px;
            background-color: rgba(0, 0, 0, 0.4);
        }
        header h1 {
            margin: 0;
            font-size: 3em;
        }
        header p {
            font-size: 1.2em;
            margin-top: 10px;
        }
        nav {
            text-align: center;
            margin: 20px 0;
        }
        nav a {
            text-decoration: none;
            color: #ffb703;
            margin: 0 15px;
            font-weight: bold;
        }
        nav a:hover {
            text-decoration: underline;
        }
        .content {
            text-align: center;
            padding: 30px;
        }
        .form-container, .stress-calculator {
            margin: 20px auto;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            width: 80%;
            max-width: 400px;
        }
        .form-container label, .stress-calculator label {
            display: block;
            margin: 10px 0 5px;
            font-weight: bold;
        }
        .form-container input, .stress-calculator input {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: none;
            border-radius: 5px;
        }
        .form-container button, .stress-calculator button {
            padding: 10px 20px;
            font-size: 1em;
            color: #fff;
            background-color: #219ebc;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .form-container button:hover, .stress-calculator button:hover {
            background-color: #023047;
        }
        .output-container {
            margin-top: 20px;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
        }
        footer {
            text-align: center;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.6);
        }
        footer p {
            margin: 0;
        }
    </style>
</head>
<body>
    <header>
        <h1>Welcome to Mindfulspace</h1>
        <p>Your journey to improved mental health starts here</p>
    </header>
    <nav>
        <a href="#about">About</a>
        <a href="#features">Features</a>
        <a href="#contact">Contact</a>
    </nav>
    <div class="content">
        <h2>Start Your Mindfulspce  Journey</h2>
        <p>Discover meditation techniques, breathing exercises, and tools to manage stress effectively.</p>
        
        <div class="form-container">
            <h3>Tell Us About Yourself</h3>
            <form onsubmit="handleSubmit(event)">
                <label for="name">Your Name:</label>
                <input type="text" id="name" name="name" placeholder="Enter your name" required>
                <label for="goal">Your Goal for Mindfulspace:</label>
                <textarea id="goal" name="goal" rows="4" placeholder="What do you want to achieve?" required></textarea>
                <button type="submit">Submit</button>
            </form>
        </div>

        <div id="output" class="output-container" style="display: none;">
            <h3>Your Input:</h3>
            <p><strong>Name:</strong> <span id="output-name"></span></p>
            <p><strong>Goal:</strong> <span id="output-goal"></span></p>
        </div>

        <div class="stress-calculator">
            <h3>Stress Calculator</h3>
            <form onsubmit="calculateStress(event)">
                <label>How often do you feel overwhelmed? (1-5):</label>
                <input type="number" id="q1" min="1" max="5" required>
                <label>How well do you sleep? (1-5, 1 = Poor, 5 = Excellent):</label>
                <input type="number" id="q2" min="1" max="5" required>
                <label>How often do you feel fatigued? (1-5):</label>
                <input type="number" id="q3" min="1" max="5" required>
                <button type="submit">Calculate Stress Level</button>
            </form>
        </div>

        <div id="stress-output" class="output-container" style="display: none;">
            <h3>Your Stress Level:</h3>
            <p id="stress-result"></p>
        </div>
    </div>

    <footer>
        <p>&copy; 2024 Mindfulspace. All rights reserved.</p>
    </footer>

    <script>
        function handleSubmit(event) {
            event.preventDefault();
            const name = document.getElementById('name').value;
            const goal = document.getElementById('goal').value;

            // Display the output container
            document.getElementById('output').style.display = 'block';
            document.getElementById('output-name').textContent = name;
            document.getElementById('output-goal').textContent = goal;

            // Clear the form
            event.target.reset();
        }

        function calculateStress(event) {
            event.preventDefault();
            const q1 = parseInt(document.getElementById('q1').value);
            const q2 = parseInt(document.getElementById('q2').value);
            const q3 = parseInt(document.getElementById('q3').value);

            const stressLevel = (q1 + (6 - q2) + q3) / 3;
            const result = stressLevel <= 2 
                ? "Low Stress" 
                : stressLevel <= 4 
                ? "Moderate Stress" 
                : "High Stress";

            document.getElementById('stress-output').style.display = 'block';
            document.getElementById('stress-result').textContent = `Your stress level is: ${result} (${stressLevel.toFixed(1)}/5).`;

            // Clear the form
            event.target.reset();
        }
    </script>
</body>
</html>
