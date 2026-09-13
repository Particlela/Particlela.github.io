# 高恒斌 - 学术简历 (LaTeX)

本目录包含高恒斌学术简历的完整 LaTeX 源码和编译后的 PDF。

## 文件说明

- **`cv.tex`** - LaTeX 主文件，包含所有简历内容和格式设置
- **`cv.pdf`** - 编译后的 PDF 文件（可直接下载）
- **`profile.jpg`** - 个人证件照（3cm 宽度）
- **`citations.bib`** - BibTeX 参考文献数据库（目前未使用，为将来出版物预留）
- **`Makefile`** - 编译脚本，用于自动化 PDF 生成
- **`README.md`** - 本文档

## 当前 CV 内容

### 个人信息
- **姓名**: 高恒斌
- **身份**: 本科生，浙江大学信息工程
- **学院**: 信息科学与电子工程学院
- **个人邮箱**: Particle_Nebula@outlook.com
- **学院邮箱**: 3230105132@zju.edu.cn
- **电话**: (+86) 19883109386
- **网站**: https://Particlela.github.io
- **GitHub**: @Particlela

### CV 章节结构

1. **个人简介** - 个人介绍与研究方向
   - 浙江大学信息工程专业本科三年级
   - 串联弹性腿机器人控制、四开关 Buck-Boost 缓冲电容器控制
   - 未来方向：机器学习、数字信号/图像处理、嵌入式系统

2. **教育背景**
   - 浙江大学，信息工程学士学位（2023-2027）
   - 信息科学与电子工程学院
   - 专业 GPA：4.48/5.0；总 GPA：4.46/5.0

3. **荣誉奖项**
   - 2026 RoboMaster 机甲大师超级对抗赛—哨兵机器人竞赛 二等奖
   - 2026 RoboMaster 机甲大师超级对抗赛—步兵机器人竞赛 三等奖
   - 2025 RoboMaster 机甲大师超级对抗赛—全国总决赛 一等奖（全国八强）
   - 2025 RoboMaster 机甲大师超级对抗赛—步兵机器人竞赛 一等奖
   - 2025 国家人才培养基地三等奖学金
   - 2025 浙江大学三等奖学金
   - 2024 浙江省政府奖学金
   - 2024 浙江大学二等奖学金

4. **项目经历**
   - **RoboMaster 串联弹性腿平衡步兵机器人控制系统**（2024年10月 - 至今）：STM32H7 平台，可变增益 LQR 平衡控制、优先级分层状态机、两级能量缓冲、二次模型功率限幅器。
   - **RoboMaster 串联弹性腿哨兵机器人控制系统**（2025年8月 - 至今）：在步兵基础上升级为自主导航哨兵，新增底盘导航指令接口。
   - **双向四开关 Buck-Boost 缓冲电容器控制系统（FSBB）**（2026年6月 - 至今）：STM32G4，多环路 PI 控制 + 电压比前馈、状态机调度、高带宽 ADC/DMA 反馈。
   - **HW-Components：通用机器人控制库**（2024年10月 - 至今）：嵌入式通信层、CAN/UART 多协议、测距传感器、裁判系统、杠杆臂补偿。

5. **专业技能**
   - 编程语言：C/C++, Python, MATLAB
   - 嵌入式平台：STM32 (H7/G4), NUC, Raspberry Pi
   - 控制理论：PID, LQR, MPC, EKF, 状态机, 自适应控制
   - 通信协议：CAN, UART, SPI, I2C, DMA
   - 开发工具：CMake, Git, Linux, ROS2, OpenCV, LaTeX

## 特色设计

### 视觉设计
- ✅ **蓝色章节标题** - 专业的深蓝色 (RGB: 0, 102, 204)
- ✅ **个人照片** - 右上角 3cm 证件照
- ✅ **清晰布局** - 姓名左对齐，联系方式两行排列
- ✅ **图标增强** - Font Awesome 图标美化联系方式

