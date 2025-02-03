<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>维多祝您蛇年快乐！</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f8e3d1; /* 暖色调背景 */
            text-align: center;
            padding: 50px;
        }
        h1 {
            color: #d32f2f; /* 红色标题 */
            margin-bottom: 20px;
        }
        p.subtitle {
            font-size: 18px;
            color: #555;
            margin-bottom: 40px;
        }
        .red-envelope {
            width: 200px;
            height: 300px;
            background-color: #c62828; /* 红包颜色 */
            color: white;
            margin: 0 auto;
            position: relative;
            border-radius: 10px;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            transition: transform 0.3s ease;
        }
        .red-envelope:hover {
            transform: scale(1.1); /* 鼠标悬停时放大效果 */
        }
        .red-envelope::before {
            content: '🧧';
            font-size: 80px;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        /* 祝福语样式 */
        .message-box {
            margin-top: 20px;
            font-size: 36px; /* 字体更大 */
            color: red; /* 红色文字 */
            min-height: 40px;
            opacity: 0; /* 初始透明 */
            transform: scale(0.8); /* 初始缩小 */
            transition: all 1s ease-in-out; /* 动画过渡 */
        }

        /* 祝福语显示动画 */
        .message-box.show {
            opacity: 1; /* 完全显示 */
            transform: scale(1); /* 恢复正常大小 */
        }

        /* 动画：红包打开效果 */
        @keyframes openEnvelope {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.2);
            }
            100% {
                transform: scale(1);
                opacity: 0;
            }
        }

        .open-animation {
            animation: openEnvelope 1s forwards;
        }
    </style>
</head>
<body>
    <h1>维多祝您蛇年快乐！</h1>
    <p class="subtitle">点击红包，领取您的专属祝福语</p>

    <!-- 红包 -->
    <div class="red-envelope" id="redEnvelope"></div>

    <!-- 显示祝福语的区域 -->
    <div class="message-box" id="messageBox"></div>

    <script>
        // 随机祝福语数组，每条祝福语后附带表情符号
        const blessings = [
            "愿您蛇年大吉，万事如意！🎉",
            "蛇年行大运，财源滚滚来！💰",
            "福如东海长流水，寿比南山不老松！🌲",
            "蛇年顺心如意，幸福安康常伴！💖",
            "事业如蛇般灵活，生活如蛇般顺畅！🚀",
            "蛇年好运连连，幸福美满到永远！🌟"
        ];

        // 获取DOM元素
        const redEnvelope = document.getElementById('redEnvelope');
        const messageBox = document.getElementById('messageBox');

        // 点击红包事件
        redEnvelope.addEventListener('click', () => {
            // 添加动画类，触发红包打开动画
            redEnvelope.classList.add('open-animation');

            // 延迟1秒（与动画时间一致）后显示祝福语
            setTimeout(() => {
                // 随机选择一条祝福语
                const randomIndex = Math.floor(Math.random() * blessings.length);
                const randomBlessing = blessings[randomIndex];

                // 显示祝福语并添加表情
                messageBox.textContent = randomBlessing;

                // 添加祝福语显示动画
                messageBox.classList.add('show');

                // 移除红包元素（模拟红包被打开）
                redEnvelope.style.display = 'none';
            }, 1000); // 动画持续时间为1秒
        });
    </script>
</body>
</html>
