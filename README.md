<!DOCTYPE html>
<html lang="en">
<head>
    <title>Language Translation Tool</title>
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

