
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Huang Zhiruike | Portfolio</title>
    <!-- 引入谷歌字体 -->
    <link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Noto+Sans+SC:wght@400;700&display=swap" rel="stylesheet">
    <!-- 引入图标库 -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            /* 浅蓝色系核心变量 */
            --primary: #00d2ff;       /* 亮青色 */
            --primary-dark: #3a7bd5;  /* 深蓝色 */
            --primary-glow: rgba(0, 210, 255, 0.6);
            --bg-dark: #020c1b;       /* 深海军蓝背景 */
            --card-bg: rgba(10, 25, 47, 0.75);
            --text-main: #e6f1ff;
            --text-sub: #8892b0;
            --gradient: linear-gradient(135deg, #020c1b, #0a192f, #112240);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Noto Sans SC', 'JetBrains Mono', sans-serif;
            background: var(--bg-dark);
            /* 浅蓝色径向光晕背景 */
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

        /* 动态背景网格 - 冰蓝色 */
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
            border: 1px solid rgba(0, 210, 255, 0.15); /* 浅蓝边框 */
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.6), 0 0 20px rgba(0, 210, 255, 0.1);
            margin: 20px 0;
            position: relative;
            overflow: hidden;
            transition: transform 0.3s ease;
        }

        /* 顶部装饰条 - 渐变蓝 */
        .container::top {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0;
            height: 4px;
            background: linear-gradient(90deg, transparent, var(--primary), var(--primary-dark), transparent);
        }

        header {
            text-align: center;
            margin-bottom: 30px;
        }

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
            /* 文字渐变：白 -> 浅蓝 */
            background: linear-gradient(to right, #ffffff, var(--primary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            font-weight: 700;
            text-shadow: 0 0 30px rgba(0, 210, 255, 0.3);
        }

        .typing-text {
            font-family: 'JetBrains Mono', monospace;
            color: var(--primary);
            font-size: 1rem;
            min-height: 1.5em;
            text-shadow: 0 0 10px rgba(0, 210, 255, 0.5);
        }

        /* 切换按钮组 */
        .lang-switch {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 30px 0;
            position: relative;
            z-index: 10;
        }

        .btn {
            background: rgba(255,255,255,0.03);
            border: 1px solid rgba(0, 210, 255, 0.3);
            color: var(--text-sub);
            padding: 10px 24px;
            border-radius: 30px;
            cursor: pointer;
            font-size: 0.95rem;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .btn:hover {
            background: rgba(0, 210, 255, 0.1);
            border-color: var(--primary);
            color: #fff;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 210, 255, 0.2);
        }

        .btn.active {
            background: var(--primary);
            color: #020c1b; /* 深色文字以保证对比度 */
            border-color: var(--primary);
            font-weight: bold;
            box-shadow: 0 0 20px var(--primary-glow);
        }

        /* 内容区域 */
        .content-wrapper {
            position: relative;
            min-height: 300px;
        }

        .content-section {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            opacity: 0;
            visibility: hidden;
            transform: translateY(20px);
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .content-section.active {
            opacity: 1;
            visibility: visible;
            transform: translateY(0);
            position: relative;
        }

        .bio-card {
            background: rgba(255,255,255,0.02);
            border-radius: 12px;
            padding: 25px;
            margin-bottom: 25px;
            border-left: 4px solid var(--primary);
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
        }

        .bio-list {
            list-style: none;
            margin-top: 15px;
        }

        .bio-list li {
            margin-bottom: 10px;
            display: flex;
            align-items: flex-start;
            gap: 10px;
            color: var(--text-sub);
        }

        .bio-list li i {
            color: var(--primary);
            margin-top: 5px;
            filter: drop-shadow(0 0 5px var(--primary-glow));
        }

        .bio-list strong {
            color: var(--text-main);
        }

        /* 技能标签 */
        .skills-container {
            text-align: center;
            margin: 30px 0;
        }
        
        .section-title {
            text-align: center;
            color: var(--text-main);
            margin-bottom: 20px;
            font-size: 1.2rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            text-shadow: 0 0 10px rgba(0, 210, 255, 0.3);
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
            cursor: default;
        }

        .skill-item:hover {
            background: var(--primary);
            color: #020c1b;
            transform: scale(1.05);
            box-shadow: 0 0 20px var(--primary-glow);
            border-color: var(--primary);
        }

        /* 统计图表容器 */
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
            transition: transform 0.3s, box-shadow 0.3s;
            border: 1px solid rgba(255,255,255,0.05);
        }
        
        .stats-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0, 210, 255, 0.15);
            border-color: rgba(0, 210, 255, 0.3);
        }

        .stats-card img {
            width: 100%;
            height: auto;
            border-radius: 8px;
        }

        footer {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid rgba(255,255,255,0.05);
            color: var(--text-sub);
            font-size: 0.85rem;
        }

        .social-links {
            margin-bottom: 15px;
        }

        .social-links a {
            color: var(--text-sub);
            font-size: 1.5rem;
            margin: 0 10px;
            transition: color 0.3s, transform 0.3s, text-shadow 0.3s;
            display: inline-block;
        }

        .social-links a:hover {
            color: var(--primary);
            transform: scale(1.2);
            text-shadow: 0 0 15px var(--primary-glow);
        }

        /* 移动端适配 */
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
            <!-- 自动获取 GitHub 头像 -->
            <img src="https://avatars.githubusercontent.com/u/RECO?s=400&v=4" alt="Avatar" class="avatar" onerror="this.src='https://ui-avatars.com/api/?name=Huang+Zhiruike&background=00d2ff&color=fff&size=200'">
        </div>
        <h1 id="name-title">Huang Zhiruike</h1>
        <div class="typing-text" id="typing-effect"></div>
    </header>

    <div class="lang-switch">
        <button class="btn active" onclick="switchLang('zh')">
            <i class="fas fa-language"></i> 中文
        </button>
        <button class="btn" onclick="switchLang('en')">
            <i class="fas fa-globe"></i> English
        </button>
    </div>

    <div class="content-wrapper">
        <!-- 中文版 -->
        <div id="zh-content" class="content-section active">
            <div class="bio-card">
                <h3 style="color: var(--primary); margin-bottom: 10px; text-shadow: 0 0 10px rgba(0,210,255,0.4);"><i class="fas fa-user-graduate"></i> 关于我</h3>
                <p>你好！我是黄之睿可，华东政法大学商学院金融专业学生。热爱探索数据背后的逻辑，致力于成为懂技术的金融人。</p>
                <ul class="bio-list">
                    <li><i class="fas fa-code"></i> <strong>正在钻研：</strong> Python 数据分析、系统设计与量化策略。</li>
                    <li><i class="fas fa-seedling"></i> <strong>当前学习：</strong> 金融工程、AWS 云服务、篮球战术。</li>
                    <li><i class="fas fa-handshake"></i> <strong>寻求合作：</strong> 欢迎一起开发 Python 项目或交流金融见解。</li>
                    <li><i class="fas fa-bolt"></i> <strong>趣味标签：</strong> 幽默随和 · 终身学习者 · 摄影爱好者</li>
                </ul>
            </div>

            <div class="skills-container">
                <h4 class="section-title"><i class="fas fa-tools"></i> 技术栈</h4>
                <div class="skills-grid">
                    <span class="skill-item"><i class="fab fa-python"></i> Python</span>
                    <span class="skill-item"><i class="fas fa-database"></i> Anaconda</span>
                    <span class="skill-item"><i class="fas fa-book"></i> Jupyter</span>
                    <span class="skill-item"><i class="fab fa-aws"></i> AWS</span>
                    <span class="skill-item"><i class="fas fa-paint-brush"></i> Photoshop</span>
                    <span class="skill-item"><i class="fab fa-git-alt"></i> Git</span>
                    <span class="skill-item"><i class="fas fa-chart-line"></i> Finance</span>
                </div>
            </div>

            <h4 class="section-title"><i class="fas fa-chart-bar"></i> 数据概览</h4>
            <div class="stats-grid">
                <div class="stats-card">
                    <!-- 统计图主题改为 blue-green 以匹配浅蓝风格 -->
                    <img src="https://github-readme-stats.vercel.app/api?username=RECO&show_icons=true&theme=blue-green&locale=zh-CN&title_color=00d2ff&icon_color=00d2ff&bg_color=0a192f&hide_rank=false" alt="Stats">
                </div>
                <div class="stats-card">
                    <img src="https://github-readme-streak-stats.herokuapp.com/?user=RECO&locale=zh-CN&theme=blue-green&fire=00d2ff&ring=00d2ff&background=0a192f" alt="Streak">
                </div>
            </div>
        </div>

        <!-- 英文版 -->
        <div id="en-content" class="content-section">
            <div class="bio-card">
                <h3 style="color: var(--primary); margin-bottom: 10px; text-shadow: 0 0 10px rgba(0,210,255,0.4);"><i class="fas fa-user-graduate"></i> About Me</h3>
                <p>Hi! I'm Huang Zhiruike, a Finance major at East China University of Political Science and Law. Passionate about exploring the logic behind data and aspiring to be a finance professional with technical expertise.</p>
                <ul class="bio-list">
                    <li><i class="fas fa-code"></i> <strong>Working on:</strong> Python Data Analysis, System Design & Quant Strategies.</li>
                    <li><i class="fas fa-seedling"></i> <strong>Learning:</strong> Financial Engineering, AWS Cloud, Basketball Tactics.</li>
                    <li><i class="fas fa-handshake"></i> <strong>Collab:</strong> Open to Python projects and financial insights exchange.</li>
                    <li><i class="fas fa-bolt"></i> <strong>Fun Fact:</strong> Humorous · Lifelong Learner · Photography Enthusiast</li>
                </ul>
            </div>

            <div class="skills-container">
                <h4 class="section-title"><i class="fas fa-tools"></i> Tech Stack</h4>
                <div class="skills-grid">
                    <span class="skill-item"><i class="fab fa-python"></i> Python</span>
                    <span class="skill-item"><i class="fas fa-database"></i> Anaconda</span>
                    <span class="skill-item"><i class="fas fa-book"></i> Jupyter</span>
                    <span class="skill-item"><i class="fab fa-aws"></i> AWS</span>
                    <span class="skill-item"><i class="fas fa-paint-brush"></i> Photoshop</span>
                    <span class="skill-item"><i class="fab fa-git-alt"></i> Git</span>
                    <span class="skill-item"><i class="fas fa-chart-line"></i> Finance</span>
                </div>
            </div>

            <h4 class="section-title"><i class="fas fa-chart-bar"></i> Statistics</h4>
            <div class="stats-grid">
                <div class="stats-card">
                    <img src="https://github-readme-stats.vercel.app/api?username=RECO&show_icons=true&theme=blue-green&locale=en&title_color=00d2ff&icon_color=00d2ff&bg_color=0a192f&hide_rank=false" alt="Stats">
                </div>
                <div class="stats-card">
                    <img src="https://github-readme-streak-stats.herokuapp.com/?user=RECO&locale=en&theme=blue-green&fire=00d2ff&ring=00d2ff&background=0a192f" alt="Streak">
                </div>
            </div>
        </div>
    </div>

    <footer>
        <div class="social-links">
            <a href="https://github.com/RECO" target="_blank"><i class="fab fa-github"></i></a>
            <a href="mailto:3537986832@qq.com"><i class="fas fa-envelope"></i></a>
            <a href="https://instagram.com/Reco-sea" target="_blank"><i class="fab fa-instagram"></i></a>
            <a href="https://fb.com/Reco Huang" target="_blank"><i class="fab fa-facebook"></i></a>
        </div>
        <p>&copy; 2026 Huang Zhiruike. Crafted with <i class="fas fa-heart" style="color: var(--primary); text-shadow: 0 0 10px var(--primary-glow);"></i> & Code.</p>
    </footer>
