document.getElementById('form').addEventListener('submit', function(e) {
    e.preventDefault();
    const url = document.getElementById('videoUrl').value;
    fetch(`https://api.tiktok-downloader.xyz/download?url=${url}`)
        .then(response => response.json())
        .then(data => {
            const videoUrl = data.video_url;
            const linkElement = document.createElement('a');
            linkElement.href = videoUrl;
            linkElement.textContent = "تحميل الفيديو";
            linkElement.download = "tiktok_video.mp4";
            document.getElementById('downloadLink').appendChild(linkElement);
        })
        .catch(err => console.error("خطأ في تحميل الفيديو", err));
});
