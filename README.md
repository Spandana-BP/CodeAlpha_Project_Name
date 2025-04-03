<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Language Translator</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; padding: 20px; background-color: #121212; color: white; }
        .container { max-width: 400px; margin: auto; padding: 20px; background: #1e1e1e; border-radius: 10px; box-shadow: 0px 0px 10px rgba(255, 255, 255, 0.1); }
        .display-box, .output { background: #2c2c2c; padding: 10px; border-radius: 5px; margin-bottom: 10px; min-height: 40px; }
        textarea, select, button { width: 100%; padding: 10px; margin-top: 10px; border-radius: 5px; border: none; }
        textarea { background: #2c2c2c; color: white; }
        button { background: #007BFF; color: white; cursor: pointer; }
    </style>
</head>
<body>
    <div class="container">
        <h2>Language Translator</h2>
        <div class="display-box" id="displayText">Enter text...</div>
        <textarea id="inputText" placeholder="Enter text..." oninput="updateDisplay()"></textarea>
        <select id="sourceLanguage">
            <option value="auto">Detect Language</option>
            <option value="en">English</option>
            <option value="kn">Kannada</option>
        </select>
        <select id="targetLanguage">
            <option value="kn">Kannada</option>
            <option value="en">English</option>
        </select>
        <button onclick="translateText()">Translate</button>
        <div class="output" id="outputText"></div>
    </div>

    <script>
        function updateDisplay() {
            document.getElementById("displayText").innerText = document.getElementById("inputText").value || "Enter text...";
        }
        async function translateText() {
            const text = document.getElementById("inputText").value;
            const sourceLang = document.getElementById("sourceLanguage").value;
            const targetLang = document.getElementById("targetLanguage").value;
            const url = `https://translate.googleapis.com/translate_a/single?client=gtx&sl=${sourceLang}&tl=${targetLang}&dt=t&q=${encodeURIComponent(text)}`;
            try {
                const response = await fetch(url);
                const data = await response.json();
                document.getElementById("outputText").innerText = data[0][0][0];
            } catch (error) {
                document.getElementById("outputText").innerText = "Error: Unable to translate.";
            }
        }
    </script>
</body>
</html>