<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Huang Zhiruike | Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Noto+Sans+SC:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary: #00d2ff;
            --primary-dark: #3a7bd5;
            --primary-glow: rgba(0, 210, 255, 0.6);
            --bg-dark: #020c1b;
            --card-bg: rgba(10, 25, 47, 0.75);
            --text-main: #e6f1ff;
            --text-sub: #8892b0;
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Noto Sans SC', 'JetBrains Mono', sans-serif;
            background: var(--bg-dark);
            background-image: 
                radial-gradient(circle at 15% 50%, rgba(0, 210, 255, 0.12) 0%, transparent 45%),
                radial-gradient(circle at 85% 30%, rgba(58, 123, 213, 0.12) 0%, transparent 45%);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            position: relative;
        }

        body::before {
            content: '';
            position: absolute;
            width: 200%;
            height: 200%;
            background-image: 
                linear-gradient(rgba(0, 210, 255, 0.03) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 210, 255, 0.03) 1px, transparent 1px);
            background-size: 40px 40px;
            transform: perspective(500px) rotateX(60deg) translateY(-100px) translateZ(-200px);
            animation: gridMove 20s linear infinite;
            z-index: -1;
            pointer-events: none;
        }

        @keyframes gridMove {
            0% { transform: perspective(500px) rotateX(60deg) translateY(0) translateZ(-200px); }
            100% { transform: perspective(500px) rotateX(60deg) translateY(40px) translateZ(-200px); }
        }

        .container {
            width: 90%;
            max-width: 900px;
            background: var(--card-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(0, 210, 255, 0.15);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.6), 0 0 20px rgba(0, 210, 255, 0.1);
            margin: 20px 0;
            position: relative;
            overflow: hidden;
        }

        header { text-align: center; margin-bottom: 30px; }

        .avatar-container {
            position: relative;
            width: 120px;
            height: 120px;
            margin: 0 auto 20px;
        }

        .avatar {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid var(--primary);
            box-shadow: 0 0 25px var(--primary-glow);
            animation: pulse-blue 3s infinite;
        }

        @keyframes pulse-blue {
            0% { box-shadow: 0 0 0 0 rgba(0, 210, 255, 0.4); }
            70% { box-shadow: 0 0 0 15px rgba(0, 210, 255, 0); }
            100% { box-shadow: 0 0 0 0 rgba(0, 210, 255, 0); }
        }

        h1 {
            font-size: 2.2rem;
            margin-bottom: 10px;
            background: linear-gradient(to right, #ffffff, var(--primary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 700;
        }

        .typing-text {
            font-family: 'JetBrains Mono', monospace;
            color: var(--primary);
            font-size: 1rem;
            min-height: 1.5em;
            text-shadow: 0 0 10px rgba(0, 210, 255, 0.5);
        }

        .lang-switch {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 30px 0;
        }

        .btn {
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(0, 210, 255, 0.3);
            color: var(--text-sub);
            padding: 10px 24px;
            border-radius: 30px;
            cursor: pointer;
            font-size: 0.95rem;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .btn:hover {
            background: rgba(0, 210, 255, 0.1);
            border-color: var(--primary);
            color: #fff;
            transform: translateY(-2px);
        }

        .btn.active {
            background: var(--primary);
            color: #020c1b;
            border-color: var(--primary);
            font-weight: bold;
            box-shadow: 0 0 20px var(--primary-glow);
        }

        .content-wrapper { position: relative; min-height: 300px; }

        .content-section {
            position: absolute;
            top: 0; left: 0; width: 100%;
            opacity: 0; visibility: hidden;
            transform: translateY(20px);
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .content-section.active {
            opacity: 1; visibility: visible;
            transform: translateY(0);
            position: relative;
        }

        .bio-card {
            background: rgba(255,255,255,0.02);
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 25px;
            border-left: 4px solid var(--primary);
        }

        .bio-list { list-style: none; margin-top: 15px; }
        .bio-list li {
            margin-bottom: 10px;
            display: flex;
            align-items: flex-start;
            gap: 10px;
            color: var(--text-sub);
        }
        .bio-list li i { color: var(--primary); margin-top: 5px; }
        .bio-list strong { color: var(--text-main); }

        .skills-container { text-align: center; margin: 30px 0; }
        .section-title {
            text-align: center;
            color: var(--text-main);
            margin-bottom: 20px;
            font-size: 1.2rem;
            text-transform: uppercase;
            letter-spacing: 2px;
        }

        .skills-grid {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 12px;
        }

        .skill-item {
            background: rgba(0, 210, 255, 0.05);
            border: 1px solid rgba(0, 210, 255, 0.2);
            padding: 8px 16px;
            border-radius: 8px;
            color: var(--primary);
            font-size: 0.9rem;
            transition: all 0.3s;
        }

        .skill-item:hover {
            background: var(--primary);
            color: #020c1b;
            transform: scale(1.05);
            box-shadow: 0 0 20px var(--primary-glow);
        }

        /* 统计图表区域样式 */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .stats-card {
            background: rgba(0,0,0,0.3);
            border-radius: 12px;
            padding: 10px;
            transition: transform 0.3s;
            border: 1px solid rgba(255,255,255,0.05);
            position: relative;
            min-height: 200px; /* 防止高度塌陷 */
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }
        
        .stats-card:hover {
            transform: translateY(-5px);
            border-color: rgba(0, 210, 255, 0.3);
        }

        .stats-card img {
            width: 100%;
            height: auto;
            border-radius: 8px;
            display: block;
            opacity: 0; /* 默认隐藏，加载成功后显示 */
            transition: opacity 0.5s ease;
        }

        .stats-card img.loaded {
            opacity: 1;
        }

        /* 加载失败时的备用样式 */
        .fallback-content {
            text-align: center;
            padding: 20px;
            display: none; /* 默认隐藏 */
            flex-direction: column;
            align-items: center;
            gap: 10px;
        }
        
        .stats-card.error .fallback-content {
            display: flex;
        }
        
        .stats-card.error img {
            display: none;
        }

        .fallback-icon {
            font-size: 2rem;
            color: var(--text-sub);
            margin-bottom: 10px;
        }

        .fallback-text {
            color: var(--text-sub);
            font-size: 0.9rem;
        }

        footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid rgba(255,255,255,0.05);
            color: var(--text-sub);
            font-size: 0.85rem;
        }

        .social-links { margin-bottom: 15px; }
        .social-links a {
            color: var(--text-sub);
            font-size: 1.5rem;
            margin: 0 10px;
            transition: all 0.3s;
            display: inline-block;
        }
        .social-links a:hover {
            color: var(--primary);
            transform: scale(1.2);
            text-shadow: 0 0 15px var(--primary-glow);
        }

        @media (max-width: 600px) {
            .container { padding: 20px; width: 95%; }
            h1 { font-size: 1.8rem; }
            .stats-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <div class="avatar-container">
            <!-- 请确保这里的 username 是你的真实 GitHub ID -->
            <img src="https://avatars.githubusercontent.com/u/RECO?s=400&v=4" alt="Avatar" class="avatar" onerror="this.src='https://ui-avatars.com/api/?name=Huang+Zhiruike&background=00d2ff&color=fff&size=200'">
        </div>
        <h1 id="name-title">Huang Zhiruike</h1>
        <div class="typing-text" id="typing-effect"></div>
    </header>

    <div class="lang-switch">
        <button class="btn active" onclick="switchLang('zh')"><i class="fas fa-language"></i> 中文</button>
        <button class="btn" onclick="switchLang('en')"><i class="fas fa-globe"></i> English</button>
    </div>

    <div class="content-wrapper">
        <!-- 中文版 -->
        <div id="zh-content" class="content-section active">
            <div class="bio-card">
                <h3 style="color: var(--primary); margin-bottom: 10px;"><i class="fas fa-user-graduate"></i> 关于我</h3>
                <p>你好！我是黄之睿可，华东政法大学商学院金融专业学生。热爱探索数据背后的逻辑。</p>
                <ul class="bio-list">
                    <li><i class="fas fa-code"></i> <strong>正在钻研：</strong> Python 数据分析、系统设计。</li>
                    <li><i class="fas fa-seedling"></i> <strong>当前学习：</strong> 金融工程、AWS、篮球。</li>
                    <li><i class="fas fa-handshake"></i> <strong>寻求合作：</strong> Python 项目与量化策略。</li>
                </ul>
            </div>

            <div class="skills-container">
                <h4 class="section-title"><i class="fas fa-tools"></i> 技术栈</h4>
                <div class="skills-grid">
                    <span class="skill-item">Python</span>
                    <span class="skill-item">Anaconda</span>
                    <span class="skill-item">Jupyter</span>
                    <span class="skill-item">AWS</span>
                    <span class="skill-item">Photoshop</span>
                    <span class="skill-item">Git</span>
                </div>
            </div>

            <h4 class="section-title"><i class="fas fa-chart-bar"></i> 数据概览</h4>
            <div class="stats-grid">
                <!-- 卡片 1: 总览 -->
                <div class="stats-card" id="card-stats-zh">
                    <img src="" alt="GitHub Stats" onload="this.classList.add('loaded')" onerror="showFallback(this, 'stats-fallback-zh')">
                    <div id="stats-fallback-zh" class="fallback-content">
                        <i class="fas fa-chart-line fallback-icon"></i>
                        <span class="fallback-text">活跃于代码世界<br>Active in Coding</span>
                        <div style="margin-top:10px; font-size:0.8rem; opacity:0.7;">Python | Finance | Data</div>
                    </div>
                </div>
                <!-- 卡片 2: 连击 -->
                <div class="stats-card" id="card-streak-zh">
                    <img src="" alt="GitHub Streak" onload="this.classList.add('loaded')" onerror="showFallback(this, 'streak-fallback-zh')">
                    <div id="streak-fallback-zh" class="fallback-content">
                        <i class="fas fa-fire fallback-icon"></i>
                        <span class="fallback-text">持续学习中<br>Keep Learning</span>
                        <div style="margin-top:10px; font-size:0.8rem; opacity:0.7;">Day by Day Progress</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- 英文版 -->
        <div id="en-content" class="content-section">
            <div class="bio-card">
                <h3 style="color: var(--primary); margin-bottom: 10px;"><i class="fas fa-user-graduate"></i> About Me</h3>
                <p>Hi! I'm Huang Zhiruike, a Finance major at ECUPL. Passionate about data logic and tech.</p>
                <ul class="bio-list">
                    <li><i class="fas fa-code"></i> <strong>Working on:</strong> Python Data Analysis & System Design.</li>
                    <li><i class="fas fa-seedling"></i> <strong>Learning:</strong> Financial Engineering, AWS, Basketball.</li>
                    <li><i class="fas fa-handshake"></i> <strong>Collab:</strong> Open to Python projects & Quant strategies.</li>
                </ul>
            </div>

            <div class="skills-container">
                <h4 class="section-title"><i class="fas fa-tools"></i> Tech Stack</h4>
                <div class="skills-grid">
                    <span class="skill-item">Python</span>
                    <span class="skill-item">Anaconda</span>
                    <span class="skill-item">Jupyter</span>
                    <span class="skill-item">AWS</span>
                    <span class="skill-item">Photoshop</span>
                    <span class="skill-item">Git</span>
                </div>
            </div>

            <h4 class="section-title"><i class="fas fa-chart-bar"></i> Statistics</h4>
            <div class="stats-grid">
                <!-- 卡片 1: 总览 -->
                <div class="stats-card" id="card-stats-en">
                    <img src="" alt="GitHub Stats" onload="this.classList.add('loaded')" onerror="showFallback(this, 'stats-fallback-en')">
                    <div id="stats-fallback-en" class="fallback-content">
                        <i class="fas fa-chart-line fallback-icon"></i>
                        <span class="fallback-text">Active in Coding</span>
                        <div style="margin-top:10px; font-size:0.8rem; opacity:0.7;">Python | Finance | Data</div>
                    </div>
                </div>
                <!-- 卡片 2: 连击 -->
                <div class="stats-card" id="card-streak-en">
                    <img src="" alt="GitHub Streak" onload="this.classList.add('loaded')" onerror="showFallback(this, 'streak-fallback-en')">
                    <div id="streak-fallback-en" class="fallback-content">
                        <i class="fas fa-fire fallback-icon"></i>
                        <span class="fallback-text">Keep Learning</span>
                        <div style="margin-top:10px; font-size:0.8rem; opacity:0.7;">Day by Day Progress</div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <footer>
        <div class="social-links">
            <a href="https://github.com/RECO" target="_blank"><i class="fab fa-github"></i></a>
            <a href="mailto:3537986832@qq.com"><i class="fas fa-envelope"></i></a>
            <a href="https://instagram.com/Reco-sea" target="_blank"><i class="fab fa-instagram"></i></a>
        </div>
        <p>&copy; 2026 Huang Zhiruike. Crafted with <i class="fas fa-heart" style="color: var(--primary);"></i> & Code.</p>
    </footer>
</div>

<script>
    // ⚠️ 重要：请将此处的 'RECO' 替换为你真实的 GitHub 用户名 (区分大小写)
    const GITHUB_USERNAME = 'Reco-sea'; 

    // 动态生成图片链接，增加 cache 参数防止缓存失效
    function getStatsUrl(lang) {
        return `https://github-readme-stats.vercel.app/api?username=${GITHUB_USERNAME}&show_icons=true&theme=blue-green&locale=${lang}&title_color=00d2ff&icon_color=00d2ff&bg_color=0a192f&hide_rank=false&cache_seconds=3600`;
    }

    function getStreakUrl(lang) {
        return `https://github-readme-streak-stats.herokuapp.com/?user=${GITHUB_USERNAME}&locale=${lang}&theme=blue-green&fire=00d2ff&ring=00d2ff&background=0a192f&cache_seconds=3600`;
    }

    // 初始化图片源
    function initImages() {
        // 中文
        document.querySelector('#card-stats-zh img').src = getStatsUrl('zh-CN');
        document.querySelector('#card-streak-zh img').src = getStreakUrl('zh-CN');
        // 英文
        document.querySelector('#card-stats-en img').src = getStatsUrl('en');
        document.querySelector('#card-streak-en img').src = getStreakUrl('en');
    }

    // 图片加载失败处理：显示备用内容
    function showFallback(imgElement, fallbackId) {
        const card = imgElement.parentElement;
        card.classList.add('error');
        console.log("Image load failed, showing fallback for:", fallbackId);
    }

    // 打字机效果
    const texts = {
        zh: ["金融系学生 | Python 爱好者", "华东政法大学 | 24004班", "探索金融与科技的边界"],
        en: ["Finance Student | Python Enthusiast", "ECUPL | Class 24004", "Exploring the Edge of Finance & Tech"]
    };
    
    let currentLang = 'zh';
    let textIndex = 0, charIndex = 0, isDeleting = false, typingSpeed = 100;

    function typeEffect() {
        const currentText = texts[currentLang][textIndex];
        const element = document.getElementById('typing-effect');
        
        if (isDeleting) {
            element.textContent = currentText.substring(0, charIndex - 1);
            charIndex--;
            typingSpeed = 50;
        } else {
            element.textContent = currentText.substring(0, charIndex + 1);
            charIndex++;
            typingSpeed = 100;
        }

        if (!isDeleting && charIndex === currentText.length) {
            isDeleting = true;
            typingSpeed = 2000;
        } else if (isDeleting && charIndex === 0) {
            isDeleting = false;
            textIndex = (textIndex + 1) % texts[currentLang].length;
            typingSpeed = 500;
        }
        setTimeout(typeEffect, typingSpeed);
    }

    function switchLang(lang) {
        currentLang = lang;
        const zhContent = document.getElementById('zh-content');
        const enContent = document.getElementById('en-content');
        const buttons = document.querySelectorAll('.btn');

        textIndex = 0; charIndex = 0; isDeleting = false;
        
        if (lang === 'zh') {
            zhContent.classList.add('active');
            enContent.classList.remove('active');
            buttons[0].classList.add('active');
            buttons[1].classList.remove('active');
        } else {
            zhContent.classList.remove('active');
            enContent.classList.add('active');
            buttons[0].classList.remove('active');
            buttons[1].classList.add('active');
        }
    }

    document.addEventListener('DOMContentLoaded', () => {
        initImages();
        typeEffect();
        const img = document.querySelector('.avatar');
        img.onerror = function() {
            this.src = 'https://ui-avatars.com/api/?name=Huang+Zhiruike&background=00d2ff&color=fff&size=200';
        };
    });
</script>

</body>
</html>
