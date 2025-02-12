# 🎬 Easy Video Editing – Add Intro & Outro Automatically!  

## 📌 What Is This?  
This script helps you **add an intro and outro** to multiple videos **automatically**. Instead of manually editing each video, this tool does it **all at once** using **FFmpeg**! 🚀  

## 🛠 What You Need  
✅ A **Windows computer** (or literally any OS but you have to check how it works there, pretty sure it is the same if not easier) 

✅ **FFmpeg installed** (It’s a free video editing tool)  
✅ Your **intro, main videos, and outro**  

---

## 🔧 Step 1: Install FFmpeg  
FFmpeg is a free tool that makes this automation possible.  

1️⃣ Download **FFmpeg** from [this link](https://ffmpeg.org/download.html).  
2️⃣ Extract the files and copy the **ffmpeg.exe** path.  
3️⃣ Add the FFmpeg path to your system’s **Environment Variables**:
   - Search for **"Environment Variables"** in Windows.  
   - Click **Path** under System Variables → **Edit** → **New**  
   - Paste the FFmpeg path.  
   - Click **OK** and close everything.  
4️⃣ Open **Command Prompt** and type:  
   ```sh
   ffmpeg -version
   ```  
   If FFmpeg is installed correctly, it will show the version details. ✅  

---

## 📂 Step 2: Organize Your Files  
Make sure your project folder is set up like this:  

```
project-folder/
│-- input_videos/       # Your main videos (place all your videos here)
│-- intro.mp4           # Your intro clip
│-- outro.mp4           # Your outro clip
│-- output_videos/      # Your final edited videos will be saved here
│-- script.bat          # The automation script
```

---

## 📝 Step 3: Create the Script  
1️⃣ Open **Notepad**  
2️⃣ Copy and paste this code:  

```batch
@echo off
mkdir output_videos
for %%f in (input_videos\*.mp4) do (
    ffmpeg -i "intro.mp4" -i "input_videos\%%f" -i "outro.mp4" -filter_complex "[0:v:0][0:a:0][1:v:0][1:a:0][2:v:0][2:a:0]concat=n=3:v=1:a=1[outv][outa]" -map "[outv]" -map "[outa]" "output_videos\%%~nf_final.mp4"
    echo Processed: %%f
)
echo 🎉 All videos processed!
```

3️⃣ **Save the file as** `script.bat` (make sure it’s not `.txt`).  
4️⃣ Move `script.bat` into the **same folder** as your videos.  

---

## 🚀 Step 4: Run the Script  
1️⃣ **Double-click** `script.bat`  
2️⃣ The script will start processing each video one by one.  
3️⃣ After completion, check the **output_videos** folder for your new videos!  

---

## ❓ Troubleshooting  
🔹 **FFmpeg is not recognized?**  
   - Make sure it’s installed and added to your system path (Step 1).  
🔹 **Videos don’t have the intro/outro?**  
   - Ensure `intro.mp4`, `outro.mp4`, and the videos are in the correct folders.  
🔹 **Script won’t run?**  
   - Right-click `script.bat` → **Run as Administrator**  

---

## 🎥 Who Is This For?  
✅ YouTubers  
✅ Content creators  
✅ Video editors  
✅ Anyone who wants to **save time!**  

💡 **Now you can edit multiple videos with just one click!** 🚀✨  
