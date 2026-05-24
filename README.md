<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
  <title>Telegram Channel Widget | WAB_BOOK</title>
  <!-- Google Fonts for clean typography -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,400;14..32,500;14..32,600;14..32,700&display=swap" rel="stylesheet">
  <!-- Font Awesome 6 (free icons) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(135deg, #0b2b3b 0%, #1b4f6e 100%);
      font-family: 'Inter', sans-serif;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 20px;
    }

    /* main card container */
    .telegram-card {
      max-width: 620px;
      width: 100%;
      background: rgba(255, 255, 255, 0.97);
      border-radius: 48px;
      box-shadow: 0 25px 45px -12px rgba(0, 0, 0, 0.35), 0 4px 12px rgba(0, 0, 0, 0.1);
      overflow: hidden;
      backdrop-filter: blur(0px);
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .telegram-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 32px 55px -15px rgba(0, 0, 0, 0.4);
    }

    /* header with Telegram brand style */
    .card-header {
      background: #2a96e5;
      padding: 24px 32px;
      position: relative;
      overflow: hidden;
    }

    .card-header::after {
      content: "✨";
      font-size: 110px;
      position: absolute;
      right: -15px;
      bottom: -35px;
      opacity: 0.12;
      pointer-events: none;
      transform: rotate(-5deg);
    }

    .header-content {
      display: flex;
      align-items: center;
      gap: 16px;
      flex-wrap: wrap;
      color: white;
    }

    .tg-icon-large {
      background: white;
      width: 58px;
      height: 58px;
      border-radius: 32px;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 8px 16px rgba(0,0,0,0.15);
    }

    .tg-icon-large i {
      font-size: 36px;
      color: #2a96e5;
    }

    .header-text h2 {
      font-weight: 700;
      font-size: 1.8rem;
      letter-spacing: -0.3px;
      margin-bottom: 6px;
    }

    .header-text p {
      font-size: 0.95rem;
      opacity: 0.9;
      font-weight: 500;
    }

    /* channel info section */
    .channel-info {
      padding: 28px 32px 12px 32px;
      background: white;
    }

    .channel-badge {
      display: inline-flex;
      align-items: center;
      background: #eef5fc;
      padding: 8px 18px;
      border-radius: 60px;
      gap: 10px;
      margin-bottom: 20px;
      font-size: 0.9rem;
      font-weight: 500;
      color: #1e6f9f;
    }

    .channel-badge i {
      font-size: 1rem;
    }

    .channel-link-display {
      background: #f8fafc;
      border-radius: 28px;
      padding: 16px 24px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 14px;
      border: 1px solid #e2edf2;
      transition: all 0.2s;
    }

    .channel-url {
      font-family: 'Monaco', 'Menlo', 'Courier New', monospace;
      font-size: 1rem;
      font-weight: 500;
      color: #0f2f3f;
      background: white;
      padding: 8px 18px;
      border-radius: 60px;
      word-break: break-all;
      letter-spacing: 0.2px;
      box-shadow: inset 0 1px 2px #00000008, 0 1px 1px white;
      border: 1px solid #dce9f0;
    }

    .copy-btn {
      background: white;
      border: 1px solid #cbdde6;
      padding: 8px 20px;
      border-radius: 40px;
      font-weight: 600;
      font-size: 0.85rem;
      color: #1a6a94;
      cursor: pointer;
      transition: 0.2s;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-family: 'Inter', sans-serif;
    }

    .copy-btn i {
      font-size: 0.9rem;
    }

    .copy-btn:hover {
      background: #e9f4fa;
      border-color: #2a96e5;
      color: #0f4c6b;
    }

    /* join button (main CTA) */
    .join-section {
      padding: 8px 32px 24px 32px;
    }

    .join-telegram-btn {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 14px;
      background: #2a96e5;
      color: white;
      text-decoration: none;
      font-weight: 700;
      font-size: 1.35rem;
      padding: 18px 22px;
      border-radius: 60px;
      transition: all 0.25s ease;
      box-shadow: 0 6px 14px rgba(42, 150, 229, 0.3);
      border: none;
      cursor: pointer;
      width: 100%;
      font-family: 'Inter', sans-serif;
    }

    .join-telegram-btn i {
      font-size: 1.8rem;
      transition: transform 0.2s;
    }

    .join-telegram-btn:hover {
      background: #1f7bb8;
      transform: scale(1.01);
      box-shadow: 0 12px 20px -8px rgba(42,150,229,0.5);
    }

    .join-telegram-btn:hover i {
      transform: translateX(4px);
    }

    /* stats / extra info */
    .stats-row {
      display: flex;
      justify-content: space-between;
      background: #fefefe;
      border-top: 1px solid #edf2f7;
      padding: 16px 32px 24px 32px;
      flex-wrap: wrap;
      gap: 20px;
    }

    .stat-item {
      display: flex;
      align-items: center;
      gap: 12px;
      color: #305f7a;
      font-weight: 500;
    }

    .stat-item i {
      font-size: 1.3rem;
      width: 28px;
      color: #2a96e5;
    }

    .stat-item span {
      font-size: 0.9rem;
    }

    .footer-note {
      background: #f0f6fa;
      padding: 14px 32px;
      text-align: center;
      font-size: 0.75rem;
      color: #3d6e8b;
      border-top: 1px solid #e0edf3;
      font-weight: 500;
    }

    /* toast notification */
    .toast-msg {
      position: fixed;
      bottom: 30px;
      left: 50%;
      transform: translateX(-50%) scale(0.9);
      background: #1a2e3b;
      color: white;
      padding: 12px 24px;
      border-radius: 60px;
      font-weight: 500;
      font-size: 0.85rem;
      opacity: 0;
      visibility: hidden;
      transition: all 0.2s ease;
      z-index: 1000;
      backdrop-filter: blur(12px);
      background: rgba(0, 0, 0, 0.8);
      box-shadow: 0 8px 18px rgba(0,0,0,0.2);
      pointer-events: none;
      font-family: 'Inter', monospace;
    }

    .toast-msg.show {
      opacity: 1;
      visibility: visible;
      transform: translateX(-50%) scale(1);
    }

    @media (max-width: 520px) {
      .card-header {
        padding: 20px 24px;
      }
      .header-text h2 {
        font-size: 1.4rem;
      }
      .join-telegram-btn {
        font-size: 1.1rem;
        padding: 14px 18px;
      }
      .channel-link-display {
        flex-direction: column;
        align-items: flex-start;
      }
      .channel-url {
        width: 100%;
        text-align: center;
        font-size: 0.85rem;
      }
      .stats-row {
        flex-direction: column;
        gap: 12px;
      }
    }
  </style>