### 内容组织
- ✅ **教育和荣誉前置** - 在项目经历之前展示
- ✅ **项目链接** - 链接到个人网站的详细页面
- ✅ **时间倒序** - 最新经历在前

## 编译 PDF

### 方法一：使用 Make（推荐）

确保系统已安装 `make` 和完整的 LaTeX 发行版（TeX Live 或 MiKTeX）：

```bash
cd files/cv_CN
make          # 编译生成 cv.pdf
make clean    # 清理中间文件（.aux, .log, .out 等）
make distclean # 清理所有文件（包括 PDF）
```

### 方法二：使用 latexmk

```bash
cd files/cv_CN
latexmk -pdf cv.tex
```

### 方法三：手动编译

```bash
xelatex cv.tex
# 如果使用参考文献：
# biber cv
# xelatex cv.tex
xelatex cv.tex
```

**注意**：
- 本简历包含中文，请使用 **XeLaTeX** 编译（推荐 `xelatex` 或 `latexmk -xelatex`）。
- 中间文件（.aux, .log, .bcf, .out, .run.xml, .synctex.gz）会被 `.gitignore` 自动忽略
- 只需提交 `cv.tex`, `cv.pdf`, `profile.jpg`, `citations.bib` 等源文件

## 在线编辑（可选）

如果不想在本地安装 LaTeX：

