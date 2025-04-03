<!DOCTYPE html>
<html lang="en">
<body>
    <div class="container">
        <h1>Google Translate Tool</h1>
        
        <textarea id="inputText" placeholder="Enter your sentence..."> </textarea>
        <br>
        
        <label><b>This is in:</b></label>
        <select id="sourceLanguage">
            <option value="auto">Detect Language</option>
            <option value="en">English</option>
            <option value="hi">Hindi</option>
            <option value="kn">Kannada</option>
            <option value="fr">French</option>
            <option value="es">Spanish</option>
            <option value="de">German</option>
        </select>

        <label><b>Translate to:</b></label>
        <select id="targetLanguage">
            <option value="hi">Hindi</option>
            <option value="kn">Kannada</option>
            <option value="en">English</option>
            <option value="fr">French</option>
            <option value="es">Spanish</option>
            <option value="de">German</option>
        </select>
        <br><br>
        
        <button onclick="translateText()">Translate</button>
        
        <h2>Translated Text:</h2>
        <p id="outputText"></p>
    </div>
    
    <script>
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




