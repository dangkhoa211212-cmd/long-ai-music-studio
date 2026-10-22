# long-ai-music-studio

<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <meta name="theme-color" content="#111827">
  <meta name="description" content="LONG AI MUSIC STUDIO - Trợ lý sáng tác âm nhạc tiếng Việt">
  <link rel="manifest" href="./manifest.webmanifest">
  <link rel="icon" href="./icon.svg" type="image/svg+xml">
  <title>LONG AI MUSIC STUDIO</title>
  <style>
    :root {
      color-scheme: dark;
      --bg: #0b1020;
      --panel: #151d30;
      --line: #293650;
      --text: #f4f7ff;
      --muted: #aab7ce;
      --accent: #8b7bff;
      --green: #43d9a3;
    }
    * { box-sizing: border-box; }
    body {
      margin: 0;
      background: var(--bg);
      color: var(--text);
      font-family: system-ui, Arial, sans-serif;
      line-height: 1.55;
    }
    header {
      padding: 25px 17px;
      background: linear-gradient(135deg,#24204d,#142c42);
      border-bottom: 1px solid var(--line);
    }
    .wrap { max-width: 850px; margin: auto; }
    .brand { color: #c7c0ff; font-size: 12px; letter-spacing: 2px; }
    h1 { font-size: clamp(25px,6vw,36px); margin: 7px 0; }
    h2 { font-size: 19px; margin-top: 0; }
    p { color: var(--muted); }
    main { padding: 16px; }
    .panel {
      background: var(--panel);
      border: 1px solid var(--line);
      border-radius: 16px;
      padding: 17px;
      margin-bottom: 15px;
    }
    label {
      display: block;
      font-size: 14px;
      margin: 13px 0 6px;
      color: #e2e9fa;
    }
    input, select, textarea {
      width: 100%;
      padding: 12px;
      border: 1px solid #394966;
      border-radius: 10px;
      background: #0c1425;
      color: white;
      font: inherit;
    }
    textarea { min-height: 115px; resize: vertical; }
    button {
      border: 0;
      border-radius: 10px;
      padding: 12px 15px;
      background: var(--accent);
      color: white;
      font-weight: 700;
      font-size: 14px;
      cursor: pointer;
    }
    button.secondary { background: #293650; }
    button.green { background: #087e61; }
    .actions { display: flex; flex-wrap: wrap; gap: 9px; margin-top: 14px; }
    .hint { font-size: 13px; }
    .status { color: var(--green); min-height: 22px; font-size: 13px; }
    .grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
    .chip {
      display: inline-block; padding: 5px 9px; margin: 3px;
      border: 1px solid var(--line); border-radius: 20px;
      color: #c7c0ff; font-size: 12px;
    }
    footer { padding: 10px 17px 28px; text-align: center; font-size: 12px; color: var(--muted); }
    @media(max-width:520px) {
      .grid { grid-template-columns: 1fr; }
      .panel { padding: 14px; }
      button { flex-grow: 1; }
    }
  </style>
</head>
<body>
<header>
  <div class="wrap">
    <div class="brand">SÁNG TÁC • CẢM XÚC • ÂM NHẠC</div>
    <h1>LONG AI MUSIC STUDIO</h1>
    <p>Không gian sáng tác bài hát dành cho người Việt.</p>
    <span class="chip">Tiếng Việt</span>
    <span class="chip">Mobile-first</span>
    <span class="chip">Bản thử nghiệm</span>
  </div>
</header>

<main class="wrap">
  <section class="panel">
    <h2>🎼 1. Ý tưởng bài hát</h2>
    <label for="title">Tên bài hát</label>
    <input id="title" placeholder="Ví dụ: Sai một lần, mất cả đời">

    <label for="topic">Chủ đề và câu chuyện</label>
    <textarea id="topic" placeholder="Ví dụ: Người đàn ông nhận ra mình đã đánh mất người phụ nữ yêu mình thật lòng..."></textarea>

    <div class="grid">
      <div>
        <label for="genre">Phong cách âm nhạc</label>
        <select id="genre">
          <option>Ballad buồn</option>
          <option>Blue rock</option>
          <option>Rock mạnh</option>
          <option>Pop hiện đại</option>
          <option>Dân ca Việt Nam</option>
          <option>Acoustic mộc mạc</option>
          <option>Bolero trữ tình</option>
        </select>
      </div>
      <div>
        <label for="voice">Giọng hát mong muốn</label>
        <select id="voice">
          <option>Nam trầm, khàn nhẹ</option>
          <option>Nam cao, khàn mạnh</option>
          <option>Nữ trầm cảm xúc</option>
          <option>Nữ cao trong trẻo</option>
          <option>Song ca nam nữ</option>
        </select>
      </div>
      <div>
        <label for="mood">Cảm xúc</label>
        <select id="mood">
          <option>Đau lòng, day dứt</option>
          <option>Mạnh mẽ, vượt qua</option>
          <option>Lãng mạn, ngọt ngào</option>
          <option>Hy vọng, chữa lành</option>
          <option>Sôi động, bùng nổ</option>
        </select>
      </div>
      <div>
        <label for="length">Độ dài dự kiến</label>
        <select id="length">
          <option>Bài hát khoảng 3 phút</option>
          <option>Bài hát khoảng 4 phút</option>
          <option>Bài hát ngắn cho video</option>
        </select>
      </div>
    </div>
    <div class="actions">
      <button onclick="makeDraft()">✍️ Tạo bản nháp lời</button>
      <button class="secondary" onclick="makePrompt()">🎧 Tạo prompt âm nhạc</button>
    </div>
    <p class="hint">Bản hiện tại tạo bản nháp theo mẫu, chưa gọi mô hình AI bên ngoài.</p>
  </section>

  <section class="panel">
    <h2>📝 2. Lời bài hát</h2>
    <label for="lyrics">Chỉnh sửa lời tại đây</label>
    <textarea id="lyrics" style="min-height:300px" placeholder="Lời bài hát sẽ xuất hiện tại đây..."></textarea>
    <div class="actions">
      <button onclick="copyText('lyrics')">Sao chép lời</button>
      <button class="secondary" onclick="downloadLyrics()">Tải lời bài hát (.txt)</button>
    </div>
  </section>

  <section class="panel">
    <h2>🎙️ 3. Prompt tạo nhạc</h2>
    <label for="prompt">Mô tả phong cách cho dịch vụ tạo nhạc</label>
    <textarea id="prompt" placeholder="Prompt sẽ xuất hiện tại đây..."></textarea>
    <div class="actions">
      <button onclick="copyText('prompt')">Sao chép prompt</button>
      <button class="green" onclick="saveProject()">💾 Lưu dự án trên máy</button>
    </div>
    <p class="hint">Prompt có thể dùng với dịch vụ tạo nhạc tương thích. Chi phí, quyền sử dụng và quyền thương mại phụ thuộc điều khoản của từng nhà cung cấp.</p>
  </section>

  <section class="panel">
    <h2>📚 4. Dự án đã lưu trên thiết bị</h2>
    <label for="projects">Chọn dự án</label>
    <select id="projects">
      <option value="">Chưa chọn dự án</option>
    </select>
    <div class="actions">
      <button class="secondary" onclick="loadProject()">Mở dự án</button>
      <button class="secondary" onclick="deleteProject()">Xóa dự án</button>
    </div>
    <p class="hint">Dự án được lưu trong trình duyệt của thiết bị này, không tự đồng bộ sang điện thoại khác.</p>
    <div id="status" class="status" role="status" aria-live="polite"></div>
  </section>

  <section class="panel">
    <h2>🚀 Lộ trình phát triển</h2>
    <p>Phiên bản tiếp theo sẽ bổ sung kết nối AI viết lời, tích hợp nhà cung cấp tạo nhạc có giọng hát và quản lý thư viện. Các tính năng này cần dịch vụ tương thích; không cam kết API miễn phí khi chưa xác minh.</p>
  </section>
</main>

<footer>LONG AI MUSIC STUDIO • Bản thử nghiệm cá nhân</footer>

<script>
const $ = id => document.getElementById(id);

function makeDraft() {
  const title = $('title').value.trim() || 'Một chuyện tình chưa quên';
  const topic = $('topic').value.trim() || 'một tình yêu đã qua, những tiếc nuối và hành trình học cách bước tiếp';
  const mood = $('mood').value;
  $('lyrics').value =
`TÊN BÀI: ${title}

[Verse 1]
Đêm nay nghe lòng mình lặng im
Bao ký ức vẫn còn nằm lại
Có những điều chưa kịp nói ra
Đã hóa thành khoảng trời xa mãi

[Pre-Chorus]
Ta đã đi qua bao tháng ngày
Giữ trong tim những điều chưa thể nói
Giữa cuộc đời rộng lớn đến vậy
Sao một người vẫn chẳng thể quên

[Chorus]
${title}, một câu chuyện chưa phai
Dẫu tháng năm đưa đôi mình xa mãi
${topic}
Vẫn có một người học cách đứng lên

[Verse 2]
Mai nếu vô tình mình gặp lại
Xin cứ xem nhau như người quen
Những vết thương rồi sẽ khép lại
Dẫu trong tim còn một cái tên

[Bridge]
Có những yêu thương không trở lại
Có những chia xa chẳng thể nào đổi thay
Nếu ngày mai bình minh thức giấc
Mong lòng mình nhẹ hơn hôm nay

[Final Chorus]
${title}, xin khép lại từ đây
Giữ những điều đẹp nhất trong ký ức
Dẫu con tim từng nhiều lần vụn vỡ
Vẫn mong đời còn những ngày bình yên

[Outro]
Một câu chuyện... xin gửi lại thời gian.`;

  setStatus('Đã tạo bản nháp mẫu. Huynh có thể sửa lời theo ý mình.');
}

function makePrompt() {
  const title = $('title').value.trim() || 'Bài hát mới';
  const topic = $('topic').value.trim() || 'câu chuyện tình yêu và hành trình trưởng thành';
  $('prompt').value =
`Create an original Vietnamese song.
Title: ${title}
Story and theme: ${topic}
Genre: ${$('genre').value}
Vocal: ${$('voice').value}
Emotion: ${$('mood').value}
Target duration: ${$('length').value}
Use natural Vietnamese pronunciation, emotionally expressive vocals,
a memorable chorus, clear verse and chorus structure, professional
mixing and a coherent musical arrangement.
Write an original melody and do not imitate a specific artist or song.
Language: Vietnamese.`;
  setStatus('Đã tạo prompt mô tả âm nhạc.');
}

async function copyText(id) {
  const value = $(id).value;
  if (!value.trim()) return setStatus('Chưa có nội dung để sao chép.');
  try {
    await navigator.clipboard.writeText(value);
    setStatus('Đã sao chép nội dung.');
  } catch (e) {
    $(id).focus();
    $(id).select();
    setStatus('Hãy nhấn giữ phần văn bản, chọn Sao chép.');
  }
}

function downloadLyrics() {
  const text = $('lyrics').value;
  if (!text.trim()) return setStatus('Chưa có lời bài hát để tải.');
  const blob = new Blob([text], {type:'text/plain;charset=utf-8'});
  const url = URL.createObjectURL(blob);
  const a = document.createElement('a');
  a.href = url;
  a.download = (($('title').value || 'loi-bai-hat').trim()) + '.txt';
  a.click();
  URL.revokeObjectURL(url);
  setStatus('Đã yêu cầu tải file lời bài hát.');
}

function readProjects() {
  try { return JSON.parse(localStorage.getItem('longMusicProjects') || '{}'); }
  catch (e) { return {}; }
}

function refreshProjects(selected = '') {
  const projects = readProjects();
  $('projects').innerHTML = '<option value="">Chọn dự án đã lưu</option>';
  Object.keys(projects).forEach(name => {
    const option = document.createElement('option');
    option.value = name;
    option.textContent = name;
    $('projects').appendChild(option);
  });
  $('projects').value = selected;
}

function saveProject() {
  const name = $('title').value.trim();
  if (!name) return setStatus('Hãy nhập tên bài hát trước khi lưu.');
  const projects = readProjects();
  projects[name] = {
    topic: $('topic').value,
    genre: $('genre').value,
    voice: $('voice').value,
    mood: $('mood').value,
    length: $('length').value,
    lyrics: $('lyrics').value,
    prompt: $('prompt').value
  };
  try {
    localStorage.setItem('longMusicProjects', JSON.stringify(projects));
    refreshProjects(name);
    setStatus('Đã lưu dự án trên trình duyệt thiết bị.');
  } catch (e) {
    setStatus('Không lưu được. Có thể bộ nhớ trình duyệt đã đầy.');
  }
}

function loadProject() {
  const name = $('projects').value;
  const project = readProjects()[name];
  if (!name || !project) return setStatus('Hãy chọn một dự án.');
  $('title').value = name;
  $('topic').value = project.topic || '';
  $('genre').value = project.genre || 'Ballad buồn';
  $('voice').value = project.voice || 'Nam trầm, khàn nhẹ';
  $('mood').value = project.mood || 'Đau lòng, day dứt';
  $('length').value = project.length || 'Bài hát khoảng 3 phút';
  $('lyrics').value = project.lyrics || '';
  $('prompt').value = project.prompt || '';
  setStatus('Đã mở dự án.');
}

function deleteProject() {
  const name = $('projects').value;
  if (!name) return setStatus('Hãy chọn dự án cần xóa.');
  if (!confirm('Huynh có chắc muốn xóa dự án "' + name + '"?')) return;
  const projects = readProjects();
  delete projects[name];
  localStorage.setItem('longMusicProjects', JSON.stringify(projects));
  refreshProjects();
  setStatus('Đã xóa dự án.');
}

function setStatus(message) {
  $('status').textContent = message;
}

refreshProjects();

if ('serviceWorker' in navigator && location.protocol.startsWith('http')) {
  window.addEventListener('load', () => {
    navigator.serviceWorker.register('./sw.js').catch(() => {});
  });
}
</script>
</body>
</html>
