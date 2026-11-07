# 14. 素材剪辑 + 动效：video-use

**效果：** 把口播或实拍素材剪成成片，自动去掉“嗯、呃”和停顿，调色、加字幕，并在关键处插入动画说明。前 13 种是用代码从零画出画面，这一种是在真实素材上加代码动画。

**工具：** [video-use](https://github.com/browser-use/video-use)，一个用 Claude Code 剪视频的开源项目，里面的动画可以调用 HyperFrames、Remotion 或 Manim 来做。安装时需要 ElevenLabs 的 API Key。

**怎么做：** 把素材放进一个文件夹，先让 Claude Code 安装 video-use，再说清楚要留什么、删什么、什么风格。

第一步，先发这条安装：

```text
Set up https://github.com/browser-use/video-use for me. Read install.md first and follow it. Ask me when you need an API key.
```

装好后再发：

```text
用 video-use 把当前文件夹里的素材剪成不超过 60 秒的 1080×1920 竖屏视频。
剪辑要求：
- 先转录素材，把逐字稿和你建议保留的段落发给我，我确认后再剪。
- 删除“嗯、呃”、重复的句子和过长的停顿，不改变我的原意。
- 开头 3 秒放最有吸引力的一句话。
- 轻微统一调色，保持肤色自然；每个剪辑点做短音频淡变，不能有爆音。
- 字幕每次 2 到 6 个字，放在安全区内，关键词用橙色。
动效要求：
- 讲到关键概念时，插入 3 到 5 个简短的动画说明，每个不超过 4 秒，不要遮挡我的脸。
- 用 HyperFrames 制作这些动画，风格统一为米白背景、黑字、橙色强调。
渲染后自己检查每个剪辑点并修复问题，最后告诉我视频路径。
```

**演示视频：** [examples/demo-14.mp4](https://github.com/rickyhu20/opus-code-animation/blob/main/examples/demo-14.mp4)
