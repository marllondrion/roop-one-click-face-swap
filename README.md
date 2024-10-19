# Roop

> Take a video and replace the face in it with a face of your choice. You only need one image of the desired face. No dataset, no training.


<img src="https://i.ibb.co/4RdPYwQ/Untitled.jpg"/>

## Installation

Be aware, the installation needs technical skills and is not for beginners. Please do not open platform and installation related issues on GitHub.


[Basic](#installation) - It is more likely to work on your computer, but will be quite slow

[Acceleration](#Acceleration) - Unleash the full potential of your CPU and GPU


## Usage

Start the program with arguments:

```
python run.py [options]

-h, --help                                                                 show this help message and exit
-s SOURCE_PATH, --source SOURCE_PATH                                       select an source image
-t TARGET_PATH, --target TARGET_PATH                                       select an target image or video
-o OUTPUT_PATH, --output OUTPUT_PATH                                       select output file or directory
--frame-processor FRAME_PROCESSOR [FRAME_PROCESSOR ...]                    frame processors (choices: face_swapper, face_enhancer, ...)
--keep-fps                                                                 keep target fps
--keep-frames                                                              keep temporary frames
--skip-audio                                                               skip target audio
--many-faces                                                               process every face
--reference-face-position REFERENCE_FACE_POSITION                          position of the reference face
--reference-frame-number REFERENCE_FRAME_NUMBER                            number of the reference frame
--similar-face-distance SIMILAR_FACE_DISTANCE                              face distance used for recognition
--temp-frame-format {jpg,png}                                              image format used for frame extraction
--temp-frame-quality [0-100]                                               image quality used for frame extraction
--output-video-encoder {libx264,libx265,libvpx-vp9,h264_nvenc,hevc_nvenc}  encoder used for the output video
--output-video-quality [0-100]                                             quality used for the output video
--max-memory MAX_MEMORY                                                    maximum amount of RAM in GB
--execution-provider {cpu} [{cpu} ...]                                     available execution provider (choices: cpu, ...)
--execution-threads EXECUTION_THREADS                                      number of execution threads
-v, --version                                                              show program's version number and exit
```


### Headless

Using the `-s/--source`, `-t/--target` and `-o/--output` argument will run the program in headless mode.


## Disclaimer

This software is designed to contribute positively to the AI-generated media industry, assisting artists with tasks like character animation and models for clothing.

We are aware of the potential ethical issues and have implemented measures to prevent the software from being used for inappropriate content, such as nudity.

Users are expected to follow local laws and use the software responsibly. If using real faces, get consent and clearly label deepfakes when sharing. The developers aren't liable for user actions.


## Licenses

Our software uses a lot of third party libraries as well pre-trained models. The users should keep in mind that these third party components have their own license and terms, therefore our license is not being applied.


## Credits

- [deepinsight](https://github.com/deepinsight) for their [insightface](https://github.com/deepinsight/insightface) project which provided a well-made library and models.


==================================

# Installation

## 1. Setup your platform
### Linux
Python
```bash
sudo apt install python3.10
```
PIP
```bash
sudo apt install python3-pip
```
GIT
```bash
sudo apt install git-all
```
FFmpeg
```bash
sudo apt install ffmpeg
```


### MacOS

Python
```bash
brew install python@3.10
```
PIP
```bash
python -m ensurepip
```
GIT
```bash
brew install git
```
FFmpeg
```bash
brew install ffmpeg
```

### Windows
Python
```bash
winget install -e --id Python.Python.3.10
```
PIP
```bash
python -m ensurepip
```
GIT
```bash
winget install -e --id Git.Git
```
FFmpeg
```bash
winget install -e --id Gyan.FFmpeg
```
Reboot your system in order for FFmpeg to function properly.
```bash
shutdown /r
```

#### Toolset
Microsoft Visual C++ 2015 Redistributable
```bash
winget install -e --id Microsoft.VCRedist.2015+.x64
```
Microsoft Visual Studio 2022 build tools
During installation, ensure to select the Desktop Development with C++ package.
```bash
winget install -e --id Microsoft.VisualStudio.2022.BuildTools --override "--wait --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended"
```

## 2. Clone Repository
```bash
git clone https://github.com/s0md3v/roop
```

## 3. Install dependencies
We highly recommend to work with a venv or conda to avoid issues.

```bash
pip install -r requirements.txt
```

## 4. Done
You should be able to run roop using python run.py command. Keep in mind that while running the program for first time, it will download some models which can take time depending on your network connection.


# Acceleration

CUDA (Nvidia)
Install CUDA Toolkit 11.8 and cuDNN for Cuda 11.x

Install dependencies:
```bash
pip uninstall onnxruntime onnxruntime-gpu
pip install onnxruntime-gpu==1.15.1
```

Usage in case the provider is available:
```bash
python run.py --execution-provider cuda
```
### CoreML (Apple)
Apple Silicon
Install dependencies:
```bash
pip uninstall onnxruntime onnxruntime-silicon
pip install onnxruntime-silicon==1.13.1
``` 
Usage in case the provider is available:
```bash
python run.py --execution-provider coreml
Apple Legacy
```
1.Install dependencies:
```bash
pip uninstall onnxruntime onnxruntime-coreml
pip install onnxruntime-coreml==1.13.1
```
Usage in case the provider is available:
```bash
python run.py --execution-provider coreml
```
DirectML (Windows)
Install dependencies:
```bash
pip uninstall onnxruntime onnxruntime-directml
pip install onnxruntime-directml==1.15.1
```
Usage in case the provider is available:
```bash
python run.py --execution-provider dml
```
OpenVINO (Intel)
Install dependencies:
```bash
pip uninstall onnxruntime onnxruntime-openvino
pip install onnxruntime-openvino==1.15.0
```
Usage in case the provider is available:
```bash
python run.py --execution-provider openvino
```

