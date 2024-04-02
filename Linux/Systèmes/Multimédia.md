## Redirection de l’entrée audio d’une machine à l’autre
```bash
ssh ramces@remote.host "arecord -f cd" | aplay
arecord -f cd | ssh ramces@remote.host "aplay"
ssh ramces@remote.host "arecord -f cd" | ffplay -nodisp -
```

## Diffusion de vidéo en direct à partir d’une webcam distante
```bash
ssh ramces@remote.host "ffmpeg  -r 14 -s 640x480 -f video4linux2 -i /dev/video0 -f matroska -" | mpv --demuxer=mkv /dev/stdin
ssh ramces@remote.host "ffmpeg  -r 14 -s 640x480 -f video4linux2 -i /dev/video0 -f matroska -" | tee my_recording.mkv | mpv --demuxer=mkv /dev/stdin
```
