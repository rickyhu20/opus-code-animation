# 3. 水彩、水墨：p5.js + p5.brush

**效果：** 有笔刷纹理和颜色晕染，开源 MV《I'm Upping My P(doom)》就是这一种。

**工具：** [p5.js](https://github.com/processing/p5.js) 负责画图，[p5.brush](https://github.com/acamposuribe/p5.brush) 负责笔刷和水彩。最省事的是直接用开源的 [ClaudeAnimationBase](https://github.com/JohnHeibel/ClaudeAnimationBase)，里面已经配好了角色、动画规则和渲染脚本。

**怎么做：** 让 Claude Code 把这个项目克隆下来，先读里面的动画指南，再让它做你的故事。

```text
把 https://github.com/JohnHeibel/ClaudeAnimationBase 克隆到当前文件夹，先读 ANIMATION_GUIDE.md 并严格遵守。
然后做一条 20 秒的水彩动画，主角用仓库自带的 Clawd，故事叫“种下一颗星星”：
0-5 秒：夜晚，Clawd 在窗边看到一颗小星星落进花盆。
5-10 秒：它开心地浇水，花盆里长出发光的嫩芽。
10-15 秒：嫩芽长成小树，枝头亮起很多小星星。
15-20 秒：星星飘回夜空，Clawd 挥手告别，用笔刷转场收尾。
保留笔刷纹理和水彩晕染，不出现任何文字。先渲染单帧，告诉我每帧耗时和预计总时长。
先给我分镜表，我确认后再写代码，用仓库的 render.mjs 渲染，最后告诉我视频路径。
```

注意：没有独立显卡的电脑渲染水彩会比较慢，每帧可能要几秒。

**演示视频：** [examples/demo-03.mp4](https://github.com/rickyhu20/opus-code-animation/blob/main/examples/demo-03.mp4)
