---
name: opus-code-animation
description: 用 Claude Opus 5.5 写代码做动画视频。从 14 种类型（分层插画、手绘草图、水彩、3D、Manim 板书、Blender 黏土、界面动效、Remotion 长片、像素、复古着色器、粒子片头、数据可视化、线稿讲解、素材剪辑加动效）里选型，按 7 要素写提示词，先出分镜再写代码，逐帧渲染成 MP4。用户想做代码动画、动效视频、用代码做视频，或问某种动画风格该用什么工具时使用。
---

# 用 Opus 5.5 做代码动画

代码动画不是让模型直接生成画面：先写一个程序，再由程序按时间画出每一帧，最后用 FFmpeg 合成 MP4。这个 skill 帮你选对类型和工具，把需求写成可执行的提示词，并按固定流程交付成片。

## 流程

1. **问清需求。** 主题、给谁看、时长、横屏还是竖屏、想要的风格、有没有素材或参考、要不要配乐或配音。用户已经说了的不再问，缺的只问关键的一两项，其余用合理默认（15 秒、1920×1080、30 帧、代码合成配乐）。
2. **选类型。** 用下面的速查表，按“想要的效果”找类型。用户点名了工具就用那个；说不清的，给 2 到 3 个候选，每个一句话说明适合的原因，并附上演示视频链接让用户挑。
3. **读参考。** 读选中类型的 `references/types/` 文件，再读 `references/prompt-logic.md`。把类型文件里的示例提示词改写成用户的主题，补齐 7 个要素和通用结尾。
4. **先出分镜。** 按秒列出每个镜头的画面、动作、文字和声音，写成表格给用户确认。用户确认前不写代码。
5. **检查环境。** 按 `references/setup.md` 检查 Node.js、浏览器、FFmpeg、Python，以及这一类型额外需要的工具（Manim、Blender、HyperFrames 等）。缺什么就装什么，装之前告诉用户要装什么。
6. **制作。** 遵守下面的硬规则写代码。先渲染关键帧或几秒小样，确认方向对了再渲染全片。
7. **自检。** 每个镜头至少抽一帧做联系图，检查文字重叠、看不清、穿模、闪烁、超出画面。修好再交付。
8. **交付。** 输出 `out/final.mp4`，告诉用户路径、时长、分辨率。之后的修改一次只改一个点。

## 14 种类型速查

| # | 类型 | 效果 | 工具 | 参考文件 |
| --- | --- | --- | --- | --- |
| 1 | 分层插画 | 纸艺立体书感，图层逐层升起 | Canvas 2D | `references/types/01-layered-illustration.md` |
| 2 | 手绘草图 | 铅笔线条一抖一抖 | Rough.js | `references/types/02-sketch-roughjs.md` |
| 3 | 水彩、水墨 | 笔刷纹理和颜色晕染 | p5.js + p5.brush | `references/types/03-watercolor-p5brush.md` |
| 4 | 3D 场景 | 空间感和电影式运镜 | Three.js | `references/types/04-3d-threejs.md` |
| 5 | 板书动画 | 公式和图形逐步推导 | Manim | `references/types/05-board-manim.md` |
| 6 | 黏土质感 | 真实材质的定格动画 | Blender | `references/types/06-clay-blender.md` |
| 7 | 界面动效 | 按钮、卡片互相变形 | HyperFrames / GSAP | `references/types/07-ui-motion-hyperframes.md` |
| 8 | 动态排版长片 | 大字、图片、字幕多场景切换 | Remotion | `references/types/08-longform-remotion.md` |
| 9 | 像素动画 | 16-bit 游戏质感 | Canvas 2D | `references/types/09-pixel-art.md` |
| 10 | 复古质感 | 老电视、胶片颗粒、光晕 | WebGL 着色器 | `references/types/10-retro-shader.md` |
| 11 | 粒子片头 | 光点聚成文字再散开 | Three.js | `references/types/11-particles-threejs.md` |
| 12 | 数据可视化 | 图表跟着讲解生长 | D3 | `references/types/12-dataviz-d3.md` |
| 13 | 线稿讲解 | 白底手绘线稿 + 配音 | Python + Pillow | `references/types/13-lineart-python.md` |
| 14 | 素材剪辑 + 动效 | 口播自动剪辑，插入动画说明 | video-use | `references/types/14-footage-edit-video-use.md` |

第一次做、用户没有偏好时，优先推荐第 9 种或第 2 种：不需要额外素材和显卡，最容易成功。

## 硬规则

- **画面只由时间 t 决定。** 网页类动画提供 `window.seek(t)`，不用 `setTimeout`、`requestAnimationFrame` 计时、CSS 过渡或帧间状态；随机数用固定种子。否则逐帧截图会跳帧、闪烁。
- **逐帧渲染。** 网页类用 Playwright 按帧调用 `seek(t)` 截图，再用 FFmpeg 合成；Manim、Blender 用它们自己的渲染命令，再用 FFmpeg 混音。
- **禁用模板套路**，除非用户要求：居中大字配渐变背景、所有元素一起淡入、粒子爆炸、霓虹辉光、夸张弹跳、闪屏。
- **数据和事实不编造。** 图表数字由数据计算；虚构的示例数据要在画面上标注。
- **声音合法。** 配乐和音效用代码合成，或用用户有授权的音乐；响度标准化到 -14 LUFS。
- **慢渲染先报时。** 水彩、Blender 这类每帧要几秒的，先渲染单帧，告诉用户单帧耗时和预计总时长。
- **写实人物交给视频模型。** 代码画不好写实人物和自然风景，遇到这类需求要说明，并建议用视频模型生成那部分，再和代码画面合成。

## 更多画风

按画风找灵感时，可以参考这些开源库：[Lemo-Opuscar](https://github.com/lemomo-ai/lemo-opuscar)、[code-animation-prompts](https://github.com/XiaoyeCodes/code-animation-prompts)、[awesome-opus5-5-videos](https://github.com/yihui-dev/awesome-opus5-5-videos)。
