# Bird in AR

A phone AR page. People scan a QR code and the bird video appears in the room around them.

- **Android (Chrome):** real AR. The phone finds the floor, you tap, and the video stands on the floor. You can walk around it.
- **iPhone (Safari):** the camera view with the video floating in front of you. It stays in place as you look around.
- **Fallback:** a "Just watch the video" button on every phone.

## Setup (about 5 minutes)

1. Create a new **public** repository on GitHub, e.g. `bird-ar`.
2. Upload these files:
   - `index.html`
   - `qr.html`
   - `video.mp4` ← your clip, named exactly this
3. Go to **Settings → Pages**. Set Source to *Deploy from a branch*, choose `main` / `root`, and save.
4. After a minute your page is live at `https://YOUR-USERNAME.github.io/bird-ar/`.
5. Open `https://YOUR-USERNAME.github.io/bird-ar/qr.html`. The QR code is made for you. Download it and print it.

## Video

`video.mp4` is the blue tit clip, already converted: 1280×676, H.264, 45 seconds, about 6 MB.

## Video tips (if you swap in a different clip)

- Use **MP4 (H.264)** so it plays on both iPhone and Android.
- Keep it **under ~25 MB** so it loads quickly on mobile data. GitHub's hard limit is 100 MB.
- To shrink it, use HandBrake's "Fast 720p30" preset, or run:
  `ffmpeg -i input.mp4 -vf scale=-2:1280 -c:v libx264 -crf 26 -preset veryfast -c:a aac -b:a 128k -movflags +faststart video.mp4`

## Tweaks

At the top of the script in `index.html`:
- `VIDEO_HEIGHT` sets how tall the video screen is, in metres.
- `FALLBACK_DISTANCE` sets how far away the video floats on iPhone.

## Notes

- The page has to be opened over **https** for camera access. GitHub Pages does this automatically.
- The video starts muted, because phones block autoplay with sound. Tap **Sound** to turn it on.
- People will be asked to allow the camera, and on iPhone also motion access.
