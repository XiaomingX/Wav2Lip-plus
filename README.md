# **Wav2Lip**: *精准同步视频中的嘴巴动作*  

此代码来自于论文：《A Lip Sync Expert Is All You Need for Speech to Lip Generation In the Wild》，发表于 ACM Multimedia 2020。  
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-lip-sync-expert-is-all-you-need-for-speech/lip-sync-on-lrs2)](https://paperswithcode.com/sota/lip-sync-on-lrs2?p=a-lip-sync-expert-is-all-you-need-for-speech)  
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-lip-sync-expert-is-all-you-need-for-speech/lip-sync-on-lrs3)](https://paperswithcode.com/sota/lip-sync-on-lrs3?p=a-lip-sync-expert-is-all-you-need-for-speech)  
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/a-lip-sync-expert-is-all-you-need-for-speech/lip-sync-on-lrw)](https://paperswithcode.com/sota/lip-sync-on-lrw?p=a-lip-sync-expert-is-all-you-need-for-speech)

|📑 论文 |📰 项目页面 |🌀 演示 |⚡ 在线测试 |📔 Colab笔记本 |
|:-:|:-:|:-:|:-:|:-:|
[论文链接](http://arxiv.org/abs/2008.10010) | [项目页面](http://cvit.iiit.ac.in/research/projects/cvit-projects/a-lip-sync-expert-is-all-you-need-for-speech-to-lip-generation-in-the-wild/) | [演示视频](https://youtu.be/0fXaDCZNOJc) | [互动演示](https://synclabs.so/) | [Colab 笔记本](https://colab.research.google.com/drive/1tZpDWXz49W6wDcTprANRGLo2D_EbD5J8?usp=sharing)

---

### **主要特点**
- 通过最新的视觉质量评估更新，提升了模型的效果！
- 高精度的唇动同步：可同步任何目标语言的视频音频，支持任何人物、声音和语言，甚至可以同步 CGI 人物面孔和合成声音。
- 提供完整的训练代码、推理代码和预训练模型。
- 可通过 [Google Colab](https://colab.research.google.com/drive/1tZpDWXz49W6wDcTprANRGLo2D_EbD5J8?usp=sharing) 快速开始。训练和测试样本已上传至 Google Drive [文件夹](https://drive.google.com/drive/folders/1I-0dNLfFOSFwrfqjNa-SXuwaURHE5K4k?usp=sharing)。
- 新增了多个评估基准和可靠的指标，帮助你更好地评估效果。

---

### **免责声明**
此开源代码和演示网站仅限用于研究、学术或个人用途。因模型是基于 LRS2 数据集训练的，严禁用于商业用途。如需商业授权，请直接联系我们！

---

### **使用要求**
- Python 3.6
- ffmpeg：`sudo apt-get install ffmpeg`
- 安装所需的包：`pip install -r requirements.txt`
- 下载并配置面部检测的预训练模型。

---

### **如何使用预训练模型进行唇动同步**
通过以下命令将视频同步到任意音频：
```bash
python inference.py --checkpoint_path <ckpt> --face <video.mp4> --audio <音频文件>
```
结果会保存在 `results/result_voice.mp4` 文件中，当然你也可以自定义保存路径。

**优化提示**：
- 你可以调整 `--pads` 参数来优化人脸框的识别范围，增加下巴区域的底部填充，可能会得到更好的效果。
- 如果嘴巴位置偏移或者出现多个嘴巴的异常情况，可以使用 `--nosmooth` 参数避免过度平滑处理。

---

### **训练数据集 LRS2**
- 将 LRS2 数据集的文件放入 `filelists/` 文件夹。
- 运行预处理命令：`python preprocess.py --data_root data_root/main --preprocessed_root lrs2_preprocessed/`
- 训练时，可以选择不使用视觉质量判别器，或者使用 GAN 版本来提升视觉效果。

---