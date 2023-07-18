# Text2Video

## Set up
1. Git clone repo
```
git clone git@github.com:sibozhang/Text2Video.git
```

2. Download and install modified vid2vid repo [vid2vid](https://github.com/sibozhang/vid2vid) 

3. Download Trained model

Please build 'checkpoints' folder in vid2vid folder and put trained model in it.

VidTIMIT fadg0 (English, Female) 

Dropbox: https://www.dropbox.com/sh/lk6et49v2uyfzjx/AADAFAp02_b3FQchaYxOZ0EMa?dl=0

百度云链接: https://pan.baidu.com/s/1SSkMKOK9LhClW2JvDCSiLg?pwd=bevj 提取码: bevj

Xuesong (Chinese, Male) 

Dropbox: https://www.dropbox.com/sh/qz3zoma5ac9mw5p/AAARiR8xKvATN4CBSyjWt_uOa?dl=0

百度云链接: 链接: https://pan.baidu.com/s/1DvuBbThYo4n5RIZsc-92rg?pwd=am7d 提取码: am7d

4. Prepare data and folder in the following order

    ```
    Text2Video
    ├── *phoneme_data
    ├── model
    ├── ...
    vid2vid
    ├── ...
    venv
    ├── vid2vid
    ```
5. Setup env 
```
sudo apt-get install sox libsox-fmt-mp3
pip install zhon
pip install moviepy
pip install ffmpeg
pip install dominate
pip install pydub
```

For Chinese, we use vosk to get timestamp of each words.
Please install vosk from https://alphacephei.com/vosk/install and unpack as 'model' in the current folder.
or install:

```
pip install vosk
pip install cn2an
pip install pypinyin
```

## Testing
1. Activate vitrual environment vid2vid
```
source ../venv/vid2vid/bin/activate
```
2. Generate video with real audio in English
```
sh text2video_audio.sh $1 $2
```

Generate video with TTS audio in English
```
sh text2video_tts.sh $1 $2 $3
```

Generate video with TTS audio in Chinese
```
sh text2video_tts.sh $1 $2 $3
```

$1: "input text"
$2: person
$3: fill f for female or m for male (gender)

Example 1. test VidTIMIT data with real audio.
```
sh text2video_audio.sh "She had your dark suit in greasy wash water all year." fadg0 f
```
    
Example 2. test VidTIMIT data with TTS audio.
```
sh text2video_tts.sh "She had your dark suit in greasy wash water all year." fadg0 f
```

Example 3. test with Chinese female TTS audio.
```
sh text2video_tts_chinese.sh "正在为您查询合肥的天气情况。今天是2020年2月24日，合肥市今天多云，最低温度9摄氏度，最高温度15摄氏度，微风。" henan f
```


## Appendices
ARPABET
![](./ARPABET.png)

## Ackowledgements
This code is based on the vid2vid framework.