</head>
<body>

<div class="telegram-card">
  <div class="card-header">
    <div class="header-content">
      <div class="tg-icon-large">
        <i class="fab fa-telegram-plane"></i>
      </div>
      <div class="header-text">
        <h2>Join our channel</h2>
        <p>Exclusive books, resources & updates</p>
      </div>
    </div>
  </div>

  <div class="channel-info">
    <div class="channel-badge">
      <i class="fas fa-link"></i> 
      <span>Official Telegram Channel</span>
    </div>
    <div class="channel-link-display">
      <div class="channel-url" id="channelUrlDisplay">https://t.me/WAB_BOOK</div>
      <button class="copy-btn" id="copyLinkBtn" aria-label="Copy channel link">
        <i class="far fa-copy"></i> Copy link
      </button>
    </div>
  </div>

  <div class="join-section">
    <a href="https://t.me/WAB_BOOK" target="_blank" rel="noopener noreferrer" class="join-telegram-btn" id="joinButton">
      <i class="fab fa-telegram"></i> Join Telegram Channel
      <i class="fas fa-arrow-right"></i>
    </a>
  </div>

  <div class="stats-row">
    <div class="stat-item">
      <i class="fas fa-book-open"></i>
      <span>Daily book updates</span>
    </div>
    <div class="stat-item">
      <i class="fas fa-users"></i>
      <span>Growing community</span>
    </div>
    <div class="stat-item">
      <i class="fas fa-bolt"></i>
      <span>Instant access</span>
    </div>
  </div>

  <div class="footer-note">
    <i class="fas fa-shield-alt"></i>  Join with one click — no login required. Your channel: <strong>WAB_BOOK</strong>
  </div>
