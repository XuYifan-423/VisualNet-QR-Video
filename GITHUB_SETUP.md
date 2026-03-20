# GitHub 仓库设置说明

## 项目概述
这是一个基于QR码的视频数据传输系统，可以将任意文件编码为QR码序列并嵌入视频中，也可以从视频中提取QR码序列并还原原始文件。

## 仓库结构说明

### 需要上传的文件
- **源代码文件** (`newvisualnet/` 目录下的 `.cpp` 和 `.h` 文件)
- **项目文件** (`*.sln`, `*.vcxproj`) - 用于Visual Studio开发
- **编译好的可执行文件** (`x64/Debug/newvisualnet.exe`) - 用户可以直接使用
- **依赖库文件**：
  - `opencv/build/bin/opencv_videoio_ffmpeg4120_64.dll` - OpenCV FFmpeg支持库
  - `ffmpeg-2026-03-05-git-74cfcd1c69-essentials_build/bin/` - FFmpeg工具

### 被忽略的文件（在.gitignore中）
- 编译中间文件 (`.obj`, `.pdb`, `.idb`, `.ilk`, `.exp`, `.tlog`)
- Visual Studio临时文件 (`.vs/`, `.suo`, `.db`)
- 用户配置文件 (`.vcxproj.user`)
- 临时测试文件 (`input/temp/`, `output/temp/`)

## 使用说明

### 直接使用（无需编译）
1. 下载仓库到本地
2. 进入 `x64/Debug/` 目录
3. 直接运行 `newvisualnet.exe` 查看可用命令

### 开发环境搭建
1. 安装 Visual Studio 2019 或更高版本
2. 打开 `newvisualnet.sln` 解决方案文件
3. 确保以下依赖库已正确配置：
   - OpenCV 4.1.2 或更高版本
   - FFmpeg 最新版本

## 主要功能

### 编码功能
- `qr-encode <输入文件>` - 将文件编码为QR码序列
- `qr-to-video <输出视频>` - 将QR码序列合成为视频

### 解码功能  
- `video-to-frames <输入视频> <输出目录>` - 从视频中提取帧
- `qr-decode <输入目录> <输出文件>` - 从QR码序列还原文件
- `decode-single-image <图片路径>` - 解码单张QR码图片

### 测试功能
- `test-qr` - 测试QR码编码和解码
- `test-qr-file` - 测试文件编码和解码
- `draw-layout <输出图片路径>` - 绘制QR码布局

## 依赖说明

### 运行时依赖
- **OpenCV DLL**: `opencv/build/bin/opencv_videoio_ffmpeg4120_64.dll`
- **FFmpeg工具**: `ffmpeg-2026-03-05-git-74cfcd1c69-essentials_build/bin/`

### 开发依赖
- OpenCV 4.1.2+ 头文件和库文件
- FFmpeg 开发库
- Visual Studio 2019+

## 注意事项

1. **路径问题**: 确保所有文件路径使用正斜杠 `/` 或双反斜杠 `\\`
2. **依赖库**: 可执行文件需要与依赖DLL在同一目录或系统PATH中
3. **视频格式**: 支持常见的视频格式，建议使用MP4格式
4. **QR码尺寸**: 默认使用133x133像素的QR码，可调整配置

## 许可证
项目代码遵循相应的开源许可证，具体请查看各依赖库的许可证文件。