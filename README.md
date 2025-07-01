<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Layout YouTube - Vídeo Principal</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f9f9f9;
      color: #333;
    }

    /* Header */
    header {
      display: flex;
      align-items: center;
      background: white;
      padding: 8px 16px;
      box-shadow: 0 1px 4px rgba(0,0,0,0.1);
      position: sticky;
      top: 0;
      z-index: 10;
    }

    .logo-youtube {
      height: 40px;
      cursor: pointer;
    }

    .search-bar {
      flex: 1;
      display: flex;
      justify-content: center;
      margin: 0 16px;
    }

    .search-bar input {
      width: 60%;
      max-width: 500px;
      padding: 6px 12px;
      font-size: 16px;
      border: 1px solid #ccc;
      border-radius: 2px 0 0 2px;
      outline: none;
    }

    .search-bar button {
      padding: 6px 12px;
      font-size: 16px;
      border: 1px solid #ccc;
      border-left: none;
      border-radius: 0 2px 2px 0;
      background: #eee;
      cursor: pointer;
      transition: background 0.3s;
    }

    .search-bar button:hover {
      background: #ddd;
    }

    .user-area {
      display: flex;
      align-items: center;
      gap: 12px;
      position: relative;
    }

    .notification {
      position: relative;
      cursor: pointer;
      display: flex;
      align-items: center;
      margin-right: 8px;
    }

    .notification svg {
      width: 28px;
      height: 28px;
      fill: #555;
    }

    .notification-badge {
      position: absolute;
      top: -6px;
      right: -6px;
      background: red;
      color: white;
      font-size: 12px;
      font-weight: bold;
      padding: 2px 6px;
      border-radius: 12px;
      box-shadow: 0 0 2px #800000;
      user-select: none;
    }

    .user-photo {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      object-fit: cover;
      cursor: pointer;
      border: 1.5px solid #ddd;
    }

    /* Main layout */
    .container {
      display: flex;
      padding: 16px;
      gap: 24px;
    }

    /* Vídeo principal */
    .video-section {
      flex: 2;
    }

    iframe {
      width: 100%;
      /* Tamanho padrão do YouTube player: 16:9 ratio */
      aspect-ratio: 16 / 9;
      border: none;
      border-radius: 8px;
    }

    .video-info {
      margin-top: 12px;
    }

    .video-title {
      font-size: 22px;
      font-weight: bold;
      margin-bottom: 6px;
    }

    .channel-info {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 14px;
      flex-wrap: wrap;
    }

    .channel-logo {
      width: 48px;
      height: 48px;
      border-radius: 50%;
      object-fit: cover;
      border: 1.5px solid #ddd;
    }

    .channel-name {
      font-weight: 600;
      font-size: 18px;
      color: #555;
      margin-right: 20px;
    }

    /* Botões ao lado do nome do canal */
    .channel-actions {
      display: flex;
      align-items: center;
      gap: 12px;
      flex-wrap: wrap;
    }

    .btn-like,
    .btn-dislike,
    .btn-subscribe {
      display: flex;
      align-items: center;
      gap: 6px;
      background: #eee;
      border: none;
      padding: 6px 12px;
      border-radius: 20px;
      cursor: pointer;
      font-weight: 600;
      font-size: 14px;
      color: #333;
      user-select: none;
      transition: background 0.3s;
    }

    .btn-like:hover,
    .btn-dislike:hover,
    .btn-subscribe:hover {
      background: #ccc;
    }

    .btn-like::before {
      content: "👍";
    }

    .btn-dislike::before {
      content: "👎";
    }

    .btn-subscribe::before {
      content: "🔴";
    }

    /* Comentários */
    .comments-section {
      margin-top: 20px;
    }

    #add-comment {
      margin-bottom: 12px;
    }

    #comment-text {
      width: 100%;
      min-height: 60px;
      resize: vertical;
      padding: 8px;
      font-size: 14px;
      border: 1px solid #ccc;
      border-radius: 4px;
      box-sizing: border-box;
      font-family: Arial, sans-serif;
    }

    #submit-comment {
      margin-top: 6px;
      padding: 6px 14px;
      background: #cc0000;
      color: white;
      border: none;
      border-radius: 3px;
      cursor: pointer;
      font-weight: bold;
      transition: background 0.3s;
    }

    #submit-comment:hover {
      background: #a30000;
    }

    .comment {
      display: flex;
      gap: 12px;
      margin-bottom: 14px;
      align-items: flex-start;
    }

    .comment img {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      object-fit: cover;
      border: 1.5px solid #ddd;
    }

    .comment-content {
      background: white;
      padding: 10px 14px;
      border-radius: 6px;
      flex: 1;
      box-shadow: 0 0 3px rgb(0 0 0 / 0.1);
    }

    .comment-author {
      font-weight: 600;
      margin-bottom: 4px;
      font-size: 15px;
    }

    .comment-text {
      font-size: 14px;
      margin-bottom: 6px;
      white-space: pre-wrap;
    }

    .comment-reactions span {
      margin-right: 16px;
      font-size: 14px;
      user-select: none;
      cursor: default;
    }

    /* Recomendações */
    .recommendations-section {
      flex: 1;
      max-width: 320px;
    }

    .recommendations-title {
      font-size: 18px;
      font-weight: bold;
      margin-bottom: 12px;
      color: #444;
    }

    .recommended-item {
      display: flex;
      gap: 10px;
      margin-bottom: 14px;
      cursor: pointer;
    }

    .recommended-item img {
      width: 120px;
      height: 67px;
      object-fit: cover;
      border-radius: 4px;
    }

    .recommended-details {
      flex: 1;
    }

    .recommended-title {
      font-weight: 600;
      font-size: 15px;
      margin-bottom: 4px;
      color: #222;
    }

    .recommended-channel,
    .recommended-views {
      font-size: 13px;
      color: #666;
      margin-bottom: 2px;
    }

  </style>
