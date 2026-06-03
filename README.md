<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>私人加密空间</title>
    <!-- 引入行业标准的加密库 CryptoJS -->
    <script src="https://cloudflare.com"></script>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, sans-serif; }
        body { background-color: #1a1a1a; color: #ffffff; display: flex; justify-content: center; align-items: center; min-height: 100vh; padding: 20px; }
        
        /* 密码输入框样式 */
        .login-container { background: #2a2a2a; padding: 40px; border-radius: 12px; box-shadow: 0 8px 24px rgba(0,0,0,0.3); text-align: center; max-width: 400px; width: 100%; transition: all 0.3s; }
        .login-container h2 { margin-bottom: 20px; font-size: 22px; color: #a29bfe; }
        .password-input { width: 100%; padding: 12px; border: 1px solid #444; background: #333; color: #fff; border-radius: 6px; margin-bottom: 20px; text-align: center; font-size: 16px; outline: none; }
        .password-input:focus { border-color: #6c5ce7; }
        .btn-decrypt { background: #6c5ce7; color: white; border: none; padding: 12px 30px; border-radius: 6px; cursor: pointer; font-weight: bold; width: 100%; transition: background 0.3s; }
        .btn-decrypt:hover { background: #5b4cc4; }
        .error-msg { color: #ff7675; margin-top: 15px; font-size: 14px; display: none; }

        /* 解密后的私人内容样式（默认隐藏） */
        #private-content { display: none; background: #222; padding: 40px; border-radius: 12px; max-width: 800px; width: 100%; box-shadow: 0 10px 30px rgba(0,0,0,0.5); border-left: 5px solid #6c5ce7; }
        .secret-title { font-size: 28px; margin-bottom: 20px; color: #a29bfe; border-bottom: 1px solid #333; padding-bottom: 10px; }
        .secret-body { font-size: 16px; line-height: 1.8; color: #e0e0e0; white-space: pre-wrap; }
    </style>
</head>
<body>

    <!-- 第一步：密码验证界面 -->
    <div class="login-container" id="login-box">
        <h2>🔒 私人加密空间</h2>
        <input type="password" id="password" class="password-input" placeholder="请输入访问密码" autocomplete="off">
        <button class="btn-decrypt" onclick="verifyAndDecrypt()">解密进入</button>
        <div class="error-msg" id="error-txt">❌ 密码错误，无法解密内容</div>
    </div>

    <!-- 第二步：解密后显示的隐私内容 -->
    <div id="private-content">
        <h1 class="secret-title">✨ 我的私人空间</h1>
        <div class="secret-body" id="secret-text">
            <!-- 解密后的文本会自动注入到这里 -->
        </div>
    </div>

    <script>
        /**
         * 🔒 安全提示与配置：
         * 这里的 encryptedData 是你的私人内容经过 AES 加密后生成的密文（乱码）。
         * 默认的解密密码是：123456
         * 
         * 如果你想修改密码和私人内容，请看代码下方的“自定义指南”。
         */
        const encryptedData = "U2FsdGVkX19R7+bBicN6CbyHj0hI/w35E4pXG423fA+Q6vNmdI7Gf/2+L/V1bM1iB4Sby10bZqX2vW+rV6w=="; 

        function verifyAndDecrypt() {
            const password = document.getElementById('password').value;
            const errorTxt = document.getElementById('error-txt');
            
            if (!password) {
                alert("请输入密码！");
                return;
            }

            try {
                // 使用输入的密码尝试解密
                const bytes = CryptoJS.AES.decrypt(encryptedData, password);
                const decryptedText = bytes.toString(CryptoJS.enc.Utf8);

                // 如果解密成功且有内容
                if (decryptedText) {
                    // 隐藏登录框，显示隐私内容
                    document.getElementById('login-box').style.display = 'none';
                    const contentDiv = document.getElementById('private-content');
                    contentDiv.style.display = 'block';
                    document.getElementById('secret-text').innerHTML = decryptedText;
                    errorTxt.style.display = 'none';
                } else {
                    errorTxt.style.display = 'block';
                }
            } catch (e) {
                // 密码错误导致解密失败会抛出异常
                errorTxt.style.display = 'block';
            }
        }

        // 支持回车键提交
        document.getElementById('password').addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                verifyAndDecrypt();
            }
        });
    </script>
</body>
</html>
