# 🎬 Automated Video Processing with FFmpeg

## 📌 Requirements
- Windows OS
- FFmpeg installed ([Download](https://ffmpeg.org/download.html))

## 📂 Folder Structure
```
project-folder/
│-- input_videos/       # Your main videos
│-- intro.mp4          # Your intro clip
│-- outro.mp4          # Your outro clip
│-- output_videos/     # Where final videos will be saved
│-- script.bat         # This script
```

## 📝 Script: `script.bat`
```batch
@echo off
mkdir output_videos
for %%f in (input_videos\*.mp4) do (
    ffmpeg -i "intro.mp4" -i "input_videos\%%f" -i "outro.mp4" -filter_complex "[0:v:0][0:a:0][1:v:0][1:a:0][2:v:0][2:a:0]concat=n=3:v=1:a=1[outv][outa]" -map "[outv]" -map "[outa]" "output_videos\%%~nf_final.mp4"
    echo Processed: %%f
)
echo 🎉 All videos processed!
```

## 🚀 How to Use
1. **Download & install FFmpeg**.
2. **Place your videos** in the `input_videos/` folder.
3. **Create a new Notepad file** and copy the script above.
4. **Save it as `script.bat`** (make sure it’s not a `.txt` file!).
5. **Double-click `script.bat`** to run it.
6. **Find final videos** in `output_videos/`.

✅ Now your videos will have an intro and outro automatically! 🚀
