<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.5, user-scalable=yes">
  <title>haloo Ikarr — sekbid 4</title>
  <!-- Fonts: serif hangat dan personal, sans untuk footer -->
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;1,400&family=Inter:wght@300;400&display=swap" rel="stylesheet">
  <style>
    /* ---------- reset — sunyi, lapang, seperti surat yang disimpan lama ---------- */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #e9edea;  /* soft grey kehijauan, seperti kertas daur ulang */
      background-image: 
        radial-gradient(circle at 94% 68%, rgba(135, 165, 175, 0.07) 1.8px, transparent 1.8px),
        radial-gradient(circle at 12% 28%, rgba(125, 155, 165, 0.05) 1.4px, transparent 1.4px);
      background-size: 70px 70px, 50px 50px;
      font-family: 'Cormorant Garamond', 'Georgia', 'Times New Roman', serif;
      color: #1a3f4a;
      line-height: 1.8;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      padding: 2.2rem 1.8rem;
    }

    /* — grain halus, seperti tekstur kertas yang menguning — */
    body::after {
      content: '';
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200" viewBox="0 0 200 200"><filter id="noise"><feTurbulence type="fractalNoise" baseFrequency="0.68" numOctaves="1" stitchTiles="stitch"/><feColorMatrix type="matrix" values="1 0 0 0 0 0 1 0 0 0 0 0 1 0 0 0 0 0 0.06 0"/></filter><rect width="200" height="200" filter="url(%23noise)" opacity="0.13"/></svg>');
      background-repeat: repeat;
      opacity: 0.15;
      pointer-events: none;
      z-index: 2;
    }

    .letter {
      max-width: 780px;
      width: 100%;
      background: rgba(255, 255, 250, 0.78);
      backdrop-filter: blur(2px);
      -webkit-backdrop-filter: blur(2px);
      border-radius: 28px;
      padding: 3.2rem 3rem;
      box-shadow: 
        0 18px 32px -18px rgba(30, 65, 75, 0.06),
        0 4px 12px -8px rgba(20, 50, 60, 0.02),
        inset 0 0 0 1px rgba(250, 250, 245, 0.6);
      border: 0.5px solid rgba(130, 170, 180, 0.15);
      position: relative;
      z-index: 5;
    }

    /* ----- HEADER : hanya judul, tanpa subheader ----- */
    header {
      margin-bottom: 2.5rem;
      border-bottom: 0.5px solid rgba(110, 150, 165, 0.2);
      padding-bottom: 1.2rem;
    }

    .title {
      font-family: 'Cormorant Garamond', 'Libre Baskerville', serif;
      font-weight: 500;
      font-size: 2.3rem;
      color: #12424e;
      letter-spacing: -0.01em;
      line-height: 1.1;
      word-break: break-word;
    }

    /* ---------- CONTENT — animasi lembut, seperti membaca surat di sore hari ---------- */
    .content {
      display: flex;
      flex-direction: column;
      gap: 1.9rem;
    }

    .paragraph-item {
      width: 100%;
      opacity: 0;
      transform: translateY(14px);
      animation: riseGentle 1s cubic-bezier(0.2, 0.9, 0.3, 1) forwards;
    }

    /* jeda bertahap — setiap paragraf punya waktunya sendiri */
    .paragraph-item:nth-child(1) { animation-delay: 0.2s; }
    .paragraph-item:nth-child(2) { animation-delay: 0.7s; }
    .paragraph-item:nth-child(3) { animation-delay: 1.2s; }
    .paragraph-item:nth-child(4) { animation-delay: 1.7s; }
    .paragraph-item:nth-child(5) { animation-delay: 2.2s; }

    @keyframes riseGentle {
      0% {
        opacity: 0;
        transform: translateY(18px);
      }
      100% {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .paragraph-text {
      font-size: 1.1rem;
      font-weight: 400;
      color: #1d4b57;
      text-align: left;
      margin: 0;
      line-height: 1.85;
      padding: 0.1rem 0;
      word-break: break-word;
    }

    /* aksen garis tipis — seperti awal kalimat dalam buku harian */
    .paragraph-text::before {
      content: "—";
      color: #9fb7bf;
      font-weight: 300;
      margin-right: 0.5rem;
      opacity: 0.5;
    }

    /* dropcap klasik — hanya di paragraf pertama */
    .paragraph-item:first-child .paragraph-text::first-letter {
      font-size: 2.9rem;
      float: left;
      line-height: 0.75;
      margin-right: 0.55rem;
      color: #2b5e6a;
      font-weight: 500;
    }

    /* FOOTER — hanya ~Ammar, sesuai permintaan */
    footer {
      margin-top: 3rem;
      padding-top: 1.5rem;
      border-top: 0.5px solid rgba(110, 160, 170, 0.2);
      font-family: 'Inter', 'Helvetica Neue', sans-serif;
      font-size: 0.95rem;
      color: #5a7e88;
      display: flex;
      justify-content: flex-end;
      font-weight: 300;
      letter-spacing: 0.02em;
      opacity: 0;
      animation: riseGentle 1s ease forwards;
      animation-delay: 2.8s;
    }

    .footer-signature {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
    }

    .footer-name {
      font-size: 1.2rem;
      font-style: italic;
      color: #436b75;
      font-family: 'Cormorant Garamond', serif;
      font-weight: 400;
    }

    /* responsive */
    @media (max-width: 600px) {
      body { padding: 1.5rem 1rem; }
      .letter { padding: 2.2rem 1.8rem; }
      .title { font-size: 2rem; }
      .paragraph-text { font-size: 1rem; }
    }

    @media (max-width: 400px) {
      .title { font-size: 1.8rem; }
      .letter { padding: 1.8rem 1.2rem; }
    }

    /* tidak ada elemen berlebih — hanya judul, 5 paragraf, footer ~Ammar */
  </style>
</head>
<body>
  <div class="letter">
    <header>
      <h1 class="title">haloo Ikarr👋🏼👋🏼</h1>
    </header>

    <!-- CONTENT: 5 PARAGRAF LENGKAP, teks asli, tanpa placeholder -->
    <div class="content">
      <!-- PARAGRAPH 1 — memori bersama -->
      <div class="paragraph-item">
        <div class="paragraph-text">te tarasa Waktu leh, sekarang somo alumni sudah sa ini, padahal macam baru kemarin kita sama sama rapat perdana, baku pasang tenda di ot, ba pubdok, ba hitung uang asc, dimarahi pafik, urus aic, urus mpls, begadang bikin aftermovie lkps, heboh karna alzfest, hedon dengan padatnya asl, sampe pembubaran panitia yang bahkan sa te ikut itu😂. tapi semuanya sudah kita sama sama lewati, ada suka dan pasti ada dukanya selama kita sama sama di sekbid 4. tapi yang pasti, meskipun itu sudah dilewati tapi semua itu terekam jelas di kenangan yang ada di kepalanya kita. jadi semoga saja walaupun kita sudah tidak ketemu lagi, kenangan yang saya, kau dan teman teman buat bersama masih bisa teringat jelas di memorimu.</div>
      </div>

      <!-- PARAGRAPH 2 — terima kasih -->
      <div class="paragraph-item">
        <div class="paragraph-text">saya mau berterima kasih sebesar besarnya buat kau atas 1 tahunnya di sekbid 4. terima kasih sudah mau ada di sekbid 4, terima kasih sudah mau ikuti apa yang saya bilang ya meskipun mungkin ada yang tidak srek di kau, terima kasih juga sudah buat kenangan sama sama, terima kasih sudah sering bercanda ke saya dan teman teman, pokoknya terima kasih atas segalanya.</div>
      </div>

      <!-- PARAGRAPH 3 — minta maaf -->
      <div class="paragraph-item">
        <div class="paragraph-text">saya juga mau minta maaf kalo selama saya jadi ketua sekbid ataupun tidak ada kata kata atau perbuatanku yang menyinggung, menghina, atau tidak srek di kau. saya minta maaf sebesar besarnya. jujur saya tidak punya maksud lain atas perbuatanku itu. saya juga minta maaf kalo ada candaan atau apapun itu yang tidak baik di kau. saya minta maaf yahh</div>
      </div>

      <!-- PARAGRAPH 4 — harapan dan doa -->
      <div class="paragraph-item">
        <div class="paragraph-text">semoga kita bisa kumpul kumpul lagi kedepannya, semoga kau tidak lupa saya dan teman teman meskipun sudah tidak sama sama lagi, semoga kau bisa Amanah buat jalani OSIS 1 periode kedepan, semoga kau bisa sukses kedepannya, semoga kau bisa menjadi yang terbaik di versi dirimu sendiri, ya semoga apa yang baik bisa ke kau semua.</div>
      </div>

      <!-- PARAGRAPH 5 — penutup, untuk Zulfikar -->
      <div class="paragraph-item">
        <div class="paragraph-text">sekali lagi saya mengucapkan terima kasih yang sebesar besarya dan minta maaf yang sebesar besarnya ke kau. <br><br>thank you, Zulfikar.</div>
      </div>
    </div>

    <!-- FOOTER — sesuai permintaan: ~Ammar -->
    <footer>
      <div class="footer-signature">
        <span class="footer-name">~Ammar</span>
      </div>
    </footer>
  </div>

  <!-- tidak ada subheader, tidak ada teks overlay. 
       hanya sapaan untuk Ikarr (Zulfikar), kenangan, dan tanda tangan Ammar. -->
</body>
</html>
