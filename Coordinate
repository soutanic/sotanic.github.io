sota005フォームのログインコードを入力してください<html>
<head>
    <title>ログインコード</title>
</head>
<body>
    <div>
        <label for="loginCode">コードを入力:</label>
        <input id="loginCode" type="text" />
        <button onclick="decryptText()">緯度経度表示</button>
    </div>

    <div>
        <p>緯度経度:</p>
        <p id="decryptedResult"></p>
    </div>

    <script>
        function vignereDecrypt(text, key) {
            let decryptedText = "";
            for (let i = 0; i < text.length; i++) {
                const char = text.charAt(i);
                const keyChar = key.charAt(i % key.length);
                const charCode = char.charCodeAt(0);
                const keyCharCode = keyChar.charCodeAt(0);
                const decryptedCharCode = charCode - keyCharCode + 123; // 123は'a'のcharCode
                decryptedText += String.fromCharCode(decryptedCharCode);
            }
            return decryptedText;
        }

        function decryptText() {
            const loginCode = document.getElementById("loginCode").value;
            const encryptedText = "矌稰硉稬矊稢矌稱矇稯瞻穉瞹稬矌稳硉稯矊稢矌稭矇稫瞻穀";
            const decryptedResult = vignereDecrypt(encryptedText, loginCode);
            document.getElementById("decryptedResult").textContent = decryptedResult;
        }
    </script>
</body>
</html>
