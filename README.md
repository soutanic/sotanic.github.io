
<!DOCTYPE html>
<html>
<head>
    <title>音声ファイル再生リスト</title>
</head>
<body>
    <label for="fileInput">音声ファイルを選択してください：</label>
    <input type="file" id="fileInput" multiple accept=".mp3, .wav">
    <button onclick="playNext()">再生</button>
    <ul id="playlist"></ul>

    <input type="range" id="volumeSlider" min="0" max="1" step="0.01" value="1">
    
    <br><br>

    <audio id="audioPlayer">
        Your browser does not support the audio element.
    </audio>
    
    <script>
        let audioFiles = [];
        let currentIndex = 0;

        const fileInput = document.getElementById('fileInput');
        const playlist = document.getElementById('playlist');
        const audioPlayer = document.getElementById('audioPlayer');
        const volumeSlider = document.getElementById('volumeSlider');

        audioPlayer.volume = 1; // デフォルトは最大音量

        fileInput.addEventListener('change', function() {
            const files = fileInput.files;

            for (let i = 0; i < files.length; i++) {
                const file = files[i];
                if (file.type.startsWith('audio/')) {
                    audioFiles.push(URL.createObjectURL(file));
                    const listItem = document.createElement('li');
                    listItem.textContent = file.name;
                    playlist.appendChild(listItem);
                }
            }
        });

        function playNext() {
            if (audioFiles.length === 0) return;

            audioPlayer.src = audioFiles[currentIndex];
            audioPlayer.play();

            audioPlayer.onended = function() {
                currentIndex = (currentIndex + 1) % audioFiles.length;
                playNext();
            };
        }

        // スライダーの値が変更されたときに音量を更新
        volumeSlider.addEventListener("input", () => {
            audioPlayer.volume = volumeSlider.value;
        });
    </script>
</body>
</html>
