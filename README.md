<!DOCTYPE html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>声旅茶帖 · 城市之声</title>
    <style>
        /* 你的原有CSS代码保持不变 */
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
        
        /* ... 其余CSS代码保持不变 ... */
    </style>
    
    <!-- 预加载关键资源 -->
    <link rel="preconnect" href="https://cdn.jsdelivr.net">
    <link rel="dns-prefetch" href="https://cdn.jsdelivr.net">
</head>
<body>
    <div class="card">
        <!-- 你的页面内容保持不变 -->
        <div class="header">
            <h1>声旅茶帖</h1>
            <div class="subtitle">Soundscape Tea Ticket</div>
            <div class="city-tag">江南 · 青花瓷</div>
        </div>
        
        <div class="player-container">
            <div class="player-title">扫码聆听城市记忆</div>
            <audio id="mainAudio" controls controlsList="nodownload">
                <!-- 多CDN音频源，自动选择可用的 -->
                <source id="audioSource1" src="https://cdn.jsdelivr.net/gh/GUILU-111/tea-sound@main/song.mp3" type="audio/mpeg">
                <source id="audioSource2" src="song.mp3" type="audio/mpeg">
                <source id="audioSource3" src="https://tea-ticket-china.pages.dev/song.mp3" type="audio/mpeg">
                您的浏览器不支持音频播放，请尝试使用Chrome或Safari浏览器。
            </audio>
            <div id="audioStatus" style="font-size:12px; color:#666; margin-top:8px; text-align:center;"></div>
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
            <!-- 网络状态显示 -->
            <div id="networkInfo" style="font-size:11px; color:#aaa; margin-top:5px;">
                当前使用: <span id="cdnType">检测中...</span>
            </div>
        </div>
    </div>
    
    <script>
        // 增强音频体验 + 多CDN自动切换
        document.addEventListener('DOMContentLoaded', function() {
            const audio = document.getElementById('mainAudio');
            const audioStatus = document.getElementById('audioStatus');
            const cdnType = document.getElementById('cdnType');
            
            // 可用的音频源列表（按优先级排序）
            const audioSources = [
                { id: 'audioSource1', url: 'https://cdn.jsdelivr.net/gh/GUILU-111/tea-sound@main/song.mp3', name: 'jsDelivr CDN' },
                { id: 'audioSource2', url: 'song.mp3', name: '直接连接' },
                { id: 'audioSource3', url: 'https://tea-ticket-china.pages.dev/song.mp3', name: '备用CDN' }
            ];
            
            // 检测最佳音频源
            function testAudioSources() {
                audioStatus.textContent = '检测最佳音频源...';
                
                let testedCount = 0;
                let bestSource = audioSources[0]; // 默认第一个
                
                // 测试每个源的可用性
                audioSources.forEach((source, index) => {
                    const testAudio = new Audio();
                    testAudio.src = source.url + '?test=' + Date.now();
                    testAudio.preload = 'auto';
                    
                    testAudio.addEventListener('loadeddata', function() {
                        // 这个源可用
                        if (index === 0 || Math.random() > 0.3) { // 优先第一个，但有时随机选择避免全部用同一个
                            bestSource = source;
                        }
                        testedCount++;
                        
                        if (testedCount === audioSources.length) {
                            // 所有源测试完成
                            applyBestSource(bestSource);
                        }
                    });
                    
                    testAudio.addEventListener('error', function() {
                        testedCount++;
                        if (testedCount === audioSources.length) {
                            applyBestSource(bestSource);
                        }
                    });
                    
                    // 设置超时
                    setTimeout(() => {
                        if (!testAudio.readyState) {
                            testedCount++;
                            if (testedCount === audioSources.length) {
                                applyBestSource(bestSource);
                            }
                        }
                    }, 2000);
                });
            }
            
            function applyBestSource(source) {
                // 切换到最佳源
                const audioElement = document.getElementById('mainAudio');
                const sourceElement = document.getElementById(source.id);
                
                // 清空所有source，添加最佳源
                audioElement.innerHTML = '';
                const newSource = document.createElement('source');
                newSource.src = source.url;
                newSource.type = 'audio/mpeg';
                audioElement.appendChild(newSource);
                audioElement.appendChild(document.createTextNode('您的浏览器不支持音频播放。'));
                
                // 更新状态显示
                audioStatus.textContent = `使用: ${source.name}`;
                cdnType.textContent = source.name;
                audioStatus.style.color = '#4CAF50';
                
                // 重新加载音频
                audioElement.load();
                
                // 预加载
                audioElement.preload = 'auto';
            }
            
            // 开始检测
            testAudioSources();
            
            // 音频事件监听
            audio.addEventListener('play', function() {
                audioStatus.textContent = '正在播放...';
                audioStatus.style.color = '#2196F3';
            });
            
            audio.addEventListener('error', function(e) {
                console.error('音频播放错误:', e);
                audioStatus.textContent = '播放失败，尝试切换源...';
                audioStatus.style.color = '#FF5722';
                
                // 3秒后重试
                setTimeout(testAudioSources, 3000);
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
            
            // 网络状态检测
            function updateNetworkInfo() {
                const connection = navigator.connection || navigator.mozConnection || navigator.webkitConnection;
                if (connection) {
                    const info = `网络: ${connection.effectiveType || '未知'} | 延迟: ${connection.rtt || '?'}ms`;
                    cdnType.textContent += ' | ' + info;
                }
            }
            
            if (navigator.connection) {
                navigator.connection.addEventListener('change', updateNetworkInfo);
            }
            updateNetworkInfo();
        });
        
        // 微信浏览器特殊处理
        (function() {
            const isWeChat = /MicroMessenger/i.test(navigator.userAgent);
            const isIOS = /iPhone|iPad|iPod/i.test(navigator.userAgent);
            
            if (isWeChat && isIOS) {
                // 在微信中显示提示
                const notice = document.createElement('div');
                notice.style.cssText = `
                    position: fixed;
                    bottom: 20px;
                    left: 20px;
                    right: 20px;
                    background: rgba(0,0,0,0.8);
                    color: white;
                    padding: 12px;
                    border-radius: 10px;
                    z-index: 10000;
                    font-size: 13px;
                    text-align: center;
                `;
                notice.innerHTML = `
                    <div style="margin-bottom:5px;">🎧 iOS微信内播放提示</div>
                    <div style="font-size:11px; opacity:0.9;">
                        如无法播放，请点击右上角"..."选择"在浏览器打开"
                    </div>
                `;
                document.body.appendChild(notice);
                
                // 10秒后自动隐藏
                setTimeout(() => {
                    notice.style.opacity = '0';
                    notice.style.transition = 'opacity 0.5s';
                    setTimeout(() => notice.remove(), 500);
                }, 10000);
            }
        })();
    </script>

    <!-- 极简网络检测 -->
    <script>
    // 简单直接的网络状态提示
    (function() {
        setTimeout(() => {
            const isSlow = performance.timing.loadEventEnd - performance.timing.navigationStart > 3000;
            const isGitHub = window.location.hostname.includes('github.io');
            
            if (isSlow && isGitHub) {
                const tip = document.createElement('div');
                tip.style.cssText = `
                    position: fixed;
                    top: 10px;
                    right: 10px;
                    background: #FF9800;
                    color: white;
                    padding: 6px 12px;
                    border-radius: 15px;
                    font-size: 11px;
                    z-index: 9998;
                `;
                tip.textContent = '网络较慢';
                document.body.appendChild(tip);
                
                setTimeout(() => tip.remove(), 5000);
            }
        }, 1000);
    })();
    </script>
</body>
</html>
