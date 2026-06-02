# Yelena Khait — Art Portfolio

A responsive portfolio site for artist Yelena Khait, showcasing paintings, custom shoes,
and TikTok content, with a commission request form. Deployed via GitHub Pages.

## Structure

```
.
├── index.html          # Home: hero, gallery (10 paintings), TikTok reels, about
├── abstract.html       # Full-width abstract / textured works
├── shoes.html          # Custom-painted shoes gallery
├── commission.html     # Commission request form (Web3Forms → khait3102@gmail.com)
├── README.md
└── assets/
    ├── images/
    │   ├── art/        # Paintings
    │   ├── shoes/      # Custom shoe designs
    │   └── artist/     # Artist headshot
    └── video/          # TikTok process videos (.mp4)
```

## Notes

- Pages live at the root so GitHub Pages serves `index.html` as the landing page.
- All asset paths are relative (`assets/...`), so the site works locally and on Pages.
- TikTok clips are local `.mp4` files (embedded TikTok links proved unreliable).
- `.mov` source files are intentionally not deployed — Chrome/Edge can't play them;
  convert with `ffmpeg -i clip.mov -vcodec h264 -acodec aac clip.mp4` before adding.

## Links

- TikTok: https://www.tiktok.com/@paintingartist2188
- Instagram: https://www.instagram.com/yelenas__art
- YouTube: https://youtube.com/@yelenakhait6520
