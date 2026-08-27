# 赣鄱山水 · 江西旅行画册

一本可以翻页、缩放和用放大镜探索的江西水彩旅行画册。

项目以十五幅开放书本跨页串起江西的山水、湖泊、古建、村落、窑火与红色记忆。拖动纸页时，页面会像真实纸张一样弯曲；把黄铜放大镜移到画面上，可以查看水彩和线稿的局部细节。

![滕王阁水彩画册跨页](sketchbook/tengwang-pavilion.webp)

## 十五处风景

1. 滕王阁 · 南昌
2. 鄱阳湖候鸟湿地 · 九江
3. 庐山 · 九江
4. 白鹿洞书院 · 九江
5. 景德镇御窑 · 景德镇
6. 婺源篁岭 · 上饶
7. 三清山 · 上饶
8. 龙虎山 · 鹰潭
9. 明月山 · 宜春
10. 武功山 · 萍乡
11. 仙女湖 · 新余
12. 井冈山 · 吉安
13. 流坑古村 · 抚州
14. 江南宋城 · 赣州
15. 共和国摇篮 · 瑞金

景点组合覆盖江西全部 11 个设区市，兼顾自然山水、湖泊湿地、历史建筑、陶瓷文化、传统村落与红色文化。主要资料参考：

- [Lushan National Park](https://whc.unesco.org/en/list/778/)
- [Mount Sanqingshan National Park](https://whc.unesco.org/en/list/1292/)
- [China Danxia](https://whc.unesco.org/en/list/1335/)
- [江西武功山—明月山景区](https://dct.jiangxi.gov.cn/jxswhhlyt/col/col21664/content/content_1764652183524667392.html)
- [仙女湖七夕文化旅游度假区](https://dct.jiangxi.gov.cn/jxswhhlyt/col/col14513/content/content_1764576259747803136.html)
- [抚州古村落文化](https://dct.jiangxi.gov.cn/jxswhhlyt/col/col15527/content/content_1764618146701570048.html)
- [鄱阳湖候鸟观赏线路](https://dct.jiangxi.gov.cn/jxswhhlyt/col/col14513/content/content_1764581375003521024.html)
- [白鹿洞书院](https://dct.jiangxi.gov.cn/jxswhhlyt/col/col15502/content/content_1764467240923410432.html)
- [瑞金共和国摇篮](https://www.ganzhou.gov.cn/zfxxgk/c144214/202211/d77e67db4e304c5fb7a1974d5bf3090f.shtml)

## 交互

- 拖动书页翻页，拖动速度会影响页面落下或回弹。
- 使用左右箭头、画面两侧热区或键盘方向键切换景点。
- 拖动放大镜查看局部水彩细节。
- 使用工具栏缩放画册，双击恢复到 100%。
- 通过下方景点索引直接跳到指定跨页。
- 触屏设备自动隐藏放大镜并改用点击翻页。
- `prefers-reduced-motion` 会跳过开场连续翻页并减少动画。

## 技术实现

- 原生 HTML、CSS 和 JavaScript，无框架、无第三方运行时依赖。
- 主要布局、样式、翻页几何、状态机和交互都位于 `index.html`。
- 翻页纸张由 18 个嵌套窄条构成，通过 CSS 3D、正反面、逐帧光影和弹簧动画模拟弯曲。
- 放大镜克隆当前书页，使用圆形 Mask 和坐标变换显示约 2.3 倍的局部内容。
- 十五张插画统一为 1760 × 1240、带透明通道的 WebP，合计约 2.8MB。

## 本地运行

```sh
python3 -m http.server 4173
```

然后打开 `http://localhost:4173`。直接打开 `index.html` 也可以，但通过 HTTP 加载字体更稳定。

## 部署

仓库内置 GitHub Pages 工作流。推送到 `main` 后，可在仓库的 **Settings → Pages** 中选择 **GitHub Actions** 作为 Source。

## 改编与署名

本项目 Fork 并改编自 [MengTo/sketchbook](https://github.com/MengTo/sketchbook)，原项目概念参考了 [matthewyuart/personalportfolio](https://github.com/matthewyuart/personalportfolio)。江西版保留了原项目的翻页、放大镜、视差和缩放交互，并重新制作了全部景点插画、中文内容、元数据与资源加载方案。

十五张江西插画使用 AI 图像生成制作，并根据真实景点的建筑和地貌特征统一构图、透明背景和画册尺寸。

## 授权说明

上游仓库当前没有提供明确的开源许可证。本 Fork 不额外声明对上游代码的再授权；复制、分发或商用前，请确认已获得上游作者许可。江西版新增插画和文字内容同样不因仓库公开而自动授予商用授权。