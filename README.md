
![PySceneDetect](https://raw.githubusercontent.com/Breakthrough/PySceneDetect/main/website/pages/img/pyscenedetect_logo_small.png)
==========================================================
Video Cut Detection and Analysis Tool
----------------------------------------------------------

[![Build Status](https://img.shields.io/github/actions/workflow/status/Breakthrough/PySceneDetect/build.yml)](https://github.com/Breakthrough/PySceneDetect/actions)
[![PyPI Status](https://img.shields.io/pypi/status/scenedetect.svg)](https://pypi.python.org/pypi/scenedetect/)
[![PyPI Version](https://img.shields.io/pypi/v/scenedetect?color=blue)](https://pypi.python.org/pypi/scenedetect/)
[![PyPI License](https://img.shields.io/pypi/l/scenedetect.svg)](https://scenedetect.com/copyright/)

----------------------------------------------------------

# 视频下载与分割逻辑

## 1. 视频下载

### 1.1 功能描述
该脚本用于从JSON数据中解析视频链接，并使用`BBDown.exe`工具下载视频。

### 1.2 代码实现

```python
import subprocess
import json

def download_videos(json_data):
    # 解析JSON数据
    data = json.loads(json_data)

    # 遍历每个视频
    for episode in data['episodes']:
        short_link = episode['short_link']
        print(f"Downloading video: {episode['title']}")

        # 使用subprocess调用BBDown.exe
        try:
            subprocess.run([".\\BBDown.exe", short_link], check=True)
            print(f"Downloaded video: {episode['title']}\n")
        except subprocess.CalledProcessError as e:
            print(f"Failed to download video: {episode['title']}. Error: {e}\n")

# 示例JSON数据
json_data = '''
{
  "episodes": [
    {
      "title": "《原神》EP - 忘忧谐律之歌",
      "link": "bilibili://video/1406050114",
      "bv_id": "BV1M6421f7Q2",
      "short_link": "https://b23.tv/BV1M6421f7Q2"
    },
    {
      "title": "《原神》EP - 晨露浮光之初",
      "link": "bilibili://video/1755988362",
      "bv_id": "BV1N4421D7vc",
      "short_link": "https://b23.tv/BV1N4421D7vc"
    },
    {
      "title": "《原神》EP - 灯影柔寂之夜",
      "link": "bilibili://video/1503593799",
      "bv_id": "BV1KD421n7PG",
      "short_link": "https://b23.tv/BV1KD421n7PG"
    },
    {
      "title": "《原神》EP - 雨濯万象之息",
      "link": "bilibili://video/1152601512",
      "bv_id": "BV1VZ421B7nU",
      "short_link": "https://b23.tv/BV1VZ421B7nU"
    },
    {
      "title": "《原神》游戏剧情EP「轻涟」MV",
      "link": "bilibili://video/493179780",
      "bv_id": "BV17N411g7Ft",
      "short_link": "https://b23.tv/BV17N411g7Ft"
    },
    {
      "title": "《原神》EP - 百草余芳之忆",
      "link": "bilibili://video/493053675",
      "bv_id": "BV1EN411G7km",
      "short_link": "https://b23.tv/BV1EN411G7km"
    },
    {
      "title": "《原神》EP - 逆风散羽之别",
      "link": "bilibili://video/998866289",
      "bv_id": "BV1ax4y197cP",
      "short_link": "https://b23.tv/BV1ax4y197cP"
    },
    {
      "title": "《原神》EP-谛思归悟之境",
      "link": "bilibili://video/229739440",
      "bv_id": "BV1hh411T7WN",
      "short_link": "https://b23.tv/BV1hh411T7WN"
    },
    {
      "title": "《原神》EP - 四时旋舞之熙",
      "link": "bilibili://video/227262361",
      "bv_id": "BV1dh411g7a9",
      "short_link": "https://b23.tv/BV1dh411g7a9"
    },
    {
      "title": "《原神》EP - 如风如露之思",
      "link": "bilibili://video/697325607",
      "bv_id": "BV1wm4y1m7DC",
      "short_link": "https://b23.tv/BV1wm4y1m7DC"
    },
    {
      "title": "《原神》EP - 春露漫散之虹",
      "link": "bilibili://video/823711537",
      "bv_id": "BV1Sg4y1s7Qp",
      "short_link": "https://b23.tv/BV1Sg4y1s7Qp"
    },
    {
      "title": "《原神》EP - 掬尘熠金之梦",
      "link": "bilibili://video/950120887",
      "bv_id": "BV1ys4y1j76C",
      "short_link": "https://b23.tv/BV1ys4y1j76C"
    },
    {
      "title": "《原神》EP - 拈骰冥思之夜",
      "link": "bilibili://video/821387826",
      "bv_id": "BV1KG4y1T76A",
      "short_link": "https://b23.tv/BV1KG4y1T76A"
    },
    {
      "title": "《原神》EP - 信步待春之月",
      "link": "bilibili://video/391787628",
      "bv_id": "BV1vd4y1a72B",
      "short_link": "https://b23.tv/BV1vd4y1a72B"
    },
    {
      "title": "《原神》EP - 妙狐徜徉之影",
      "link": "bilibili://video/347772742",
      "bv_id": "BV1bR4y1f7P2",
      "short_link": "https://b23.tv/BV1bR4y1f7P2"
    },
    {
      "title": "《原神》EP - 硝彩盛放之光",
      "link": "bilibili://video/344024671",
      "bv_id": "BV1Zd4y1K76h",
      "short_link": "https://b23.tv/BV1Zd4y1K76h"
    },
    {
      "title": "《原神》EP - 拨云见日之曦",
      "link": "bilibili://video/600786023",
      "bv_id": "BV1GB4y1p7HC",
      "short_link": "https://b23.tv/BV1GB4y1p7HC"
    },
    {
      "title": "《原神》EP - 花坂豪情之志",
      "link": "bilibili://video/385220196",
      "bv_id": "BV1RZ4y1v7u7",
      "short_link": "https://b23.tv/BV1RZ4y1v7u7"
    },
    {
      "title": "《原神》EP - 白鹭儃伫之思",
      "link": "bilibili://video/640848701",
      "bv_id": "BV1nY4y1a76M",
      "short_link": "https://b23.tv/BV1nY4y1a76M"
    },
    {
      "title": "《原神》EP - 天光澄寂之景",
      "link": "bilibili://video/254589574",
      "bv_id": "BV1UY411g7RU",
      "short_link": "https://b23.tv/BV1UY411g7RU"
    }
  ]
}
'''

# 调用函数下载视频
download_videos(json_data)
```

## 2. 视频分割

### 2.1 功能描述
该脚本用于对指定目录中的视频文件进行分割，使用`HistogramDetector`检测场景变化，并使用`split_video_ffmpeg`进行视频分割。

### 2.2 代码实现

```python
import os
from scenedetect import detect, ContentDetector, split_video_ffmpeg, detectors
from tqdm import tqdm
from IPython import display

def split_videos_in_directory(directory_path):
    # 获取目录中的所有视频文件
    video_files = [f for f in os.listdir(directory_path) if f.endswith(('.mp4', '.avi', '.mkv'))]

    for video_file in tqdm(video_files, desc="Processing videos"):
        video_path = os.path.join(directory_path, video_file)

        # 使用 HistogramDetector 进行视频分割
        scene_list = detect(video_path, detectors.HistogramDetector(threshold=0.02, min_scene_len=60))

        # 打印场景列表长度
        print(f"Scene list length for {video_file}: {len(scene_list)}")

        # 使用 split_video_ffmpeg 进行视频分割
        split_video_ffmpeg(video_path, scene_list, show_progress=True)
        display.clear_output(wait=True)

# 示例调用
directory_path = "EP原数据"
split_videos_in_directory(directory_path)
```

## 3. 类解释和区别讨论

### 3.1 `ContentDetector`

**参数解释：**
- `threshold`：用于判断剪辑的阈值，默认值为27.0。较高的阈值会减少剪辑检测的敏感度，较低的阈值会增加敏感度。
- `min_scene_len`：最小场景长度，默认值为15帧。确保在检测到剪辑后，至少有这么多帧不会被检测为新的剪辑。
- `weights`：用于计算颜色和亮度差异的权重。默认值为`Components(delta_hue=1.0, delta_sat=1.0, delta_lum=1.0, delta_edges=0.0)`，表示在HSV颜色空间中，色调、饱和度和亮度的变化对剪辑检测的影响相同。
- `luma_only`：是否仅使用亮度（亮度）进行检测，默认值为`False`。如果设置为`True`，则仅使用亮度信息进行剪辑检测。
- `kernel_size`：用于边缘检测的内核大小，默认值为`None`。如果设置为整数，将使用该内核大小进行边缘检测。
- `filter_mode`：闪烁过滤模式，默认值为`Mode.MERGE`。用于处理闪烁或快速变化的帧。

**用途**：检测快速剪辑，通过帧之间的颜色和亮度变化来判断。

### 3.2 `AdaptiveDetector`

**参数解释：**
- `adaptive_threshold`：自适应阈值，默认值为3.0。用于调整剪辑检测的敏感度。
- `min_scene_len`：最小场景长度，默认值为15帧。确保在检测到剪辑后，至少有这么多帧不会被检测为新的剪辑。
- `window_width`：窗口宽度，默认值为2。用于计算滚动平均值的窗口大小。
- `min_content_val`：最小内容值，默认值为15.0。用于过滤低内容变化的帧。
- `weights`：用于计算颜色和亮度差异的权重。默认值为`Components(delta_hue=1.0, delta_sat=1.0, delta_lum=1.0, delta_edges=0.0)`，表示在HSV颜色空间中，色调、饱和度和亮度的变化对剪辑检测的影响相同。
- `luma_only`：是否仅使用亮度（亮度）进行检测，默认值为`False`。如果设置为`True`，则仅使用亮度信息进行剪辑检测。
- `kernel_size`：用于边缘检测的内核大小，默认值为`None`。如果设置为整数，将使用该内核大小进行边缘检测。
- `video_manager`：视频管理器，默认值为`None`。用于处理视频帧的输入。
- `min_delta_hsv`：最小HSV差异，默认值为`None`。用于过滤低HSV差异的帧。

**用途**：两遍检测器，首先使用`ContentDetector`计算帧分数，然后应用滚动平均值来处理相机移动等情况下的误检测。

### 3.3 `HistogramDetector`

**参数解释：**
- `threshold`：用于判断剪辑的阈值，默认值为0.05。较高的阈值会减少剪辑检测的敏感度，较低的阈值会增加敏感度。
- `bins`：直方图的箱数，默认值为256。用于计算YUV颜色空间的Y通道直方图。
- `min_scene_len`：最小场景长度，默认值为15帧。确保在检测到剪辑后，至少有这么多帧不会被检测为新的剪辑。

**用途**：通过比较相邻帧的YUV颜色空间Y通道直方图的差异来检测剪辑。

### 3.4 `ThresholdDetector`

**参数解释：**
- `threshold`：用于判断剪辑的阈值，默认值为12。较高的阈值会减少剪辑检测的敏感度，较低的阈值会增加敏感度。
- `min_scene_len`：最小场景长度，默认值为15帧。确保在检测到剪辑后，至少有这么多帧不会被检测为新的剪辑。
- `fade_bias`：淡入淡出偏差，默认值为0.0。用于调整淡入淡出检测的敏感度。
- `add_final_scene`：是否添加最终场景，默认值为`False`。如果设置为`True`，则会在视频结束时添加一个场景。
- `method`：检测方法，默认值为`Method.FLOOR`。用于选择检测淡入淡出的方法。
- `block_size`：块大小，默认值为`None`。用于计算帧亮度的块大小。

**用途**：检测快速剪辑和慢速淡入淡出，通过帧亮度与给定阈值的比较来判断。

### 3.5 比较和选择

1. **`ContentDetector` vs `AdaptiveDetector`**：
   - `ContentDetector`适用于快速剪辑检测，通过颜色和亮度变化来判断。
   - `AdaptiveDetector`在`ContentDetector`的基础上增加了滚动平均值处理，适用于相机移动等情况下的剪辑检测。

2. **`HistogramDetector` vs `ThresholdDetector`**：
   - `HistogramDetector`通过比较YUV颜色空间Y通道直方图的差异来检测剪辑，适用于颜色变化较大的场景。
   - `ThresholdDetector`通过帧亮度与给定阈值的比较来检测剪辑和淡入淡出，适用于亮度变化较大的场景。

3. **选择依据**：
   - 如果视频主要是快速剪辑，且颜色和亮度变化较大，可以选择`ContentDetector`。
   - 如果视频中存在相机移动等情况，可以选择`AdaptiveDetector`。
   - 如果视频主要是颜色变化较大的场景，可以选择`HistogramDetector`。
   - 如果视频主要是亮度变化较大的场景，可以选择`ThresholdDetector`。

根据视频内容和检测需求，选择合适的检测器和参数设置。(剩余的数据集制作及上传流程参见 https://github.com/svjack/LLaVA-NeXT)

### Latest Release: v0.6.5 (November 24, 2024)

**Website**:  [scenedetect.com](https://www.scenedetect.com)

**Quickstart Example**: [scenedetect.com/cli/](https://www.scenedetect.com/cli/)

**Documentation**:  [scenedetect.com/docs/](https://www.scenedetect.com/docs/)

**Discord**: https://discord.gg/H83HbJngk7

----------------------------------------------------------

**Quick Install**:

    pip install scenedetect[opencv] --upgrade

Requires ffmpeg/mkvmerge for video splitting support. Windows builds (MSI installer/portable ZIP) can be found on [the download page](https://scenedetect.com/download/).

----------------------------------------------------------

**Quick Start (Command Line)**:

Split input video on each fast cut using `ffmpeg`:

    scenedetect -i video.mp4 split-video

Save some frames from each cut:

    scenedetect -i video.mp4 save-images

Skip the first 10 seconds of the input video:

    scenedetect -i video.mp4 time -s 10s

More examples can be found throughout [the documentation](https://www.scenedetect.com/docs/latest/cli.html).

**Quick Start (Python API)**:

To get started, there is a high level function in the library that performs content-aware scene detection on a video (try it from a Python prompt):

```python
from scenedetect import detect, ContentDetector
scene_list = detect('my_video.mp4', ContentDetector())
```

`scene_list` will now be a list containing the start/end times of all scenes found in the video.  There also exists a two-pass version `AdaptiveDetector` which handles fast camera movement better, and `ThresholdDetector` for handling fade out/fade in events.

Try calling `print(scene_list)`, or iterating over each scene:

```python
from scenedetect import detect, ContentDetector
scene_list = detect('my_video.mp4', ContentDetector())
for i, scene in enumerate(scene_list):
    print('    Scene %2d: Start %s / Frame %d, End %s / Frame %d' % (
        i+1,
        scene[0].get_timecode(), scene[0].get_frames(),
        scene[1].get_timecode(), scene[1].get_frames(),))
```

We can also split the video into each scene if `ffmpeg` is installed (`mkvmerge` is also supported):

```python
from scenedetect import detect, ContentDetector, split_video_ffmpeg
scene_list = detect('my_video.mp4', ContentDetector())
split_video_ffmpeg('my_video.mp4', scene_list)
```

For more advanced usage, the API is highly configurable, and can easily integrate with any pipeline. This includes using different detection algorithms, splitting the input video, and much more. The following example shows how to implement a function similar to the above, but using [the `scenedetect` API](https://www.scenedetect.com/docs/latest/api.html):

```python
from scenedetect import open_video, SceneManager, split_video_ffmpeg
from scenedetect.detectors import ContentDetector
from scenedetect.video_splitter import split_video_ffmpeg

def split_video_into_scenes(video_path, threshold=27.0):
    # Open our video, create a scene manager, and add a detector.
    video = open_video(video_path)
    scene_manager = SceneManager()
    scene_manager.add_detector(
        ContentDetector(threshold=threshold))
    scene_manager.detect_scenes(video, show_progress=True)
    scene_list = scene_manager.get_scene_list()
    split_video_ffmpeg(video_path, scene_list, show_progress=True)
```

See [the documentation](https://www.scenedetect.com/docs/latest/api.html) for more examples.

## Reference

 - [Documentation](https://www.scenedetect.com/docs/) (covers application and Python API)
 - [CLI Example](https://www.scenedetect.com/cli/)
 - [Config File](https://www.scenedetect.com/docs/0.6.4/cli/config_file.html)

## Help & Contributing

Please submit any bugs/issues or feature requests to [the Issue Tracker](https://github.com/Breakthrough/PySceneDetect/issues). Before submission, ensure you search through existing issues (both open and closed) to avoid creating duplicate entries.
Pull requests are welcome and encouraged.  PySceneDetect is released under the BSD 3-Clause license, and submitted code should be compliant.

For help or other issues, you can join [the official PySceneDetect Discord Server](https://discord.gg/H83HbJngk7), submit an issue/bug report [here on Github](https://github.com/Breakthrough/PySceneDetect/issues), or contact me via [my website](http://www.bcastell.com/about/).

## Code Signing

This program uses free code signing provided by [SignPath.io](https://signpath.io?utm_source=foundation&utm_medium=github&utm_campaign=PySceneDetect), and a free code signing certificate by the [SignPath Foundation](https://signpath.org?utm_source=foundation&utm_medium=github&utm_campaign=PySceneDetect)

## License

BSD-3-Clause; see [`LICENSE`](LICENSE) and [`THIRD-PARTY.md`](THIRD-PARTY.md) for details.

----------------------------------------------------------

Copyright (C) 2014-2024 Brandon Castellano.
All rights reserved.