</div>

<script>
    // 打字机效果配置
    const texts = {
        zh: ["金融系学生 | Python 爱好者", "华东政法大学 | 24004班", "探索金融与科技的边界"],
        en: ["Finance Student | Python Enthusiast", "ECUPL | Class 24004", "Exploring the Edge of Finance & Tech"]
    };
    
    let currentLang = 'zh';
    let textIndex = 0;
    let charIndex = 0;
    let isDeleting = false;
    let typingSpeed = 100;

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
            typingSpeed = 2000; // 停顿时间
        } else if (isDeleting && charIndex === 0) {
            isDeleting = false;
            textIndex = (textIndex + 1) % texts[currentLang].length;
            typingSpeed = 500;
        }

        setTimeout(typeEffect, typingSpeed);
    }

    // 语言切换逻辑
    function switchLang(lang) {
        currentLang = lang;
        const zhContent = document.getElementById('zh-content');
        const enContent = document.getElementById('en-content');
        const buttons = document.querySelectorAll('.btn');

        // 重置打字机状态以匹配新语言
        textIndex = 0;
        charIndex = 0;
        isDeleting = false;
        
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

    // 初始化
    document.addEventListener('DOMContentLoaded', () => {
        typeEffect();
        // 尝试获取真实头像，如果失败则使用默认
        const img = document.querySelector('.avatar');
        img.onerror = function() {
            this.src = 'https://ui-avatars.com/api/?name=Huang+Zhiruike&background=00d2ff&color=fff&size=200';
        };
    });
</script>

</body>
</html>
