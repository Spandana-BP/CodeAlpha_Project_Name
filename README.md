<!DOCTYPE html>
<html lang="en">
<body>
    <div class="container">
        <h1>Translate Tool</h1>
        
<body>
    <div class="container">
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