</div>

<div id="toastMsg" class="toast-msg">✓ Link copied to clipboard!</div>

<script>
  (function() {
    // ----- CONFIGURATION -----
    // Channel link as provided (static, but also used for dynamic generation)
    const CHANNEL_LINK = "https://t.me/WAB_BOOK";
    // Optional: also store raw handle (just for reference)
    const CHANNEL_HANDLE = "WAB_BOOK";
    
    // DOM elements
    const joinBtn = document.getElementById('joinButton');
    const copyBtn = document.getElementById('copyLinkBtn');
    const channelUrlSpan = document.getElementById('channelUrlDisplay');
    const toast = document.getElementById('toastMsg');
    
    // Ensure href matches the exact channel URL (already correct, but set explicitly)
    if (joinBtn) {
      joinBtn.setAttribute('href', CHANNEL_LINK);
      // Add security attributes (rel noopener noreferrer already present)
    }
    
    // Set the displayed link text (makes it clear)
    if (channelUrlSpan) {
      channelUrlSpan.textContent = CHANNEL_LINK;
    }
    
    // ----- Helper: show toast notification -----
    function showToast(message) {
      if (!toast) return;
      toast.textContent = message || "✓ Link copied to clipboard!";
      toast.classList.add('show');
      setTimeout(() => {
        toast.classList.remove('show');
      }, 2200);
    }
    
    // ----- Copy link functionality (using modern clipboard API) -----
    async function copyChannelLink() {
      try {
        await navigator.clipboard.writeText(CHANNEL_LINK);
        showToast("🔗 Channel link copied! Share with friends.");
        // Optional: subtle haptic if supported? not needed.
      } catch (err) {
        console.warn('Clipboard API failed, using fallback', err);
        // Fallback for older browsers or permission issues
        const textarea = document.createElement('textarea');
        textarea.value = CHANNEL_LINK;
        document.body.appendChild(textarea);
        textarea.select();
        try {
          document.execCommand('copy');
          showToast("📋 Link copied (fallback method)");
        } catch (e) {
          showToast("⚠️ Could not copy, please select manually");
        }
        document.body.removeChild(textarea);
      }
    }
    
    // Add event listener to copy button
    if (copyBtn) {
      copyBtn.addEventListener('click', (e) => {
        e.preventDefault();
        copyChannelLink();
      });
    }
    
    // ----- Optional: track join event? just nice to have console info (non intrusive) -----
    if (joinBtn) {
      joinBtn.addEventListener('click', (e) => {
        // simple analytics friendly, but we don't track, just keep console for debug
        console.log(`🔵 Redirecting to Telegram channel: ${CHANNEL_LINK}`);
        // the default behavior will open a new tab/window
      });
    }
    
    // For dynamic note: show a nice effect on hover for the copy button (already in css)
    // Also handle potential "?start" parameter? Not needed.
    // Provide additional snippet: if user wants to embed this widget multiple times,
    // this script is self-contained.
    
    // Additional micro interaction: make channel badge clickable? just for fun (optional)
    const channelBadgeDiv = document.querySelector('.channel-badge');
    if (channelBadgeDiv) {
      channelBadgeDiv.style.cursor = 'pointer';
      channelBadgeDiv.addEventListener('click', () => {
        copyChannelLink();
      });
      channelBadgeDiv.title = 'Click to copy channel link';
    }
    
    // Bonus: display channel handle as additional context in stats row or via tooltip
    // enhance footer note consistency
    const footerStrong = document.querySelector('.footer-note strong');
    if (footerStrong) footerStrong.textContent = CHANNEL_HANDLE;
    
    // Extra feature: "generated" timestamp only in console (no UI clutter)
    console.log(`✅ Telegram channel widget ready — link: ${CHANNEL_LINK}`);
    console.log('📢 Join button leads to @WAB_BOOK channel');
    
    // For complete HTML code generation, if this script is embedded inside <body>, everything works.
    // Also detect iframe or direct embedding - no issues.
  })();
</script>
</body>
</html>