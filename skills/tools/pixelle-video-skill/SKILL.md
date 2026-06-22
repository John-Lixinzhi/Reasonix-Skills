---
name: pixelle-video-skill
description: [工具] Pixelle-Video视频生成 — 触发条件：需要自动生成短视频/视频内容/数字人/图生视频时。AI全自动短视频引擎：输入主题→自动写文案→生成配图/视频→合成语音→加BGM→输出视频。支持API直连/ComfyUI工作流
---

# Pixelle-Video — AI 全自动短视频引擎

来源：AIDC-AI/Pixelle-Video (23.2k⭐)

输入一个主题，自动完成：文案→配图→配音→BGM→合成视频。

## 核心流程
1. 输入主题
2. AI 智能写文案（支持 GPT/通义千问/DeepSeek/Ollama）
3. AI 生成配图或视频片段（支持 ComfyUI 工作流或直连 API）
4. TTS 语音合成（支持 Edge-TTS/Index-TTS 等）
5. 添加背景音乐
6. 一键合成视频

## 特色功能
- **数字人口播**：生成虚拟数字人播报视频
- **图生视频**：静态图片转动态视频
- **动作迁移**：参考视频+图片进行动作迁移
- **声音克隆**：上传参考音频克隆音色
- **多尺寸**：竖屏/横屏/方形

## 对我生态的价值
- 与 PPT 技能互补：PPT（静态演示）+ Pixelle（动态视频）
- 可以先用 PPT 设计内容，再用 Pixelle 生成配套视频

## 使用方式
```bash
git clone https://github.com/AIDC-AI/Pixelle-Video.git
cd Pixelle-Video
uv run streamlit run web/app.py
```
浏览器打开 http://localhost:8501 即可使用。
