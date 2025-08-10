<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>カメラで写真を撮ろう</title>
<style>
  body {
    font-family: Arial, sans-serif;
    text-align: center;
    margin: 30px;
    background: #f0f0f0;
  }
  video, canvas {
    border: 2px solid #333;
    border-radius: 8px;
    max-width: 100%;
  }
  button {
    margin-top: 15px;
    padding: 10px 20px;
    font-size: 1rem;
    border: none;
    background: #007bff;
    color: white;
    border-radius: 6px;
    cursor: pointer;
  }
  button:active {
    background: #0056b3;
  }
  #photos {
    margin-top: 20px;
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    justify-content: center;
  }
  #photos img {
    max-width: 150px;
    border: 2px solid #555;
    border-radius: 8px;
  }
</style>
</head>
<body>
  <h1>カメラで写真を撮ろう</h1>
  <video id="video" autoplay playsinline></video>
  <br />
  <button id="snap">写真を撮る</button>
  <div id="photos"></div>

<script>
  const video = document.getElementById('video');
  const snapBtn = document.getElementById('snap');
  const photos = document.getElementById('photos');

  async function setupCamera() {
    try {
      const stream = await navigator.mediaDevices.getUserMedia({ video: true });
      video.srcObject = stream;
    } catch (e) {
      alert('カメラにアクセスできませんでした。許可を確認してください。');
      console.error(e);
    }
  }
  setupCamera();

  snapBtn.addEventListener('click', () => {
    // canvasを作る（画面に表示しない）
    const canvas = document.createElement('canvas');
    canvas.width = video.videoWidth;
    canvas.height = video.videoHeight;
    const ctx = canvas.getContext('2d');
    ctx.drawImage(video, 0, 0, canvas.width, canvas.height);

    // DataURLを取得してimgタグを作成
    const imgUrl = canvas.toDataURL('image/png');
    const img = document.createElement('img');
    img.src = imgUrl;

    // photosエリアに追加
    photos.appendChild(img);
  });
</script>
</body>
</html>