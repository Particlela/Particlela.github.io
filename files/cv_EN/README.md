# Hengbin Gao - Academic CV (LaTeX)

This directory contains the complete LaTeX source code and compiled PDF for Hengbin Gao's academic CV.

## File Description

- **`cv.tex`** - Main LaTeX file containing all CV content and formatting settings
- **`cv.pdf`** - Compiled PDF file (ready for download)
- **`profile.jpg`** - Personal ID photo (3cm width)
- **`citations.bib`** - BibTeX bibliography database (reserved for future publications)
- **`Makefile`** - Build script for automated PDF generation
- **`README.md`** - This document

## Current CV Content

### Personal Information
- **Name**: Hengbin Gao
- **Role**: Undergraduate, Zhejiang University, Information Engineering
- **College**: College of Information Science and Electronic Engineering
- **Personal Email**: Particle_Nebula@outlook.com
- **Institutional Email**: 3230105132@zju.edu.cn
- **Phone**: (+86) 19883109386
- **Website**: https://Particlela.github.io
- **GitHub**: @Particlela

### CV Section Structure

1. **Summary** - Introduction and Research Interests
   - Third-year undergraduate at Zhejiang University, majoring in Information Engineering
   - Research focus: series-elastic leg robot control; FSBB buffer-capacitor control
   - Forward-looking interests: machine learning, digital signal/image processing, embedded systems

2. **Education** - Academic Background
   - Zhejiang University, B.Eng. in Information Engineering (2023 - 2027)
   - College of Information Science and Electronic Engineering
   - Major GPA: 4.48/5.0; Overall GPA: 4.46/5.0

3. **Honors & Awards** - Achievements
   - 2026 RoboMaster University Championship — Sentry Robot Competition: Second Prize
   - 2026 RoboMaster University Championship — Infantry Robot Competition: Third Prize
   - 2025 RoboMaster University Championship — National Final: First Prize (National Top 8)
   - 2025 RoboMaster University Championship — Infantry Robot Competition: First Prize
   - 2025 Third Prize Scholarship, National Talent Training Base
   - 2025 Third Prize Scholarship, Zhejiang University
   - 2024 Provincial Government Scholarship, Zhejiang University
   - 2024 Second Prize Scholarship, Zhejiang University

4. **Projects**
   - **RoboMaster: Series-Elastic Leg Balancing Infantry Robot Control System** (Oct 2024 - Present): STM32H7 platform, variable-gain LQR balance control, priority-based hierarchical state machine, two-stage energy buffer, quadratic-model power limiter.
   - **RoboMaster: Series-Elastic Leg Sentry Robot Control System** (Aug 2025 - Present): autonomous navigation upgrade with chassis command interface.
   - **Bidirectional Four-Switch Buck-Boost Buffer Capacitor Control System (FSBB)** (June 2026 - Present): STM32G4, multi-loop PI control with voltage-ratio feedforward, state-machine scheduling, high-bandwidth ADC/DMA feedback.
   - **HW-Components: Universal Robot Control Library** (Oct 2024 - Present): embedded communication layer, CAN/UART multi-protocol, ranging sensors, referee system, lever-arm compensation.

5. **Skills**
   - Programming Languages: C/C++, Python, MATLAB
   - Embedded Platforms: STM32 (H7/G4), NUC, Raspberry Pi
   - Control Theory: PID, LQR, MPC, EKF, State Machine, Adaptive Control
   - Communication Protocols: CAN, UART, SPI, I2C, DMA
   - Development Tools: CMake, Git, Linux, ROS2, OpenCV, LaTeX

## Features

### Visual Design
- ✅ **Blue Section Headings** - Professional dark blue (RGB: 0, 102, 204)
- ✅ **Personal Photo** - Top right 3cm ID photo
- ✅ **Clear Layout** - Name left-aligned, contact info in two rows
- ✅ **Icon Enhancement** - Font Awesome icons for contact details

### Content Organization
- ✅ **Education & Honors First** - Highlighted before project experience
- ✅ **Project Links** - Linked to detailed project pages on personal website
- ✅ **Reverse Chronological** - Most recent experiences first

## Build PDF

### Method 1: Using Make (Recommended)

Ensure `make` and a full LaTeX distribution (TeX Live or MiKTeX) are installed:

