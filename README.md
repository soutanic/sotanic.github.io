
<html>
<head>
    <title>ログインコード</title>
</head>
<body>
    <div>
        <label for="loginCode">ログインコードを入力してください:</label>
        <input type="text" id="loginCode">
        <button onclick="decryptText()">ログイン</button>
    </div>

    <div>
        <p>URL:</p>
        <p id="decryptedResult"></p>
    </div>

    <script>
        // ビジュネル複合化関数
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

        // 複合化ボタンのクリック時に呼び出される関数
        function decryptText() {
            const loginCode = document.getElementById("loginCode").value;
            const encryptedText = "码穯砍穫砌稵矈稪砐穲砐稩砇穪砍穤砈穩矇穮砈稪砌穪砍穜矉稫矎稨矉稬矌種矉穝矿稭矽穞矉穞矍種矐種矻稰矎穡矐穞矾穝矻稯矍稫矌稴矏稲";
            const decryptedResult = vignereDecrypt(encryptedText, loginCode);
            document.getElementById("decryptedResult").textContent = decryptedResult;

            // ログインという文字にリンクを付ける
            const loginLink = document.createElement("a");
            loginLink.href = decryptedResult; // 複合結果をURLとして設定
            loginLink.textContent = "ログイン";
            document.getElementById("decryptedResult").innerHTML = ""; // 一旦内容をクリア
            document.getElementById("decryptedResult").appendChild(loginLink); // リンクを追加
        }

        // Enterキーが押されたときにdecryptTextを呼び出す
        document.getElementById("loginCode").addEventListener("keyup", function(event) {
            if (event.key === "Enter") {
                decryptText();
            }
        });
    </script>
</body>
</html>
