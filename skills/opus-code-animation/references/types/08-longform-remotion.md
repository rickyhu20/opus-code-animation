# 8. 动态排版长片：Remotion

**效果：** 大字跟着节奏弹出，图片、字幕、图表不断切换，适合几分钟的知识视频和产品介绍。

**工具：** [Remotion](https://github.com/remotion-dev/remotion)，用 React 写视频的开源框架，官方还提供了 [Remotion Skills](https://github.com/remotion-dev/skills)。商用前记得看一下它的授权条款。

**怎么做：** 把文案拆成场景，每个场景单独制作，可以在 Remotion Studio 里拖动预览，只改有问题的镜头。

```bash
npx skills add remotion-dev/skills
```

```text
用 Remotion 做一条 45 秒、1080×1920 竖屏、30 帧的知识视频，遵守 Remotion Skills 的规范。
文案（每句一个场景）：
1. 这条视频，不是 AI 生成的像素。
2. 它是 AI 写出来的代码。
3. 视频模型靠描述直接生成画面。
4. 代码动画是先写程序，再让程序一帧一帧画出来。
5. 所以文字不会变形，细节不会闪。
6. 改一个颜色，只需要改一行代码。
7. 现在，想法比软件更重要。
风格：米白背景、黑色粗体、橙色强调，每屏只讲一句，关键词用大字弹出，用遮罩显示和匹配剪辑转场。
禁止：居中大字配渐变背景、所有元素一起淡入、闪屏和抖动。
为短视频平台的界面留出安全区，配上代码合成的轻快配乐。
先给我每句的时长和画面设计，我确认后再写代码，每个场景抽一帧自检，最后告诉我视频路径。
```

**演示视频：** [examples/demo-08.mp4](https://github.com/rickyhu20/opus-code-animation/blob/main/examples/demo-08.mp4)