### Overleaf
1. 访问 [Overleaf](https://www.overleaf.com/)
2. 创建新项目，上传所有文件（cv.tex, profile.jpg, citations.bib）
3. 编译器选择 **XeLaTeX**
4. 在线编辑并实时预览
5. 下载编译后的 PDF

## 更新 CV 内容

### 修改个人信息

编辑 `cv.tex` 中的标题部分（约第 145-152 行）：

```latex
\begin{tabularx}{\linewidth}{@{} X r @{}}
\Huge{你的姓名} & \multirow{6}{*}{\includegraphics[width=3cm]{profile.jpg}} \\[3pt]
\normalsize{\textit{你的身份}} & \\
\normalsize{\textit{你的学校和专业}} & \\[10pt]
\href{mailto:your.email@example.com}{...} & \\[3pt]
\href{https://yourwebsite.com}{...} \ $|$ \
\href{https://github.com/yourusername}{...} & \\
\end{tabularx}
```

### 修改各章节内容

**个人简介**:
```latex
\section{个人简介}
在这里写你的个人简介和研究兴趣...
```

**教育背景**:
```latex
\section{教育背景}
\begin{tabularx}{\linewidth}{@{}l X@{}}
2023 - 2027 & 学位 at \textbf{大学名称} \\
& 学院名称 \\
& GPA: xx/xx \\
\end{tabularx}
```

**项目经历**:
```latex
\begin{tabularx}{\linewidth}{ @{}l r@{} }
\textbf{项目名称} & \hfill \href{链接}{时间段} \\[3.75pt]
\multicolumn{2}{@{}X@{}}{项目详细描述...}  \\
\end{tabularx}
```

### 添加/修改照片

1. 将新照片命名为 `profile.jpg`（或修改 cv.tex 中的文件名）
2. 建议尺寸：证件照规格，宽度会自动调整为 3cm
3. 替换文件后重新编译

### 调整颜色

当前章节标题使用蓝色，如需修改（约第 81 行）：

```latex
% 修改为其他颜色
\definecolor{sectioncolor}{RGB}{0, 102, 204}  % 当前蓝色
% \definecolor{sectioncolor}{RGB}{0, 128, 0}  % 绿色
% \definecolor{sectioncolor}{RGB}{139, 0, 0}  % 深红色
```

### 添加出版物（未来）

当有学术出版物时，在 `citations.bib` 中添加：

```bibtex
@article{gao2026robotics,
    title = {Your Paper Title},
    author = {Gao, Hengbin and Coauthor, Name},
    journal = {Journal Name},
    year = {2026},
    volume = {1},
    pages = {1--10}
}
```

然后取消 cv.tex 中的注释（约第 230-234 行）：

```latex
\section{Publications}
\begin{refsection}[citations.bib]
\nocite{*}
\printbibliography[heading=none]
\end{refsection}
```

## 在个人网站中使用

### 当前配置

CV PDF 可以通过以下方式访问：

1. **边栏下载链接** - 所有页面的左侧边栏底部都有简历下载链接
   - 文件位置：`_includes/author-profile.html`
   - 链接到：`/files/cv_CN/cv.pdf`

2. **直接 URL 访问**
   - https://Particlela.github.io/files/cv_CN/cv.pdf

### 更新流程

每次修改 CV 后：
1. 编辑 `cv.tex` 文件
2. 编译生成新的 `cv.pdf`：`make`
3. 检查 PDF 内容是否正确
4. 提交到 Git：
   ```bash
   git add cv.tex cv.pdf
   git commit -m "Update CV"
   git push
   ```
5. 等待 GitHub Pages 部署（约 1-2 分钟）
6. 访问网站验证新 CV

## 技术细节

### LaTeX 包依赖

- `ctex` - 中文支持（需要 XeLaTeX）
- `tabularx` - 灵活的表格布局
- `multirow` - 多行单元格（用于照片）
- `fontawesome5` - 图标字体
- `xcolor` - 颜色支持
- `titlesec` - 自定义章节格式
- `hyperref` - 超链接支持
- `graphicx` - 图片插入
- `biblatex` - 参考文献管理（可选）

### 文件编码

- 使用 UTF-8 编码
- 使用 XeLaTeX 编译以支持中文

### 布局设置

- 纸张：A4
- 字体大小：12pt
- 页边距：通过 `geometry` 包设置为 0.9 倍
- 章节标题：Large 字体，蓝色，带下划线

## 常见问题

### Q: 编译时中文显示乱码或报错？

A: 请使用 XeLaTeX 编译，不要使用 pdfLaTeX：
```bash
xelatex cv.tex
```
或在 Overleaf 中将编译器设置为 XeLaTeX。

### Q: 照片和文字重叠怎么办？

A: 调整 `\multirow` 的行数（当前为 6）：
```latex
\multirow{6}{*}{\includegraphics[width=3cm]{profile.jpg}}
% 增加数字以增加照片占用的行数
```

### Q: 如何修改章节标题颜色？

A: 修改 `\definecolor{sectioncolor}` 的 RGB 值：
```latex
\definecolor{sectioncolor}{RGB}{0, 102, 204}  % 蓝色
```

### Q: 编译时出现错误？

A: 常见解决方法：
1. 确保安装了完整的 LaTeX 发行版
2. 删除所有中间文件：`make clean` 或手动删除 .aux, .log 等
3. 检查特殊字符是否正确转义（如 &, %, # 等）
4. 确保 `profile.jpg` 文件存在
5. 中文内容请使用 XeLaTeX 编译

### Q: 如何改变 PDF 文件名？

A: 修改 `Makefile` 中的 `NAME` 变量，或直接重命名编译后的文件。

## 版本历史

- **2026.09** - 重写个人信息和项目内容，更新为高恒斌的真实资料
- **2025.10** - 添加蓝色章节标题，个人照片集成
- **2025.10** - 初始版本，基于 autoCV 模板定制

## 参考资源

- **模板来源**: [autoCV](https://github.com/jitinnair1/autoCV) - MIT License
- **LaTeX 文档**: [Overleaf Documentation](https://www.overleaf.com/learn)
- **Font Awesome**: [fontawesome.com](https://fontawesome.com/)

## 维护者

**高恒斌**
- Email: Particle_Nebula@outlook.com / 3230105132@zju.edu.cn
- Phone: (+86) 19883109386
- GitHub: [@Particlela](https://github.com/Particlela)
- Website: [Particlela.github.io](https://Particlela.github.io)

---

*Last updated: September 2026*