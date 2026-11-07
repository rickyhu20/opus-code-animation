# 7. 界面动效：HyperFrames

**效果：** 按钮、播放器、图表互相变形，弹性顺滑，就是科技公司发布会里常见的那种产品动效。

**工具：** [HyperFrames](https://github.com/heygen-com/hyperframes)，把网页动画渲染成视频的开源工具，自带约 450 个现成组件和配套的 Skill。也可以用 [GSAP](https://github.com/greensock/GSAP) 做时间轴动画。

**怎么做：** 抖音「卡尔的AI沃茨」教程视频给了做产品宣传片的三种办法：

1. **给资料：** 告诉 AI 产品卖点、做给谁看、片子多长、最后希望观众记住什么。
2. **定美术风格：** 提前定好背景、字体、品牌色，比如“颜色只用这三种”“一屏只讲一个卖点”。
3. **复刻宣传片：** 给一条喜欢的参考片，让 AI 反向拆成代码，再换成你的内容。视频里的原始指令是 `reverse this video into HyperFrames code`。

先在 Claude Code 里安装它的 Skill：

```bash
npx hyperframes skills update
```

```text
用 HyperFrames 做一条 15 秒、1920×1080、60 帧的界面动效，使用它的 Skill 并遵守规范。
主题：一个按钮，一路变成整支产品演示，全程不切镜头。
风格：浅灰背景，黑白组件，Inter 字体，动画用弹簧，只允许轻微回弹。
分镜（120 BPM，每一拍都有变化）：
0-3 秒：光标点击“开始”按钮，按钮变成加载圈，再变成对勾。
3-6 秒：对勾展开成音乐播放器，播放键变成暂停键。
6-9 秒：光标拖动进度条，进度条变成音量滑块。
9-12 秒：滑块变成开关，开关变成标签页，标签页展开成一张折线图。
12-15 秒：图表收成搜索框，输入“done”，回车后弹出提示，再变回最初的按钮。
禁止：粒子爆炸、霓虹辉光、渐变按钮、闪屏、夸张弹跳。
用子帧混合做真实运动模糊，最后一帧和第一帧一致，可以无缝循环。
（加上通用结尾，见 references/prompt-logic.md）
```

**演示视频：** [examples/demo-07.mp4](https://github.com/rickyhu20/opus-code-animation/blob/main/examples/demo-07.mp4)
