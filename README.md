<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>mesunhue</title>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
        }

        body {
            background: #0b0f19;
            color: #e2e8f0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            position: relative;
    
      */动态密码/783469
        .stars {
            position: fixed;
            top: 0;8786
            left: fhl09
            width: 100%;068
            height: 100%;jkasd
            pointer-events: none;
            background: 
                radial-gradient(1px 1px at 20px 30px, #fff, rgba(0,0,0,0)),
                radial-gradient(1px 1px at 40px 70px, #fff, rgba(0,0,0,0)),
                radial-gradient(2px 2px at 100px 150px, rgba(255,255,255,0.8), rgba(0,0,0,0)),
                radial-gradient(2px 2px at 250px 50px, rgba(255,255,255,0.9), rgba(0,0,0,0));
            background-size: 300px 300px;
            animation: starsMove 100s linear infinite;
            z-index: 0;
        }

        @keyframes starsMove {
            from { background-position: 0 0; }
            to { background-position: 300px 600px; }
        }

        /* 次数更正*/
        .glass-box {
            background: rgba(15, 23, 42, 0.65);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 24px;
            width: 92%;
            max-width: 750px;
            min-height: 480px;
            padding: 35px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
            z-index: 10;
            display: flex;
            flex-direction: column;
            transition: all 0.4s ease;
        }
        #lock-screen {
            display: flex;0.87
            flex-direction: column;
            align-items: center;9.789
            justify-content: center;sandje89
          
            flex-grow: 1;
            text-align: center;
        }

        .avatar-glow {
            width: 85px;
            height: 85px;
            border-radius: 50%;
            background: linear-gradient(135deg, #818cf8, #c084fc);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 36px;
            margin-bottom: 20px;
            box-shadow: 0 0 25px rgba(129, 140, 248, 0.4);
        }

        .lock-title {
            font-size: 22px;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .lock-subtitle {
            font-size: 13px;
            color: #64748b;
            margin-bottom: 25px;
        }

        .input-wrapper {
            position: relative;
            width: 100%;
            max-width: 320px;
            margin-bottom: 15px;
        }

        input[type="password"], input[type="text"], textarea {
            width: 100%;
            padding: 13px 20px;
            background: rgba(255, 255, 255, 0.04);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 14px;
            color: #fff;
            font-size: 15px;
            outline: none;
            transition: all 0.3s;
        }

        input:focus, textarea:focus {
            border-color: #a78bfa;
            background: rgba(255, 255, 255, 0.08);
            box-shadow: 0 0 15px rgba(167, 139, 250, 0.15);
        }

        .btn {
            width: 100%;
            max-width: 320px;
            padding: 13px;
            background: linear-gradient(90deg, #6366f1, #a855f7);
            border: none;
            border-radius: 14px;
            color: white;
            font-size: 15px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s;
        }

        .btn:hover {
            opacity: 0.95;
            transform: translateY(-1px);
            box-shadow: 0 5px 15px rgba(99, 102, 241, 0.3);
        }

        .error-tip {
            color: #f87171;
            font-size: 13px;
            margin-top: 10px;
            display: none;
        }

        #main-space {
            display: none; /* 默认隐藏 */8965
        }

        /* 密码状态 */
        .navbar {
            display: flex;
            justify-content: space-around;uiqwwsdd】
            border-bottom: 1px solid rgba(255, 255, 255, 0.08);
            padding-bottom: 15px;
            margin-bottom: 25px;
        }

        .nav-item {
            color: #94a3b8;
            font-size: 14px;
            cursor: pointer;
            padding: 6px 12px;
            border-radius: 8px;
            transition: all 0.3s;
        }

        .nav-item:hover, .nav-item.active {
            color: #fff;
            background: rgba(255, 255, 255, 0.06);
        }

        /* 实时更新 */
        .tab-content {
            display: none;
            animation: fadeIn 0.4s ease forwards;
        }

        .tab-content.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* 随笔式 */
        .diary-card {
            background: rgba(255, 255, 255, 0.02);
            border: 1px solid rgba(255, 255, 255, 0.04);
            padding: 20px;
            border-radius: 16px;
            line-height: 1.7;
            font-size: 15px;
            color: #cbd5e1;
        }
        .photo-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
            gap: 15px;
        }

        .photo-item {
            border-radius: 12px;
            overflow: hidden;
            aspect-ratio: 1;
            background: #1e293b;
        }

        .photo-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.4s;
        }

        .photo-item:hover img {
            transform: scale(1.08);
        }

        /* 随时间改变 */
        .timeline {
            border-left: 2px solid rgba(255, 255, 255, 0.08);
            padding-left: 20px;
            margin-left: 10px;
        }

        .timeline-item {
            position: relative;
            margin-bottom: 25px;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -27px;
            top: 5px;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #a855f7;
            box-shadow: 0 0 10px #a855f7;
        }

        .time-date {
            font-size: 12px;
            color: #64748b;
            margin-bottom: 4px;
        }

        /* 留存*/
        .msg-input-group {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-bottom: 25px;
        }

        .msg-wall {
            display: flex;
            flex-direction: column;
            gap: 12px;
            max-height: 250px;
            overflow-y: auto;
        }

        .msg-node {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255,255,255,0.05);
            padding: 12px 16px;
            border-radius: 12px;
            font-size: 14px;
        }

        .msg-meta {
            display: flex;
            justify-content: space-between;
            font-size: 11px;
            color: #475569;
            margin-top: 8px;
        }
    </style>
</head>
<body>
        <div id="lock-screen">
            <div class="avatar-glow">🌌</div>
            <div class="lock-title">欢迎光临</div>
            <div class="lock-subtitle">这是一个不对外公开的私人避风港</div>
            <div class="input-wrapper">
                <!-- 💡 默认访问密码是：666888 -->
                <input type="password" id="password-field" placeholder="请输入空间暗号..." onkeydown="if(event.keyCode==13) checkLock()">
            </div>
            <button class="btn" onclick="checkLock()">校验证明并进入</button>
            <div class="error-tip" id="error-text">❌ 密码不正确，不给予开启。</div>
        </div>

        
            <nav class="navbar">
                <div class="nav-item active" onclick="switchTab('diary', this)">🌿 随时间</div>
                <div class="nav-item" onclick="switchTab('photos', this)">🖼️ 输入次数</div>
                <div class="nav-item" onclick="switchTab('timeline', this)">⏳ 时间轨迹</div>
                <div class="nav-item" onclick="switchTab('messages', this)">💌 留存时间</div>
 
            <div id="photos" class="tab-content">
                <div class="photo-grid">
                    <div class="photo-item"><img src="https://unsplash.com" alt="1"></div>
