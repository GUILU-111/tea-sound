<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>声旅茶帖 · 城市之声</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-tap-highlight-color: transparent;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, "PingFang SC", "Helvetica Neue", sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            display: flex;
            justify-content: center;
            align-items: center;
            line-height: 1.6;
        }
        
        .card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border-radius: 24px;
            padding: 30px 25px;
            width: 100%;
            max-width: 400px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.15);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }
        
        .header {
            text-align: center;
            margin-bottom: 30px;
        }
        
        h1 {
            color: #2d3748;
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 8px;
            background: linear-gradient(135deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .subtitle {
            color: #718096;
            font-size: 16px;
            font-weight: 400;
        }
        
        .city-tag {
            display: inline-block;
            background: linear-gradient(135deg, #4299e1, #667eea);
            color: white;
            padding: 8px 20px;
            border-radius: 50px;
            font-size: 16px;
            margin: 15px 0 25px;
            box-shadow: 0 4px 12px rgba(102, 126, 234, 0.3);
        }
        
        .player-container {
            background: #f8fafc;
            border-radius: 18px;
            padding: 25px 20px;
            margin: 25px 0;
            border: 1px solid #e2e8f0;
        }
        
        .player-title {
            color: #4a5568;
            font-size: 16px;
            margin-bottom: 15px;
            text-align: center;
            font-weight: 500;
        }
        
        audio {
            width: 100%;
            height: 48px;
            border-radius: 12px;
            outline: none;
        }
        
        /* iOS Safari音频控件美化 */
        audio::-webkit-media-controls-panel {
            background-color: #edf2f7;
            border-radius: 12px;
        }
        
        audio::-webkit-media-controls-play-button {
            background-color: #667eea;
            border-radius: 50%;
        }
        
        .features {
            margin: 25px 0;
        }
        
        .feature-item {
            display: flex;
            align-items: flex-start;
            margin-bottom: 18px;
            padding-bottom: 18px;
            border-bottom: 1px solid #f1f5f9;
        }
        
        .feature-item:last-child {
            border-bottom: none;
            margin-bottom: 0;
            padding-bottom: 0;
        }
        
        .feature-icon {
            font-size: 22px;
            margin-right: 15px;
            margin-top: 2px;
        }
        
        .feature-text {
            flex: 1;
            color: #4a5568;
            font-size: 15px;
        }
        
        .feature-text strong {
            color: #2d3748;
            font-weight: 600;
        }
        
        .footer {
            text-align: center;
            margin-top: 30px;
            padding-top: 25px;
            border-top: 1px solid #e2e8f0;
            color: #a0aec0;
            font-size: 13px;
        }
        
        .footer a {
            color: #667eea;
            text-decoration: none;
        }
        
        /* 响应式调整 */
        @media (max-width: 380px) {
            .card {
                padding: 25px 20px;
            }
            
            h1 {
                font-size: 24px;
            }
            
            .city-tag {
                font-size: 14px;
                padding: 6px 16px;
            }
        }
        
        /* 加载动画 */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .card {
            animation: fadeIn 0.6s ease-out;
        }
    </style>
</head>
<body>
    <div class="card">
        <div class="header">
            <h1>声旅茶帖</h1>
            <div class="subtitle">Soundscape Tea Ticket</div>
            <div class="city-tag">江南 · 青花瓷</div>
        </div>
        
        <div class="player-container">
            <div class="player-title">扫码聆听城市记忆</div>
            <audio controls controlsList="nodownload">
                <source src="song.mp3" type="audio/mpeg">
                您的浏览器不支持音频播放，请尝试使用Chrome或Safari浏览器。
            </audio>
        </div>
        
        <div class="features">
            <div class="feature-item">
                <div class="feature-icon">🎵</div>
                <div class="feature-text">
                    <strong>原创音乐</strong><br>
                    此音频为团队成员原创弹奏的《青花瓷》片段，融合江南小调元素。
                </div>
            </div>
            
            <div class="feature-item">
                <div class="feature-icon">🍵</div>
                <div class="feature-text">
                    <strong>茶音共品</strong><br>
                    建议搭配西湖龙井一同体验，感受茶香与乐韵的交融。
                </div>
            </div>
            
            <div class="feature-item">
                <div class="feature-icon">📍</div>
                <div class="feature-text">
                    <strong>城市漫游</strong><br>
                    每张"茶票"对应一座城市，扫码即可开启专属的声音旅程。
                </div>
            </div>
        </div>
        
        <div class="footer">
            <p>一纸花约 × 声旅茶帖项目</p>
            <p style="margin-top: 8px; font-size: 12px;">
                扫描包装二维码，发现更多城市声音
            </p>
        </div>
    </div>
    
    <script>
        // 增强音频体验
        document.addEventListener('DOMContentLoaded', function() {
            const audio = document.querySelector('audio');
            
            // 预加载音频
            audio.preload = 'auto';
            
            // 添加播放状态提示
            audio.addEventListener('play', function() {
                console.log('开始播放城市声音');
            });
            
            // 防止音频自动播放（遵守浏览器策略）
            document.addEventListener('click', function() {
                if (audio.paused) {
                    // 用户交互后可播放
                }
            }, { once: true });
        });
        
        // 防止双击缩放（iOS Safari）
        let lastTouchEnd = 0;
        document.addEventListener('touchend', function(event) {
            const now = Date.now();
            if (now - lastTouchEnd <= 300) {
                event.preventDefault();
            }
            lastTouchEnd = now;
        }, false);
    </script>

    <!-- ==================== 新增：iPhone访问优化提示 ==================== -->
    <script>
    // 增强版iPhone访问优化
    (function() {
        // 等待页面加载完成
        document.addEventListener('DOMContentLoaded', function() {
            // 检测是否为iOS设备
            const isIOS = /iPhone|iPad|iPod/.test(navigator.userAgent);
            const isGitHub = window.location.hostname.includes('github.io');
            
            if (isIOS && isGitHub) {
                // 创建提示框
                const notice = document.createElement('div');
                notice.id = 'ios-optimize-notice';
                notice.innerHTML = `
                    <div style="
                        position: fixed;
                        top: 0;
                        left: 0;
                        right: 0;
                        background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
                        color: white;
                        padding: 15px;
                        z-index: 9999;
                        font-family: -apple-system, BlinkMacSystemFont, sans-serif;
                        box-shadow: 0 4px 12px rgba(0,0,0,0.1);
                        text-align: center;
                    ">
                        <div style="display: flex; align-items: center; justify-content: center; gap: 10px;">
                            <span style="font-size: 18px;">📱</span>
                            <div style="text-align: left;">
                                <div style="font-weight: 600; font-size: 14px;">iPhone访问优化建议</div>
                                <div style="font-size: 12px; opacity: 0.9;">GitHub在国内访问可能较慢，点击下方链接获得最佳体验</div>
                            </div>
                        </div>
                        <a href="https://cdn.jsdelivr.net/gh/GUILU-111/tea-sound@main/index.html" 
                           style="
                               display: inline-block;
                               margin-top: 10px;
                               padding: 8px 20px;
                               background: white;
                               color: #667eea;
                               border-radius: 20px;
                               text-decoration: none;
                               font-weight: 600;
                               font-size: 13px;
                               box-shadow: 0 2px 8px rgba(0,0,0,0.1);
                           ">
                            点击切换到优化版本
                        </a>
                        <button onclick="document.getElementById('ios-optimize-notice').style.display='none'" 
                                style="
                                    position: absolute;
                                    right: 10px;
                                    top: 10px;
                                    background: transparent;
                                    border: none;
                                    color: white;
                                    font-size: 20px;
                                    cursor: pointer;
                                ">
                            ×
                        </button>
                    </div>
                `;
                
                // 添加到页面
                document.body.appendChild(notice);
                
                // 调整页面内容位置（避免被提示框遮挡）
                const originalPadding = document.body.style.paddingTop;
                document.body.style.paddingTop = '80px';
                
                // 点击关闭时恢复
                notice.querySelector('button').addEventListener('click', function() {
                    document.body.style.paddingTop = originalPadding;
                });
                
                // 10分钟后自动隐藏（如果评委停留时间很长）
                setTimeout(() => {
                    if (document.getElementById('ios-optimize-notice')) {
                        document.getElementById('ios-optimize-notice').style.opacity = '0';
                        document.getElementById('ios-optimize-notice').style.transition = 'opacity 0.5s';
                        setTimeout(() => {
                            if (document.getElementById('ios-optimize-notice')) {
                                document.getElementById('ios-optimize-notice').remove();
                                document.body.style.paddingTop = originalPadding;
                            }
                        }, 500);
                    }
                }, 600000); // 10分钟
            }
        });
    })();
    </script>
    <!-- ==================== iPhone优化代码结束 ==================== -->

</body>
</html>
