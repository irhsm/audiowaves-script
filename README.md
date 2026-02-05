# audiowaves-script

A simple FFmpeg script to generate waveforms from WAV audio files.

## macOS Apple Silicon

A script for macOS with Apple silicon:

```bash
ffmpeg -i YOUR_MEDIA.wav -filter_complex \
"showwaves=s=1920x1080:mode=line:colors=white:draw=full[v]" \
-map "[v]" -pix_fmt yuv420p -c:v h264_videotoolbox -b:v 5M \
-an YOUR_MEDIA.mp4
```

## Windows (NVIDIA GPU)

A script for Windows with NVIDIA GPU:

```bash
ffmpeg -i YOUR_MEDIA.wav -filter_complex \
"showwaves=s=1920x1080:mode=line:colors=white:draw=full[v]" \
-map "[v]" -pix_fmt yuv420p -c:v h264_nvenc -b:v 5M \
-an YOUR_MEDIA.mp4
```

## Linux / Universal (Software Encoding)

A script for Linux without dedicated GPU—but just **libx264**:

```bash
ffmpeg -i YOUR_MEDIA.wav -filter_complex \
"showwaves=s=1920x1080:mode=line:colors=white:draw=full[v]" \
-map "[v]" -pix_fmt yuv420p -c:v libx264 -preset fast -b:v 5M \
-an YOUR_MEDIA.mp4
```

## Windows (Intel QuickSync)

A script for Windows laptop with integrated Intel graphics:

```bash
ffmpeg -i YOUR_MEDIA.wav -filter_complex \
"showwaves=s=1920x1080:mode=line:colors=white:draw=full[v]" \
-map "[v]" -pix_fmt yuv420p -c:v h264_qsv -b:v 5M \
-an YOUR_MEDIA.mp4
```