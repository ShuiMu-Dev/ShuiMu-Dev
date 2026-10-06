<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ShuiMu-Dev · 个人主页</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', 'Fira Code', 'Inter', system-ui, -apple-system, BlinkMacSystemFont, sans-serif;
      background: #0b0e14;
      color: #c9d1d9;
      line-height: 1.6;
      padding: 1.5rem 1rem;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    .main-container {
      max-width: 1100px;
      width: 100%;
    }

    /* 卡片通用样式 */
    .glass-card {
      background: rgba(13, 17, 23, 0.85);
      backdrop-filter: blur(6px);
      border-radius: 2rem;
      border: 1px solid rgba(112, 165, 253, 0.2);
      box-shadow: 0 20px 35px -10px rgba(0, 0, 0, 0.7), 0 0 0 1px rgba(112, 165, 253, 0.1);
      padding: 1.5rem 2rem;
      transition: all 0.3s ease;
    }

    .glass-card:hover {
      border-color: rgba(112, 165, 253, 0.5);
      box-shadow: 0 20px 40px -8px #70a5fd20, 0 0 0 1px #70a5fd40;
    }

    /* 头部波浪 */
    .wave-header {
      width: 100%;
      height: 220px;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
      border-radius: 2.5rem 2.5rem 1.5rem 1.5rem;
      position: relative;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      margin-bottom: 2rem;
      box-shadow: 0 25px 40px -15px #000000aa;
      animation: waveGlow 8s infinite alternate;
    }

    @keyframes waveGlow {
      0% { filter: brightness(1) drop-shadow(0 0 10px #667eea80); }
      100% { filter: brightness(1.1) drop-shadow(0 0 25px #f093fb80); }
    }

    .wave-header::before {
      content: "";
      position: absolute;
      inset: 0;
      background-image: radial-gradient(white 1px, transparent 1px);
      background-size: 40px 40px;
      opacity: 0.25;
      animation: twinkle 4s infinite alternate;
    }

    @keyframes twinkle {
      0% { opacity: 0.2; }
      100% { opacity: 0.5; }
    }

    .wave-header h1 {
      font-size: clamp(3rem, 12vw, 5rem);
      font-weight: 800;
      color: white;
      text-shadow: 0 0 20px #ffffffcc, 0 0 40px #a58aff;
      letter-spacing: -0.02em;
      z-index: 3;
      margin-bottom: 0.2rem;
      animation: fadeSlide 1.2s ease;
    }

    .wave-header p {
      font-size: 1.2rem;
      color: #ffffffdd;
      font-weight: 500;
      letter-spacing: 2px;
      text-shadow: 0 0 15px #f093fb;
      z-index: 3;
      background: rgba(0, 0, 0, 0.2);
      padding: 0.3rem 1.2rem;
      border-radius: 40px;
      backdrop-filter: blur(3px);
      animation: fadeSlide 1.4s ease;
    }

    @keyframes fadeSlide {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* 打字动画 */
    .typing-wrapper {
      display: flex;
      justify-content: center;
      margin: 0.5rem 0 2rem;
    }

    .typing-box {
      background: #0d1117dd;
      backdrop-filter: blur(6px);
      border-radius: 60px;
      padding: 0.6rem 2rem;
      border: 1px solid #70a5fd55;
      box-shadow: 0 0 15px #70a5fd30;
      display: inline-flex;
      align-items: center;
      gap: 4px;
    }

    .typing-text {
      font-family: 'Fira Code', 'Courier New', monospace;
      font-weight: 600;
      font-size: 1.5rem;
      background: linear-gradient(90deg, #70a5fd, #bf91f3, #f093fb);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      white-space: nowrap;
      overflow: hidden;
      border-right: 3px solid #70a5fd;
      animation: typing 6s steps(40) infinite, blink 0.8s step-end infinite;
      width: 0;
    }

    @keyframes typing {
      0% { width: 0; }
      25% { width: 100%; }
      75% { width: 100%; }
      100% { width: 0; }
    }

    @keyframes blink {
      from, to { border-color: transparent; }
      50% { border-color: #70a5fd; }
    }

    /* 头像区域 */
    .avatar-section {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 1rem 0 2rem;
    }

    .avatar-ring {
      width: 160px;
      height: 160px;
      border-radius: 50%;
      padding: 6px;
      background: linear-gradient(135deg, #70a5fd, #bf91f3, #f093fb);
      box-shadow: 0 0 35px #70a5fd, 0 0 60px #bf91f380;
      animation: pulseGlow 3s infinite alternate;
    }

    @keyframes pulseGlow {
      0% { box-shadow: 0 0 25px #70a5fd, 0 0 45px #bf91f380; }
      100% { box-shadow: 0 0 40px #70a5fd, 0 0 75px #f093fb; }
    }

    .avatar-ring img {
      width: 100%;
      height: 100%;
      border-radius: 50%;
      object-fit: cover;
      border: 3px solid #0d1117;
      display: block;
    }

    .avatar-section h3 {
      font-size: 2rem;
      margin-top: 1rem;
      color: #ffffff;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 8px;
      flex-wrap: wrap;
      justify-content: center;
    }

    .avatar-section h3 span {
      background: linear-gradient(45deg, #70a5fd, #bf91f3);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      font-weight: 800;
    }

    .avatar-section p {
      color: #8b949e;
      font-size: 1.1rem;
      margin-top: 0.2rem;
      background: #0d1117aa;
      padding: 0.3rem 1.2rem;
      border-radius: 30px;
      backdrop-filter: blur(4px);
    }

    /* 社交按钮 */
    .social-buttons {
      display: flex;
      justify-content: center;
      gap: 1rem;
      flex-wrap: wrap;
      margin: 1.5rem 0 1rem;
    }

    .btn-social {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 0.7rem 1.8rem;
      border-radius: 60px;
      font-weight: 600;
      font-size: 1rem;
      background: #161b22;
      color: #c9d1d9;
      border: 1px solid #30363d;
      transition: 0.2s;
      text-decoration: none;
      box-shadow: 0 4px 12px #00000040;
      letter-spacing: 0.5px;
    }

    .btn-social svg {
      width: 20px;
      height: 20px;
      fill: currentColor;
    }

    .btn-social:hover {
      background: #1f2630;
      border-color: #70a5fd;
      color: #70a5fd;
      transform: translateY(-3px);
      box-shadow: 0 12px 20px -8px #70a5fd;
    }

    /* 统计徽章 */
    .stats-badges {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 0.8rem;
      margin: 1.8rem 0;
    }

    .badge {
      background: #0d1117;
      border: 1px solid #30363d;
      border-radius: 40px;
      padding: 0.4rem 1.4rem;
      font-weight: 600;
      font-size: 0.9rem;
      display: flex;
      align-items: center;
      gap: 8px;
      color: #c9d1d9;
      box-shadow: 0 5px 10px #00000030;
      transition: 0.2s;
      letter-spacing: 0.3px;
    }

    .badge:hover {
      border-color: #70a5fd;
      box-shadow: 0 0 15px #70a5fd60;
    }

    .badge svg {
      width: 16px;
      height: 16px;
      fill: #8b949e;
    }

    .badge .accent {
      color: #70a5fd;
      font-weight: 700;
      margin-left: 4px;
    }

    /* 技术栈 */
    .tech-stack {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1rem;
      margin: 1.5rem 0 1rem;
    }

    .tech-item {
      background: #0d1117;
      border: 1px solid #30363d;
      border-radius: 40px;
      padding: 0.6rem 1.6rem;
      display: flex;
      align-items: center;
      gap: 12px;
      font-weight: 600;
      color: #e6edf3;
      font-size: 1.1rem;
      transition: 0.25s;
      box-shadow: 0 4px 12px #00000030;
    }

    .tech-item:hover {
      border-color: #70a5fd;
      transform: translateY(-4px);
      box-shadow: 0 18px 25px -12px #70a5fd;
    }

    .tech-item img {
      width: 26px;
      height: 26px;
      filter: drop-shadow(0 0 6px #70a5fd80);
    }

    .skill-icons-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1.2rem;
      margin: 0.5rem 0 2rem;
    }

    .skill-icon {
      background: #0d1117;
      border: 1px solid #30363d;
      border-radius: 18px;
      padding: 0.8rem 1.5rem;
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 500;
      font-family: 'Fira Code', monospace;
      font-size: 1.1rem;
      color: #c9d1d9;
      transition: 0.2s;
    }

    .skill-icon:hover {
      border-color: #bf91f3;
      background: #1a1f2b;
      box-shadow: 0 0 25px #bf91f380;
    }

    /* 数据卡片 */
    .stats-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1.8rem;
      justify-content: center;
      margin: 2rem 0;
    }

    .stat-card {
      background: #0d1117;
      border-radius: 2rem;
      border: 1px solid #30363d;
      padding: 1.8rem 1.8rem;
      flex: 1 1 280px;
      max-width: 380px;
      box-shadow: 0 20px 30px -15px #000000;
      transition: 0.3s;
      display: flex;
      flex-direction: column;
    }

    .stat-card:hover {
      border-color: #70a5fd;
      box-shadow: 0 0 35px #70a5fd30;
    }

    .stat-title {
      font-size: 1.2rem;
      font-weight: 600;
      color: #70a5fd;
      margin-bottom: 1.2rem;
      display: flex;
      align-items: center;
      gap: 8px;
      letter-spacing: 0.5px;
      border-bottom: 1px solid #21262d;
      padding-bottom: 0.8rem;
    }

    .stat-row {
      display: flex;
      justify-content: space-between;
      padding: 0.6rem 0;
      border-bottom: 1px dashed #21262d;
      font-size: 1rem;
    }

    .stat-row:last-child {
      border-bottom: none;
    }

    .stat-label {
      color: #8b949e;
    }

    .stat-value {
      font-weight: 700;
      color: #e6edf3;
      font-family: 'Fira Code', monospace;
    }

    .stat-value.accent {
      color: #f7b32b;
    }

    .streak-days {
      font-size: 2.5rem;
      font-weight: 800;
      background: linear-gradient(135deg, #70a5fd, #f093fb);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      line-height: 1.2;
    }

    /* 奖杯行 */
    .trophy-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1.5rem;
      margin: 1.5rem 0 2rem;
    }

    .trophy-item {
      background: #0d1117;
      border: 1px solid #30363d;
      border-radius: 30px;
      padding: 0.6rem 1.8rem;
      display: flex;
      align-items: center;
      gap: 8px;
      font-weight: 500;
      color: #c9d1d9;
      transition: 0.2s;
      font-size: 1rem;
    }

    .trophy-item span {
      font-size: 1.5rem;
      filter: drop-shadow(0 0 12px #f7b32b);
    }

    .trophy-item:hover {
      border-color: #f7b32b;
      background: #1a1f2b;
    }

    /* 名言 */
    .quote-box {
      background: linear-gradient(145deg, #0d1117, #10161f);
      border-left: 6px solid #70a5fd;
      border-radius: 1.5rem;
      padding: 1.8rem 2rem;
      margin: 1.5rem 0;
      text-align: center;
      font-style: italic;
      color: #d0d7de;
      box-shadow: 0 15px 30px -10px #000000;
      position: relative;
    }

    .quote-box::before {
      content: "“";
      font-size: 5rem;
      position: absolute;
      left: 15px;
      top: -20px;
      color: #70a5fd40;
      font-family: serif;
    }

    .quote-text {
      font-size: 1.3rem;
      font-weight: 400;
      line-height: 1.6;
      margin-bottom: 0.8rem;
    }

    .quote-author {
      color: #8b949e;
      font-style: normal;
      font-weight: 500;
    }

    /* 页脚波浪 */
    .wave-footer {
      width: 100%;
      height: 130px;
      background: linear-gradient(135deg, #f093fb, #764ba2, #667eea);
      border-radius: 1.5rem 1.5rem 2.5rem 2.5rem;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top: 2.5rem;
      color: white;
      font-size: 1.4rem;
      font-weight: 600;
      text-shadow: 0 0 15px #ffffffaa;
      letter-spacing: 1px;
      position: relative;
      overflow: hidden;
      box-shadow: 0 -10px 30px #00000060;
    }

    .wave-footer::after {
      content: "";
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at 20% 30%, #ffffff30 0%, transparent 50%);
      animation: shimmer 6s infinite alternate;
    }

    @keyframes shimmer {
      0% { opacity: 0.3; transform: translateX(-10px); }
      100% { opacity: 0.8; transform: translateX(10px); }
    }

    /* 通用标题 */
    .section-title {
      text-align: center;
      font-size: 2rem;
      font-weight: 700;
      margin: 2.5rem 0 1rem;
      background: linear-gradient(90deg, #70a5fd, #bf91f3, #f093fb);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      letter-spacing: -0.5px;
      position: relative;
    }

    .section-title::after {
      content: "";
      display: block;
      width: 80px;
      height: 4px;
      background: linear-gradient(90deg, #70a5fd, #f093fb);
      margin: 0.5rem auto 0;
      border-radius: 4px;
    }

    @media (max-width: 650px) {
      body { padding: 1rem 0.8rem; }
      .glass-card { padding: 1rem 1.2rem; }
      .wave-header h1 { font-size: 2.8rem; }
      .typing-text { font-size: 1rem; }
      .stat-card { padding: 1.2rem; }
    }
  </style>
</head>
<body>
  <div class="main-container">
    <!-- 头部 -->
    <div class="wave-header">
      <h1>ShuiMu-Dev</h1>
      <p>Minecraft Developer</p>
    </div>

    <!-- 打字动画 -->
    <div class="typing-wrapper">
      <div class="typing-box">
        <div class="typing-text">Minecraft Developer</div>
      </div>
    </div>

    <!-- 头像 -->
    <div class="avatar-section">
      <div class="avatar-ring">
        <img src="https://github.com/ShuiMu-Dev.png" alt="ShuiMu-Dev avatar" loading="lazy">
      </div>
      <h3>Hi there, I'm <span>ShuiMu-Dev</span></h3>
      <p>Minecraft Developer | China 🇨🇳 | Lazy Developer</p>
    </div>

    <!-- 社交按钮 -->
    <div class="social-buttons">
      <a href="https://github.com/ShuiMu-Dev" class="btn-social" target="_blank" rel="noopener">
        <svg viewBox="0 0 24 24"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.3 3.438 9.8 8.205 11.387.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61-.546-1.387-1.333-1.756-1.333-1.756-1.09-.745.083-.73.083-.73 1.205.085 1.84 1.237 1.84 1.237 1.07 1.834 2.807 1.304 3.492.997.108-.775.418-1.305.762-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.468-2.38 1.235-3.22-.123-.3-.535-1.52.117-3.16 0 0 1.008-.322 3.3 1.23.96-.267 1.98-.4 3-.405 1.02.005 2.04.138 3 .405 2.29-1.552 3.297-1.23 3.297-1.23.653 1.64.24 2.86.118 3.16.768.84 1.233 1.91 1.233 3.22 0 4.61-2.804 5.62-5.476 5.92.43.37.824 1.102.824 2.22 0 1.602-.015 2.894-.015 3.287 0 .322.216.694.825.576C20.565 21.796 24 17.3 24 12c0-6.63-5.37-12-12-12z"/></svg>
        GitHub
      </a>
      <a href="mailto:MC-ShuiMu@outlook.com" class="btn-social">
        <svg viewBox="0 0 24 24"><path d="M12 12.713l-11.985-9.713h23.97l-11.985 9.713zm0 2.574l-12-9.725v15.438h24v-15.438l-12 9.725z"/></svg>
        Outlook
      </a>
    </div>

    <!-- 统计徽章 -->
    <div class="stats-badges">
      <div class="badge">
        <svg viewBox="0 0 24 24"><path d="M12 4.5C7 4.5 2.73 7.61 1 12c1.73 4.39 6 7.5 11 7.5s9.27-3.11 11-7.5c-1.73-4.39-6-7.5-11-7.5zM12 17c-2.76 0-5-2.24-5-5s2.24-5 5-5 5 2.24 5 5-2.24 5-5 5zm0-8c-1.66 0-3 1.34-3 3s1.34 3 3 3 3-1.34 3-3-1.34-3-3-3z"/></svg>
        Profile Views <span class="accent">1.2k</span>
      </div>
      <div class="badge">
        <svg viewBox="0 0 24 24"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 3c1.66 0 3 1.34 3 3s-1.34 3-3 3-3-1.34-3-3 1.34-3 3-3zm0 14.2c-2.5 0-4.71-1.28-6-3.22.03-1.99 4-3.08 6-3.08 1.99 0 5.97 1.09 6 3.08-1.29 1.94-3.5 3.22-6 3.22z"/></svg>
        Followers <span class="accent">128</span>
      </div>
      <div class="badge">
        <svg viewBox="0 0 24 24"><path d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"/></svg>
        Stars <span class="accent">342</span>
      </div>
      <div class="badge">
        <svg viewBox="0 0 24 24"><path d="M20 6h-4V4c0-1.11-.89-2-2-2h-4c-1.11 0-2 .89-2 2v2H4c-1.11 0-1.99.89-1.99 2L2 19c0 1.11.89 2 2 2h16c1.11 0 2-.89 2-2V8c0-1.11-.89-2-2-2zm-6 0h-4V4h4v2z"/></svg>
        Coding & Coffee <span class="accent">☕</span>
      </div>
    </div>

    <!-- 技术栈 -->
    <div class="section-title">Tech Stack</div>

    <div class="tech-stack">
      <div class="tech-item">
        <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23ED8B00'%3E%3Cpath d='M12 0C5.37 0 0 5.37 0 12c0 5.3 3.438 9.8 8.205 11.387.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61-.546-1.387-1.333-1.756-1.333-1.756-1.09-.745.083-.73.083-.73 1.205.085 1.84 1.237 1.84 1.237 1.07 1.834 2.807 1.304 3.492.997.108-.775.418-1.305.762-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.468-2.38 1.235-3.22-.123-.3-.535-1.52.117-3.16 0 0 1.008-.322 3.3 1.23.96-.267 1.98-.4 3-.405 1.02.005 2.04.138 3 .405 2.29-1.552 3.297-1.23 3.297-1.23.653 1.64.24 2.86.118 3.16.768.84 1.233 1.91 1.233 3.22 0 4.61-2.804 5.62-5.476 5.92.43.37.824 1.102.824 2.22 0 1.602-.015 2.894-.015 3.287 0 .322.216.694.825.576C20.565 21.796 24 17.3 24 12c0-6.63-5.37-12-12-12z'/%3E%3C/svg%3E" alt="Java" width="26" height="26">
        Java
      </div>
      <div class="tech-item">
        <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%2300599C'%3E%3Cpath d='M12 0C5.37 0 0 5.37 0 12c0 5.3 3.438 9.8 8.205 11.387.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61-.546-1.387-1.333-1.756-1.333-1.756-1.09-.745.083-.73.083-.73 1.205.085 1.84 1.237 1.84 1.237 1.07 1.834 2.807 1.304 3.492.997.108-.775.418-1.305.762-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.468-2.38 1.235-3.22-.123-.3-.535-1.52.117-3.16 0 0 1.008-.322 3.3 1.23.96-.267 1.98-.4 3-.405 1.02.005 2.04.138 3 .405 2.29-1.552 3.297-1.23 3.297-1.23.653 1.64.24 2.86.118 3.16.768.84 1.233 1.91 1.233 3.22 0 4.61-2.804 5.62-5.476 5.92.43.37.824 1.102.824 2.22 0 1.602-.015 2.894-.015 3.287 0 .322.216.694.825.576C20.565 21.796 24 17.3 24 12c0-6.63-5.37-12-12-12z'/%3E%3C/svg%3E" alt="C++" width="26" height="26">
        C++
      </div>
      <div class="tech-item">
        <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%233776AB'%3E%3Cpath d='M14.25.18l.9.2.73.26.59.3.45.36.34.38.26.42.18.46.1.48.04.5-.02.5-.1.52-.18.5-.28.48-.36.44-.44.4-.5.35-.56.3-.62.24-.66.18-.7.12-.72.06-.74-.02-.74-.1-.72-.2-.68-.28-.62-.36-.56-.44-.48-.5-.4-.56-.3-.6-.2-.66-.1-.7v-.72l.1-.7.2-.66.3-.6.4-.56.48-.5.56-.44.62-.36.68-.28.72-.2.74-.1.74-.02.72.06.7.12.66.18.62.24.56.3.5.35.44.4.36.44.28.48.18.5.1.52.02.5-.04.5-.1.48-.18.46-.26.42-.34.38-.45.36-.59.3-.73.26-.9.2-.92.12-.92.05-.92-.05-.92-.12z'/%3E%3C/svg%3E" alt="Python" width="26" height="26">
        Python
      </div>
      <div class="tech-item">
        <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%23E34F26'%3E%3Cpath d='M12 0C5.37 0 0 5.37 0 12c0 5.3 3.438 9.8 8.205 11.387.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61-.546-1.387-1.333-1.756-1.333-1.756-1.09-.745.083-.73.083-.73 1.205.085 1.84 1.237 1.84 1.237 1.07 1.834 2.807 1.304 3.492.997.108-.775.418-1.305.762-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.468-2.38 1.235-3.22-.123-.3-.535-1.52.117-3.16 0 0 1.008-.322 3.3 1.23.96-.267 1.98-.4 3-.405 1.02.005 2.04.138 3 .405 2.29-1.552 3.297-1.23 3.297-1.23.653 1.64.24 2.86.118 3.16.768.84 1.233 1.91 1.233 3.22 0 4.61-2.804 5.62-5.476 5.92.43.37.824 1.102.824 2.22 0 1.602-.015 2.894-.015 3.287 0 .322.216.694.825.576C20.565 21.796 24 17.3 24 12c0-6.63-5.37-12-12-12z'/%3E%3C/svg%3E" alt="HTML5" width="26" height="26">
        HTML5
      </div>
      <div class="tech-item">
        <img src="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='%235C2D91'%3E%3Cpath d='M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm-1-13h2v6h-2zm0 8h2v2h-2z'/%3E%3C/svg%3E" alt="Visual Studio" width="26" height="26">
        Visual Studio
      </div>
    </div>

    <!-- 技能图标 -->
    <div class="skill-icons-row">
      <div class="skill-icon">☕ Java</div>
      <div class="skill-icon">⚡ C++</div>
      <div class="skill-icon">🐍 Python</div>
      <div class="skill-icon">🌐 HTML5</div>
      <div class="skill-icon">🖥️ Visual Studio</div>
    </div>

    <!-- 数据统计 -->
    <div class="section-title">GitHub Stats</div>

    <div class="stats-grid">
      <div class="stat-card">
        <div class="stat-title">
          <svg viewBox="0 0 24 24" width="20" height="20" fill="#70a5fd"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8zm-1-13h2v6h-2zm0 8h2v2h-2z"/></svg>
          Overall Stats
        </div>
        <div class="stat-row">
          <span class="stat-label">Total Commits</span>
          <span class="stat-value">3,842</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Repositories</span>
          <span class="stat-value">42</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Stars</span>
          <span class="stat-value accent">342</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Followers</span>
          <span class="stat-value">128</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Contributions</span>
          <span class="stat-value">1,284</span>
        </div>
      </div>

      <div class="stat-card">
        <div class="stat-title">
          <svg viewBox="0 0 24 24" width="20" height="20" fill="#f7b32b"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 18c-4.41 0-8-3.59-8-8s3.59-8 8-8 8 3.59 8 8-3.59 8-8 8z"/></svg>
          Current Streak
        </div>
        <div style="display: flex; align-items: baseline; gap: 0.5rem; margin: 0.5rem 0 0.8rem;">
          <span class="streak-days">32</span>
          <span style="color: #8b949e; font-size: 1rem;">days</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Longest Streak</span>
          <span class="stat-value">87 days</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Last Active</span>
          <span class="stat-value">Today</span>
        </div>
        <div class="stat-row">
          <span class="stat-label">Rank</span>
          <span class="stat-value accent">#3,221</span>
        </div>
      </div>
    </div>

    <!-- 奖杯 -->
    <div class="trophy-row">
      <div class="trophy-item"><span>🏆</span> Starstruck</div>
      <div class="trophy-item"><span>🥇</span> Committer</div>
      <div class="trophy-item"><span>🔥</span> Streak Master</div>
      <div class="trophy-item"><span>🚀</span> Pull Shark</div>
      <div class="trophy-item"><span>⭐</span> Open Source</div>
    </div>

    <!-- 名言 -->
    <div class="section-title">Quote of the Day</div>

    <div class="quote-box">
      <div class="quote-text">“代码如诗，简洁而有力；开发如旅，永无止境。”</div>
      <div class="quote-author">— ShuiMu-Dev</div>
    </div>

    <!-- 页脚 -->
    <div class="wave-footer">
      Thanks for visiting
    </div>
  </div>
</body>
</html>
