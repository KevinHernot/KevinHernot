# GIF Creation Recipe: bubble_globe.gif

Generated on April 6, 2026.

## Source
- **Input**: `assets/bubble_globe.mp4`
- **Starting Point**: `00:00:01`
- **Total Duration**: 60 seconds

## Settings
- **Resolution**: 360p (Landscape: 792x360)
- **Framerate**: 30 fps
- **Filters**: 
  - `transpose=2`: 90-degree counter-clockwise rotation (Portrait to Landscape)
  - `scale=-2:360`: Resize to 360px height with Lanczos scaling
  - `fps=30`: Frame rate normalization
- **Dithering**: Bayer Dithering (`bayer_scale=3`)
- **Palette**: Custom 128-color palette generated per-frame

## FFmpeg Command
```bash
ffmpeg -y -ss 00:00:01 -t 60 -i assets/bubble_globe.mp4 \
  -vf "transpose=2,fps=30,scale=-2:360:flags=lanczos,split[s0][s1];[s0]palettegen=max_colors=128[p];[s1][p]paletteuse=dither=bayer:bayer_scale=3" \
  -loop 0 assets/bubble_globe.gif
```
