<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Language Translation Tool</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background-color: #f4f4f4;
        }
        .container {
            max-width: 600px;
            margin: auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        textarea {
            width: 100%;
            height: 100px;
            margin-bottom: 10px;
        }
        button {
            padding: 10px 20px;
            background: #007BFF;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Language Translation Tool</h1>
        <textarea id="inputText" placeholder="Enter text to translate..."></textarea>
        <br>
        <select id="targetLanguage">
            <option value="es">Spanish</option>
            <option value="fr">French</option>
            <option value="de">German</option>
            <option value="hi">Hindi</option>
        </select>
        <br><br>
        <button onclick="translateText()">Translate</button>
        <h2>Translated Text:</h2>
        <p id="outputText"></p>
    </div>
    
    <script>
        async function translateText() {
            const text = document.getElementById("inputText").value;
            const targetLang = document.getElementById("targetLanguage").value;
            const apiKey = 'YOUR_GOOGLE_TRANSLATE_API_KEY'; // Replace with your actual API key
            
            const url = `https://translation.googleapis.com/language/translate/v2?key=${apiKey}`;
            
            const response = await fetch(url, {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ q: text, target: targetLang, format: "text" })
            });

            if (!response.ok) {
                document.getElementById("outputText").innerText = "Error: Unable to translate.";
                return;
            }

            const data = await response.json();
            document.getElementById("outputText").innerText = data.data.translations[0].translatedText;
        }
    </script>
</body>
</html>

