<!doctype html>
<html lang="zh-Hant">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#10141d">
  <meta name="description" content="ComfyUI Image-to-Image 圖生圖練習作品展示：原圖、生成圖、完整工作流、正反提示詞與學習心得。">
  <title>從照片到古風戰士｜ComfyUI 圖生圖作品</title>
  <style>
    :root{color-scheme:dark;--bg:#0c1017;--panel:#151c27;--edge:#30394a;--ink:#f4f5f7;--muted:#aeb9c7;--accent:#f2cc8d}
    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{margin:0;color:var(--ink);background:radial-gradient(circle at 85% 3%,#2a2932,transparent 42%),var(--bg);font-family:system-ui,-apple-system,"Noto Sans TC","Microsoft JhengHei",sans-serif;line-height:1.75}
    .container{width:min(1120px,calc(100% - 36px));margin:auto}
    header{padding:72px 0 54px;border-bottom:1px solid var(--edge)}
    .eyebrow{text-transform:uppercase;color:var(--accent);letter-spacing:.22em;font-size:.77rem;font-weight:750}
    h1{font-size:clamp(2rem,5vw,3.9rem);line-height:1.2;letter-spacing:-.02em;margin:18px 0}
    .lede{max-width:760px;color:var(--muted);font-size:1.05rem;margin:0}
    .chips{display:flex;flex-wrap:wrap;gap:9px;margin-top:27px}
    .chip{border:1px solid #4a4e55;border-radius:999px;padding:5px 14px;font-size:.85rem;color:#e2e5e9}
    nav{display:flex;gap:20px;flex-wrap:wrap;padding:16px 0;font-size:.92rem}
    a{color:var(--accent);text-decoration:none}a:hover{text-decoration:underline}
    section{padding-top:54px}
    h2{font-size:clamp(1.3rem,3vw,1.85rem);margin:0 0 10px}
    .section-desc{color:var(--muted);margin:0 0 22px}
    .pair{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:18px}
    figure{margin:0;background:var(--panel);border:1px solid var(--edge);border-radius:16px;overflow:hidden}
    .photo{display:flex;justify-content:center;align-items:center;min-height:400px;background:#0a0c12}
    .photo img{width:100%;height:490px;object-fit:contain;display:block}
    .wide-image{display:block;width:100%;height:auto;max-height:720px;object-fit:contain;background:#0a0c12}
    figcaption{padding:16px 20px;color:var(--muted);font-size:.93rem}
    figcaption strong{display:block;color:var(--ink);font-size:1rem}
    .flow-text{border-left:3px solid var(--accent);margin-top:19px;padding:8px 18px;background:#181d26;color:#e6e7e8}
    .prompt-list{display:grid;grid-template-columns:1fr 1fr;gap:18px}
    .card{padding:24px;background:var(--panel);border:1px solid var(--edge);border-radius:16px}
    .card h3{margin:0 0 14px;font-size:1.1rem}
    pre{margin:0;white-space:pre-wrap;overflow-wrap:anywhere;font: .92rem/1.8 Consolas,Monaco,monospace;color:#d6e0ee}
    .settings{display:flex;gap:10px;flex-wrap:wrap;margin:17px 0 0}
    .settings span{padding:7px 12px;border-radius:8px;background:#232c38;color:#dce3ea;font-size:.88rem}
    .reflection{font-size:1.01rem;color:#d8e0ea;max-width:900px}
    footer{color:var(--muted);text-align:center;margin-top:65px;padding:30px;border-top:1px solid var(--edge);font-size:.87rem}
    @media(max-width:700px){header{padding-top:48px}.pair,.prompt-list{grid-template-columns:1fr}.photo{min-height:0}.photo img{height:420px}section{padding-top:42px}}
  </style>
</head>
<body>
  <header>
    <div class="container">
      <div class="eyebrow">ComfyUI · Image to Image · Assignment</div>
      <h1>ComfyUI 圖生圖作品</h1>
      <p class="lede"></p>

    </div>
  </header>
  <div class="container">
   
    <main>
      <section id="comparison">
        <h2>01 / 原圖與生成圖</h2>
        <p class="section-desc">左側為自行拍攝的原始照片，右側為 ComfyUI 生成後的古風戰士影像。</p>
        <div class="pair">
          <figure><div class="photo"><img src="original.jpg" alt="本人拍攝的原始照片" loading="eager"></div><figcaption><strong>Original / 原始照片</strong>使用自己的照片作為 Image-to-Image 輸入。</figcaption></figure>
          <figure><div class="photo"><img src="generated.png" alt="AI 生成的中國古風戰士照片" loading="eager"></div><figcaption><strong>Generated / AI 生成圖</strong>以中國古風戰士、傳統盔甲及戰場氛圍為視覺目標。</figcaption></figure>
        </div>
      </section>
      <section id="workflow">
        <h2>02 / 完整工作流</h2>
        <p class="section-desc">ComfyUI 節點式影像生成流程與參數設定的畫面紀錄。</p>
        <figure><img class="wide-image" src="workflow.png" alt="ComfyUI 的完整 Image-to-Image 節點工作流截圖" loading="lazy"><figcaption></figcaption></figure>
      </section>
      <section id="prompts">
        <h2>03 / 使用的正反提示詞</h2>
        <div class="prompt-list">
          <div class="card"><h3>Positive Prompt / 正向提示詞</h3><pre>(masterpiece, best quality), a young Asian man as an ancient Chinese warrior, wearing traditional Chinese battle armor, intricate dark metal armor, red cape, long black hair, ancient Chinese battlefield, dramatic cinematic lighting, epic atmosphere, full body portrait, realistic photography, highly detailed</pre></div>
          <div class="card"><h3>Negative Prompt / 反向提示詞</h3><pre>worst quality, low quality, blurry, bad anatomy, deformed face, distorted body, extra arms, extra legs, extra fingers, duplicate person, modern suit, modern clothes, cartoon, anime, watermark, text</pre></div>
        </div>
      </section>
      <section id="reflection">
        <h2>04 / 個人心得</h2>
        <div class="card reflection"><p>這次使用 ComfyUI 進行圖生圖練習，讓我第一次實際理解節點式工作流的運作方式。剛開始我以為把照片拖進軟體就可以直接生成，但後來才發現，還需要建立完整的圖生圖流程，並載入適合的模型。</p><p>實作過程中最困難的是找到 ComfyUI Desktop 的模型資料夾，以及處理照片尺寸過大、生成時間太長的問題。我也發現 Denoise 數值會明顯影響結果：數值太低時，生成圖跟原圖很像；調高後，服裝與場景的風格變化才更明顯。</p><p>最後，我成功將自己的照片轉換成古風戰士的影像。這次作業讓我學到 AI 影像創作不只是輸入一句文字，更需要理解模型、節點連線、提示詞與參數之間的關係，才能逐步調整出想要的效果。</p></div>
      </section>
    </main>
  </div>
  <footer>ComfyUI Image-to-Image ｜ 課堂作業展示</footer>
</body>
</html>