```bash
cd files/cv_EN
make          # Build cv.pdf
make clean    # Clean intermediate files (.aux, .log, .out etc.)
make distclean # Clean all files including PDF
```

### Method 2: Using latexmk

```bash
cd files/cv_EN
latexmk -pdf cv.tex
```

### Method 3: Manual Compilation

```bash
pdflatex cv.tex
# If bibliography is enabled:
# biber cv
# pdflatex cv.tex
pdflatex cv.tex
```

**Note**:
- Intermediate files (.aux, .log, .bcf, .out, .run.xml, .synctex.gz) are ignored by `.gitignore`
- Commit `cv.tex`, `cv.pdf`, `profile.jpg`, `citations.bib` to the repository

## Online Editing (Optional)

If you don't want to install LaTeX locally:

### Overleaf
1. Visit [Overleaf](https://www.overleaf.com/)
2. Create a new project, upload all files (cv.tex, profile.jpg, citations.bib)
3. Edit online and preview in real time
4. Download the compiled PDF

## Update CV Content

### Modifying Personal Info

Edit the header section in `cv.tex` (around lines 145-152):

```latex
\begin{tabularx}{\linewidth}{@{} X r @{}}
\Huge{Your Name} & \multirow{6}{*}{\includegraphics[width=3cm]{profile.jpg}} \\[3pt]
\normalsize{\textit{Role}} & \\
\normalsize{\textit{University, Major}} & \\[10pt]
\href{mailto:email@example.com}{...} & \\[3pt]
\href{https://yourwebsite.com}{...} \ $|$ \
\href{https://github.com/yourusername}{...} & \\
\end{tabularx}
```

### Modifying Sections

**Summary**:
```latex
\section{Summary}
I am currently...
```

**Education**:
```latex
\section{Education}
\begin{tabularx}{\linewidth}{@{}l X@{}}
2023 - 2027 & Degree at \textbf{University} \\
& College \\
& GPA: xx/xx \\
\end{tabularx}
```

**Projects**:
```latex
\begin{tabularx}{\linewidth}{ @{}l r@{} }
\textbf{Project Name} & \hfill \href{link}{Date} \\[3.75pt]
\multicolumn{2}{@{}X@{}}{Description...}  \\
\end{tabularx}
```

### Changing Photo

1. Name the new photo `profile.jpg` (or update filename in cv.tex)
2. Recommended size: ID photo aspect ratio, width will be auto-adjusted to 3cm
3. Recompile after replacing the file

### Adjusting Colors

To change the blue section headers (around line 81):

```latex
% Change to other colors
\definecolor{sectioncolor}{RGB}{0, 102, 204}  % Current Blue
% \definecolor{sectioncolor}{RGB}{0, 128, 0}  % Green
% \definecolor{sectioncolor}{RGB}{139, 0, 0}  % Dark Red
```

## Website Integration

### Current Configuration

The CV PDF is accessible via:

1. **Sidebar Download Link** - "Download CV" at the bottom of the left sidebar
   - File location: `_includes/author-profile.html`
   - Links to: `/files/cv_EN/cv.pdf`

2. **Direct URL**
   - https://Particlela.github.io/files/cv_EN/cv.pdf

### Update Workflow

After modifying the CV:
1. Edit `cv.tex`
2. Compile new `cv.pdf`: `make`
3. Check PDF content
4. Commit to Git:
   ```bash
   git add cv.tex cv.pdf
   git commit -m "Update CV"
   git push
   ```
5. Wait for GitHub Pages deployment
6. Verify on website

## Technical Details

### LaTeX Dependencies

- `tabularx` - Flexible table layout
- `multirow` - Multi-row cells (for photo)
- `fontawesome5` - Icon fonts
- `xcolor` - Color support
- `titlesec` - Custom section formatting
- `hyperref` - Hyperlinks
- `graphicx` - Image insertion
- `biblatex` - Bibliography management (optional)

### Layout Settings

- Paper: A4
- Font Size: 12pt
- Margins: 0.9 scale via `geometry` package
- Section Headers: Large font, blue, underlined

## Maintainer

**Hengbin Gao**
- Email: Particle_Nebula@outlook.com / 3230105132@zju.edu.cn
- Phone: (+86) 19883109386
- GitHub: [@Particlela](https://github.com/Particlela)
- Website: [Particlela.github.io](https://Particlela.github.io)

---

*Last updated: September 2026*