</head>
<body>

<header>
  <img class="logo-youtube" src="https://classic.exame.com/wp-content/uploads/2017/08/new-youtube-logo-840x402.jpg" alt="YouTube Logo" />
  <div class="search-bar">
    <input type="text" placeholder="Pesquisar" />
    <button>🔍</button>
  </div>
  <div class="user-area">
    <div class="notification" title="Notificações">
      <svg viewBox="0 0 24 24" >
        <path d="M12 22c1.1 0 2-.89 2-1.98h-4c0 1.09.9 1.98 2 1.98zm6-6v-5c0-3.07-1.63-5.64-4.5-6.32V4a1.5 1.5 0 0 0-3 0v.68C7.63 5.36 6 7.92 6 11v5l-2 2v1h16v-1l-2-2z"/>
      </svg>
      <div class="notification-badge">9+</div>
    </div>
    <img class="user-photo" src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/65/20180610_FIFA_Friendly_Match_Austria_vs._Brazil_Neymar_850_1705.jpg/960px-20180610_FIFA_Friendly_Match_Austria_vs._Brazil_Neymar_850_1705.jpg" alt="Usuário Neymar" />
  </div>
</header>

<div class="container">

  <section class="video-section">
    <iframe src="https://www.youtube.com/embed/GTVDNV4KrKU" allowfullscreen title="Portugal se classifica contra a Alemanha pra final!"></iframe>
    <div class="video-info">
      <div class="video-title">Portugal se classifica contra a Alemanha pra final!</div>
      <div class="channel-info">
        <img class="channel-logo" src="https://i.pinimg.com/736x/1f/8f/86/1f8f8666f2efd5a44546449eb12ab511.jpg" alt="Logo ESPN" />
        <div class="channel-name">ESPN</div>
        <div class="channel-actions">
          <button class="btn-like">12</button>
          <button class="btn-dislike">1</button>
          <button class="btn-subscribe">Inscreva-se</button>
        </div>
      </div>
    </div>

    <section class="comments-section">
      <div id="add-comment">
        <textarea id="comment-text" placeholder="Escreva um comentário..."></textarea>
        <button id="submit-comment" onclick="addComment()">Comentar</button>
      </div>

      <div class="comments">
        <div class="comment">
          <img src="https://randomuser.me/api/portraits/men/32.jpg" alt="João" />
          <div class="comment-content">
            <div class="comment-author">João</div>
            <div class="comment-text">Que jogo emocionante, Portugal merece a final!</div>
            <div class="comment-reactions">
              <span>👍 12</span>
              <span>👎 0</span>
            </div>
          </div>
        </div>
        <div class="comment">
          <img src="https://randomuser.me/api/portraits/women/44.jpg" alt="Maria" />
          <div class="comment-content">
            <div class="comment-author">Maria</div>
            <div class="comment-text">Estou muito feliz com essa vitória!</div>
            <div class="comment-reactions">
              <span>👍 9</span>
              <span>👎 1</span>
            </div>
          </div>
        </div>
      </div>
    </section>
  </section>

  <aside class="recommendations-section">
    <div class="recommendations-title">Recomendações</div>

    <div class="recommended-item">
      <img src="https://img.youtube.com/vi/FTQbiNvZqaY/hqdefault.jpg" alt="Vídeo recomendado 1" />
      <div class="recommended-details">
        <div class="recommended-title">Neymar Skills</div>
        <div class="recommended-channel">Canal Neymar</div>
        <div class="recommended-views">3M de visualizações</div>
      </div>
    </div>

    <div class="recommended-item">
      <img src="https://img.youtube.com/vi/kJQP7kiw5Fk/hqdefault.jpg" alt="Vídeo recomendado 2" />
      <
