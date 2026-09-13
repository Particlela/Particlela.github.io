# Hengbin Gao's Academic Website

**Personal academic portfolio website built with Jekyll and GitHub Pages.**

🌐 **Live Site:** [https://Particlela.github.io/](https://Particlela.github.io/)

## About This Site

This is the personal academic website of **Hengbin Gao**, an undergraduate student at the College of Information Science and Electronic Engineering, **Zhejiang University**, majoring in **Information Engineering (2023 - 2027)**. As a member of the RoboMaster electrical control team, his work focuses on the embedded control of series-elastic leg balancing robots and bidirectional four-switch buck-boost (FSBB) buffer-capacitor energy management. The site presents research and engineering projects, competition awards, and a downloadable CV.

## Site Structure

### Active Pages

- **About** (`/`) - Personal introduction and education background at the College of Information Science and Electronic Engineering, Zhejiang University.
- **Project** (`/project/`) - Engineering projects, including:
  - **RoboMaster Series-Elastic Leg Infantry Robot Control System** (STM32H7, variable-gain LQR balancing, priority-based hierarchical state machine, two-stage energy buffer, quadratic-model power limiter).
  - **Series-Elastic Leg Sentry Robot Control System** (autonomous navigation, chassis command interface).
  - **Bidirectional Four-Switch Buck-Boost Buffer Capacitor (FSBB)** (STM32G4, multi-loop PI control with feedforward, real-time ADC/DMA state feedback).
  - **HW-Components: Universal Robot Control Library** (CAN/UART protocol stack, ranging sensors, referee system, supercapacitor link, lever-arm compensation).
- **Award** (`/award/`) - RoboMaster competition awards (Infantry, Sentry, National Championship Top 8) and academic scholarships (2024 - 2026).
- **Research** (`/research/`) - Reserved research archive page.

### Features

- **LaTeX CV**: Full academic CV maintained in `files/cv_CN/` and `files/cv_EN/`.
- **PDF Download**: CV PDFs available from the sidebar.
- **Responsive Design**: Mobile-friendly layout powered by the Minimal Mistakes theme.
- **Clean Navigation**: Focused navigation across About / Project / Award.

## CV Management

### LaTeX Source

The CV is maintained as two LaTeX documents under `files/`:

```
files/
├── cv_CN/
│   ├── cv.tex              # Chinese CV (LaTeX source)
│   ├── cv.pdf              # Compiled Chinese PDF
│   ├── profile.jpg         # Profile photo
│   ├── Makefile            # Compilation script
│   └── README.md           # CV-specific documentation
└── cv_EN/
    ├── cv.tex              # English CV (LaTeX source)
    ├── cv.pdf              # Compiled English PDF
    ├── profile.jpg         # Profile photo
    ├── Makefile            # Compilation script
    └── README.md           # CV-specific documentation
```

### Compiling the CV

```bash
cd files/cv_CN     # or files/cv_EN
make                # Compile PDF
make clean          # Remove intermediate files
make distclean      # Remove all generated files
```

Or manually:
```bash
latexmk -pdf cv.tex
```

### CV Features

- Professional blue section headers
- Integrated profile photo
- Contact information with icons (Email / GitHub / Website)
- Sections: Education, Honors & Awards, Research Experience, Projects, Skills

## Getting Started

### Prerequisites

- Ruby (>= 2.7)
- Bundler
- Node.js (for JavaScript dependencies)

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/Particlela/Particlela.github.io.git
   cd Particlela.github.io
   ```

2. **Install dependencies**
   ```bash
   bundle install
   ```

3. **Run local server**
   ```bash
   bundle exec jekyll serve -l -H localhost
   ```

4. **View site**

   Open browser to `http://localhost:4000`

### Updating Content

#### Edit Personal Information

Edit `_config.yml`:
```yaml
author:
  name: "Hengbin Gao"
  email: "3230105132@zju.edu.cn"
  github: "Particlela"
  employer: "Zhejiang University"
```

#### Update Pages

- **About**: Edit `_pages/about.md`
- **Research**: Edit `_pages/research.md`
- **Projects**: Edit `_pages/project.md`
- **Awards**: Edit `_pages/award.md`

#### Update CV

1. Edit `files/cv_CN/cv.tex` and/or `files/cv_EN/cv.tex`
2. Compile: `cd files/cv_CN && make` (and similarly for `cv_EN`)
3. Commit the updated `cv.pdf` files.

#### Add Images & Videos

Place images in `images/` and videos in `videos/`, then reference them in the relevant page:

```markdown
![Description](/images/your-image.jpg)
<video width="100%" controls>
  <source src="{{ site.url }}{{ site.baseurl }}/videos/your-video.mp4" type="video/mp4">
</video>
```

## Site Configuration

### Navigation Menu

Edit `_data/navigation.yml` to customize the navigation bar. Currently active entries:

```yaml
main:
  - title: "About"
    url: /
  - title: "Project"
    url: /project/
  - title: "Award"
    url: /award/
```

### Sidebar

The sidebar includes:
- Profile photo (`images/Gao.jpg`)
- Name and affiliation
- Location, employer, email, and GitHub links
- **CV Download links** for both Chinese and English versions

Customize in `_includes/author-profile.html`.

## Content Not Currently Used

The following template features are disabled in the navigation but remain on disk:

- **Publications** (`_publications/`) - For academic papers
- **Talks** (`_talks/`) - For presentations and seminars
- **Teaching** (`_teaching/`) - For teaching experience
- **Portfolio** (`_portfolio/`) - For additional projects
- **Blog** (`_posts/`) - For blog posts
- **CV (Markdown / JSON)** (`_pages/cv.md`, `_pages/cv-json.md`, `_data/cv.json`) - PDF CV is preferred.

To enable any of these, uncomment the relevant lines in `_data/navigation.yml`.

## Technical Details

### Built With

- **Jekyll** - Static site generator
- **Minimal Mistakes Theme** - Base theme (customized)
- **GitHub Pages** - Hosting
- **Font Awesome** - Icons
- **LaTeX** - CV typesetting

### File Structure

```
├── _config.yml           # Site configuration
├── _data/
│   ├── navigation.yml    # Navigation menu
│   └── cv.json           # Legacy JSON CV (unused)
├── _includes/
│   └── author-profile.html  # Sidebar customization
├── _pages/               # Main content pages
│   ├── about.md
│   ├── research.md
│   ├── project.md
│   └── award.md
├── files/
│   ├── cv_CN/            # Chinese LaTeX CV
│   └── cv_EN/            # English LaTeX CV
├── images/               # Site images
│   ├── Gao.jpg           # Profile photo
│   ├── Infantry.jpg
│   ├── Sentry.jpg
│   └── buffercap*.png
├── videos/               # Project demo videos
└── README.md             # This file
```

## Deployment

The site automatically deploys to GitHub Pages when you push to the `master` branch:

1. Make your changes locally
2. Test with `bundle exec jekyll serve`
3. Commit and push:
   ```bash
   git add .
   git commit -m "Update content"
   git push origin master
   ```
4. GitHub Actions will build and deploy (usually within 1-2 minutes)
5. Check status at: Settings → Pages

## Maintenance Notes

### Updating CV

After editing the LaTeX CV:
1. Compile new PDF: `cd files/cv_CN && make` (and `cd files/cv_EN && make`)
2. Verify the PDFs look correct
3. Commit both `cv.tex` and `cv.pdf`
4. Push to GitHub

### Adding New Research/Projects

1. Add images to `images/` and videos to `videos/`
2. Edit the corresponding markdown file in `_pages/`
3. Follow the existing format for consistency (separator `***`, centered/responsive media, English-Chinese bilingual style where appropriate)
4. Test locally before pushing

## License

This repository is based on the Academic Pages template, which is © 2016 Michael Rose and released under the MIT License.

Personal content © 2024-2026 Hengbin Gao.

## Contact

- **Email**: 3230105132@zju.edu.cn
- **GitHub**: [@Particlela](https://github.com/Particlela)
- **Website**: [https://Particlela.github.io](https://Particlela.github.io)

---

*Last updated: September 2026*

## Advanced Usage

### Using Docker

For cross-platform development without installing Ruby:

```bash
chmod -R 777 .
docker compose up
```

Access the site at `http://localhost:4000`

### Using VS Code DevContainer

If using Visual Studio Code:

1. Open the repository in VS Code
2. Press F1 → "DevContainer: Reopen in Container"
3. Site automatically available at `http://localhost:4000`

---

## Credits

This site is based on the [Academic Pages](https://github.com/academicpages/academicpages.github.io) template, customized for Hengbin Gao's academic portfolio.