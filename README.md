<!DOCTYPE html>
<html>
<head>
    <title>声旅茶帖 | 城市之声</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            margin: 0;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }
        .container {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            max-width: 500px;
            text-align: center;
        }
        h1 {
            color: #2d3748;
            margin-bottom: 10px;
        }
        .subtitle {
            color: #718096;
            margin-bottom: 30px;
        }
        .player {
            background: #f7fafc;
            border-radius: 15px;
            padding: 25px;
            margin: 25px 0;
        }
        audio {
            width: 100%;
            margin-top: 15px;
        }
        .note {
            font-size: 14px;
            color: #4a5568;
            line-height: 1.6;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>声旅茶帖</h1>
        <div class="subtitle">Soundscape Tea Ticket</div>
        
        <div class="player">
            <p>正在播放：青花瓷 · 江南小调</p>
            <audio controls>
                <source src="青花瓷（1）.mp3" type="audio/mpeg">
                您的浏览器不支持音频播放。
            </audio>
        </div>
        
        <div class="note">
            <p>🎵 此声音为原创弹奏的《青花瓷》片段</p>
            <p>🍵 建议搭配龙井茶一同品味</p>
            <p>📍 扫描车票二维码体验更多城市声音</p>
        </div>
        
        <div style="margin-top: 25px; font-size: 12px; color: #a0aec0;">
            一纸花约 × 声旅茶帖项目
        </div>
    </div>
</body>
</html>
