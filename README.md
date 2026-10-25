import os, zipfile, textwrap

base = "/mnt/data/ivoid_github_profile"
assets = os.path.join(base, "assets")
workflow = os.path.join(base, ".github", "workflows")
os.makedirs(assets, exist_ok=True)
os.makedirs(workflow, exist_ok=True)

header_svg = r'''<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="340" viewBox="0 0 1200 340" role="img" aria-labelledby="title desc">
<title id="title">IVOID — animated developer banner</title>
<desc id="desc">A dark futuristic banner with animated violet particles, glowing lines, and the IVOID wordmark.</desc>
<defs>
  <linearGradient id="bg" x1="0" y1="0" x2="1" y2="1">
    <stop offset="0" stop-color="#050508"/><stop offset=".55" stop-color="#130b24"/><stop offset="1" stop-color="#251044"/>
  </linearGradient>
  <linearGradient id="neon" x1="0" y1="0" x2="1" y2="0">
    <stop offset="0" stop-color="#6d28d9"/><stop offset=".5" stop-color="#c4b5fd"/><stop offset="1" stop-color="#7c3aed"/>
  </linearGradient>
  <radialGradient id="glow">
    <stop offset="0" stop-color="#8b5cf6" stop-opacity=".34"/><stop offset="1" stop-color="#8b5cf6" stop-opacity="0"/>
  </radialGradient>
  <filter id="blur"><feGaussianBlur stdDeviation="18"/></filter>
  <filter id="softGlow"><feGaussianBlur stdDeviation="3" result="b"/><feMerge><feMergeNode in="b"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
  <pattern id="grid" width="38" height="38" patternUnits="userSpaceOnUse">
    <path d="M38 0H0V38" fill="none" stroke="#a78bfa" stroke-opacity=".08" stroke-width="1"/>
  </pattern>
  <clipPath id="clip"><rect width="1200" height="340" rx="18"/></clipPath>
</defs>
<g clip-path="url(#clip)">
  <rect width="1200" height="340" fill="url(#bg)"/>
  <rect width="1200" height="340" fill="url(#grid)"/>
  <ellipse cx="840" cy="150" rx="360" ry="230" fill="url(#glow)" filter="url(#blur)">
    <animate attributeName="rx" values="300;390;300" dur="9s" repeatCount="indefinite"/>
    <animate attributeName="opacity" values=".55;1;.55" dur="7s" repeatCount="indefinite"/>
  </ellipse>
  <g fill="none" stroke="url(#neon)" stroke-width="1.5" opacity=".65">
    <path d="M-80 265 L320 265 L390 195 L700 195" stroke-dasharray="8 12">
      <animate attributeName="stroke-dashoffset" from="0" to="-200" dur="12s" repeatCount="indefinite"/>
    </path>
    <path d="M790 60 L920 60 L985 125 L1270 125" stroke-dasharray="4 10">
      <animate attributeName="stroke-dashoffset" from="0" to="180" dur="10s" repeatCount="indefinite"/>
    </path>
    <path d="M900 300 L1030 170 L1240 170" stroke-dasharray="2 9">
      <animate attributeName="stroke-dashoffset" from="0" to="-120" dur="8s" repeatCount="indefinite"/>
    </path>
  </g>
  <g fill="#c4b5fd">
    <circle cx="110" cy="75" r="2"><animate attributeName="opacity" values=".15;1;.15" dur="3s" repeatCount="indefinite"/></circle>
    <circle cx="275" cy="220" r="1.7"><animate attributeName="opacity" values="1;.2;1" dur="4s" repeatCount="indefinite"/></circle>
    <circle cx="460" cy="90" r="2"><animate attributeName="opacity" values=".2;1;.2" dur="2.6s" repeatCount="indefinite"/></circle>
    <circle cx="730" cy="275" r="2"><animate attributeName="opacity" values="1;.2;1" dur="3.7s" repeatCount="indefinite"/></circle>
    <circle cx="1050" cy="70" r="2"><animate attributeName="opacity" values=".2;1;.2" dur="3.2s" repeatCount="indefinite"/></circle>
    <circle cx="1120" cy="240" r="1.5"><animate attributeName="opacity" values="1;.2;1" dur="2.8s" repeatCount="indefinite"/></circle>
  </g>
  <g transform="translate(82 0)">
    <text x="0" y="151" font-family="monospace" font-size="15" letter-spacing="6" fill="#a78bfa">INDEPENDENT DEVELOPER</text>
    <text x="-2" y="224" font-family="monospace" font-size="78" font-weight="700" letter-spacing="5" fill="#8b5cf6" opacity=".45" filter="url(#softGlow)">IVOID</text>
    <text x="0" y="220" font-family="monospace" font-size="78" font-weight="700" letter-spacing="5" fill="#f5f3ff">IVOID</text>
    <rect x="2" y="240" width="220" height="2" rx="1" fill="url(#neon)">
      <animate attributeName="width" values="35;220;175;220" dur="5s" repeatCount="indefinite"/>
    </rect>
    <text x="2" y="272" font-family="monospace" font-size="15" fill="#d4d4d8">SYSTEMS  /  GAME DEV  /  3D</text>
  </g>
  <g transform="translate(855 205)" opacity=".9">
    <rect x="0" y="0" width="250" height="68" rx="8" fill="#08070d" fill-opacity=".82" stroke="#6d28d9" stroke-opacity=".8"/>
    <circle cx="16" cy="15" r="3" fill="#8b5cf6"/><circle cx="27" cy="15" r="3" fill="#a78bfa" opacity=".65"/><circle cx="38" cy="15" r="3" fill="#c4b5fd" opacity=".4"/>
    <text x="15" y="40" font-family="monospace" font-size="12" fill="#a78bfa">$ build --release</text>
    <text x="15" y="56" font-family="monospace" font-size="11" fill="#71717a">optimizing ideas...</text>
    <rect x="157" y="47" width="7" height="11" fill="#c4b5fd">
      <animate attributeName="opacity" values="1;0;1" dur="1s" repeatCount="indefinite"/>
    </rect>
  </g>
  <rect x="1" y="1" width="1198" height="338" rx="18" fill="none" stroke="#8b5cf6" stroke-opacity=".35"/>
</g>
</svg>'''

footer_svg = r'''<svg xmlns="http://www.w3.org/2000/svg" width="1200" height="140" viewBox="0 0 1200 140" role="img" aria-labelledby="title">
<title id="title">IVOID animated footer</title>
<defs>
 <linearGradient id="line" x1="0" y1="0" x2="1" y2="0"><stop stop-color="#09090b"/><stop offset=".5" stop-color="#a78bfa"/><stop offset="1" stop-color="#09090b"/></linearGradient>
 <linearGradient id="bg" x1="0" y1="0" x2="1" y2="0"><stop stop-color="#050508"/><stop offset=".5" stop-color="#170d2d"/><stop offset="1" stop-color="#050508"/></linearGradient>
</defs>
<rect width="1200" height="140" rx="16" fill="url(#bg)"/>
<path d="M0 28 H1200" stroke="url(#line)" stroke-width="2">
 <animate attributeName="opacity" values=".3;1;.3" dur="4s" repeatCount="indefinite"/>
</path>
<g fill="#a78bfa">
 <circle cx="160" cy="68" r="2"><animate attributeName="cy" values="68;53;68" dur="3s" repeatCount="indefinite"/></circle>
 <circle cx="1030" cy="83" r="2"><animate attributeName="cy" values="83;96;83" dur="4s" repeatCount="indefinite"/></circle>
 <circle cx="910" cy="55" r="1.5"><animate attributeName="opacity" values=".2;1;.2" dur="2s" repeatCount="indefinite"/></circle>
</g>
<text x="600" y="77" font-family="monospace" font-size="18" letter-spacing="5" fill="#f5f3ff" text-anchor="middle">MAKE IT WORK. MAKE IT CLEAN. MAKE IT YOURS.</text>
<text x="600" y="105" font-family="monospace" font-size="11" letter-spacing="3" fill="#a78bfa" text-anchor="middle">IVOID  //  ENGINEERED WITH INTENT</text>
</svg>'''

typing_svg = r'''<svg xmlns="http://www.w3.org/2000/svg" width="900" height="90" viewBox="0 0 900 90" role="img" aria-labelledby="title">
<title id="title">Animated IVOID developer tagline</title>
<rect width="900" height="90" fill="transparent"/>
<g font-family="monospace" font-size="22" fill="#c4b5fd">
  <text x="450" y="48" text-anchor="middle" opacity="0">SYSTEMS PROGRAMMING
    <animate attributeName="opacity" values="0;1;1;0;0" keyTimes="0;.08;.32;.4;1" dur="12s" repeatCount="indefinite"/>
  </text>
  <text x="450" y="48" text-anchor="middle" opacity="0">BUILDING WITH RUST &amp; C++
    <animate attributeName="opacity" values="0;0;1;1;0;0" keyTimes="0;.25;.33;.57;.65;1" dur="12s" repeatCount="indefinite"/>
  </text>
  <text x="450" y="48" text-anchor="middle" opacity="0">CREATING WORLDS IN UNREAL ENGINE
    <animate attributeName="opacity" values="0;0;1;1;0;0" keyTimes="0;.5;.58;.82;.9;1" dur="12s" repeatCount="indefinite"/>
  </text>
  <text x="450" y="48" text-anchor="middle" opacity="0">MODELING · RIGGING · ANIMATION
    <animate attributeName="opacity" values="0;0;1;1;0" keyTimes="0;.75;.83;.96;1" dur="12s" repeatCount="indefinite"/>
  </text>
</g>
<path d="M220 68 H680" stroke="#6d28d9" stroke-opacity=".6">
 <animate attributeName="stroke-dasharray" values="0 460;460 0;0 460" dur="5s" repeatCount="indefinite"/>
</path>
</svg>'''

readme = r'''<!--
  IVOID — Animated GitHub Profile
  1. Replace EVERY YOUR_USERNAME with your exact GitHub username.
  2. Put this README.md in the public repository named exactly YOUR_USERNAME.
  3. Keep the assets/ folder and .github/workflows/snake.yml in the same repository.
-->

<div align="center">

<img src="assets/header.svg" width="100%" alt="IVOID animated neon developer banner"/>

<img src="assets/typing.svg" width="100%" alt="Systems programming, Rust and C++, Unreal Engine, and 3D animation"/>

<a href="https://github.com/YOUR_USERNAME">
  <img src="https://komarev.com/ghpvc/?username=YOUR_USERNAME&style=for-the-badge&color=6d28d9&label=PROFILE+VIEWS" alt="Profile views"/>
</a>
<a href="https://github.com/YOUR_USERNAME?tab=repositories">
  <img src="https://img.shields.io/badge/REPOSITORIES-EXPLORE-6d28d9?style=for-the-badge&logo=github&logoColor=white" alt="Explore repositories"/>
</a>

</div>

---

<div align="center">

## `01 — IDENTITY`

**Independent Developer · Systems Programming · Game Development · 3D Art**

*I build software, explore performance, and create interactive worlds.*

</div>

```text
┌──────────────────────────────────────────────────────────────┐
│  HANDLE       IVOID                                          │
│  CORE         Rust · C · C++ · Python · Zig · C# · Lua       │
│  GAME DEV     Unreal Engine · Unity · Godot                  │
│  3D PIPELINE  Blender · Modeling · Rigging · Animation       │
│  WORKSPACE    Linux · Git · Open Source                      │
└──────────────────────────────────────────────────────────────┘
```

## `02 — TECH STACK`

<div align="center">

**LANGUAGES**

<img src="https://skillicons.dev/icons?i=rust,c,cpp,cs,python,zig,lua&theme=dark&perline=7" alt="Rust, C, C++, C sharp, Python, Zig and Lua"/>

**GAME DEVELOPMENT & 3D**

<img src="https://skillicons.dev/icons?i=unreal,blender,unity,godot&theme=dark&perline=4" alt="Unreal Engine, Blender, Unity and Godot"/>

**TOOLS & ENVIRONMENT**

<img src="https://skillicons.dev/icons?i=linux,git,github,cmake,sqlite,vscode,visualstudio&theme=dark&perline=7" alt="Linux, Git, GitHub, CMake, SQLite and development tools"/>

</div>

## `03 — CURRENTLY BUILDING`

<table>
<tr>
<td width="50%" valign="top">

### `01 / SYSTEMS`

Exploring Rust and C/C++ with a focus on performance, software architecture, and understanding what happens under the hood.

</td>
<td width="50%" valign="top">

### `02 / GAME DEV`

Developing game systems and immersive experiences with Unreal Engine, C++, and custom 3D assets.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### `03 / 3D PIPELINE`

Creating models, materials, rigs, and animations in Blender for real-time projects.

</td>
<td width="50%" valign="top">

### `04 / LINUX`

Building a focused development environment and exploring open-source tools and workflows.

</td>
</tr>
</table>

## `04 — GITHUB TELEMETRY`

<div align="center">

<a href="https://github.com/YOUR_USERNAME">
  <img height="170" src="https://github-readme-stats.vercel.app/api?username=YOUR_USERNAME&show_icons=true&hide_border=true&bg_color=09090b&title_color=a78bfa&icon_color=8b5cf6&text_color=e4e4e7&rank_icon=github" alt="GitHub stats"/>
</a>
<a href="https://github.com/YOUR_USERNAME">
  <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_USERNAME&layout=compact&hide_border=true&bg_color=09090b&title_color=a78bfa&text_color=e4e4e7&langs_count=8" alt="Most used languages"/>
</a>

<br/><br/>

<img width="94%" src="https://github-readme-streak-stats.herokuapp.com/?user=YOUR_USERNAME&hide_border=true&background=09090b&stroke=6d28d9&ring=a78bfa&fire=8b5cf6&currStreakLabel=a78bfa&sideLabels=e4e4e7&currStreakNum=ffffff&sideNums=ffffff&dates=71717a" alt="GitHub contribution streak"/>

<br/><br/>

<img width="98%" src="https://github-readme-activity-graph.vercel.app/graph?username=YOUR_USERNAME&bg_color=09090b&color=c4b5fd&line=7c3aed&point=e9d5ff&area=true&hide_border=true&custom_title=CONTRIBUTION%20ACTIVITY" alt="GitHub contribution activity graph"/>

</div>

> **Note:** Stats cards are served by external projects and may occasionally be unavailable or cached. Language percentages describe detected repository code, not skill level.

## `05 — CONTRIBUTION SNAKE`

<div align="center">

<!-- Generated automatically by .github/workflows/snake.yml after you enable GitHub Actions. -->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-contribution-grid-snake-dark.svg"/>
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-contribution-grid-snake.svg"/>
  <img alt="Animated snake moving through the GitHub contribution grid" src="https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_USERNAME/output/github-contribution-grid-snake.svg" width="100%"/>
</picture>

</div>

## `06 — PROJECT ARCHIVE`

<div align="center">

<!-- Pinned repo cards: replace REPO_ONE / REPO_TWO with actual repository names. -->
<a href="https://github.com/YOUR_USERNAME/REPO_ONE">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=YOUR_USERNAME&repo=REPO_ONE&hide_border=true&bg_color=09090b&title_color=a78bfa&text_color=e4e4e7&icon_color=8b5cf6" alt="Featured project one"/>
</a>
<a href="https://github.com/YOUR_USERNAME/REPO_TWO">
  <img src="https://github-readme-stats.vercel.app/api/pin/?username=YOUR_USERNAME&repo=REPO_TWO&hide_border=true&bg_color=09090b&title_color=a78bfa&text_color=e4e4e7&icon_color=8b5cf6" alt="Featured project two"/>
</a>

</div>

### Visual work

<div align="center">

<!-- Your original screenshots are retained. Replace or reorder them as you like. -->
<img src="https://i.ibb.co/Q7SmNzNR/Capture-d-cran-20261025-024004.png" width="92%" alt="Main project showcase"/>

<br/><br/>

<img src="https://i.ibb.co/YK6DNfX/Capture-d-cran-20261025-022606.png" width="44%" alt="Project preview one"/>
<img src="https://i.ibb.co/4R9VNfTm/ada.png" width="44%" alt="Project preview two"/>

<br/><br/>

<img src="https://i.ibb.co/XkWWB2Zd/q.png" width="44%" alt="Project preview three"/>
<img src="https://i.ibb.co/HLyNhDY1/image.png" width="44%" alt="Project preview four"/>

<br/><br/>

<img src="https://i.ibb.co/JwNbgJPY/d.png" width="70%" alt="Project preview five"/>

</div>

## `07 — FIND ME`

<div align="center">

<!-- Replace each platform homepage with your own profile URL. -->
<a href="https://www.youtube.com/">
  <img src="https://img.shields.io/badge/YOUTUBE-111111?style=for-the-badge&logo=youtube&logoColor=ff0033" alt="YouTube"/>
</a>
<a href="https://www.instagram.com/">
  <img src="https://img.shields.io/badge/INSTAGRAM-111111?style=for-the-badge&logo=instagram&logoColor=e4405f" alt="Instagram"/>
</a>
<a href="https://discord.com/">
  <img src="https://img.shields.io/badge/DISCORD-111111?style=for-the-badge&logo=discord&logoColor=7289da" alt="Discord"/>
</a>
<a href="https://itch.io/">
  <img src="https://img.shields.io/badge/ITCH.IO-111111?style=for-the-badge&logo=itchdotio&logoColor=fa5c5c" alt="itch.io"/>
</a>

<br/><br/>

<img src="assets/footer.svg" width="100%" alt="IVOID animated footer"/>

<sub>IVOID · Code with intent. Create with purpose.</sub>

</div>
'''
workflow_yml = r'''name: Generate contribution snake

on:
  schedule:
    - cron: "17 */12 * * *"
  workflow_dispatch:
  push:
    branches:
      - main

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    steps:
      - name: Generate snake SVGs
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
      - name: Publish SVGs to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
'''

with open(os.path.join(base, "README.md"), "w", encoding="utf-8") as f:
    f.write(readme)
with open(os.path.join(assets, "header.svg"), "w", encoding="utf-8") as f:
    f.write(header_svg)
with open(os.path.join(assets, "typing.svg"), "w", encoding="utf-8") as f:
    f.write(typing_svg)
with open(os.path.join(assets, "footer.svg"), "w", encoding="utf-8") as f:
    f.write(footer_svg)
with open(os.path.join(workflow, "snake.yml"), "w", encoding="utf-8") as f:
    f.write(workflow_yml)

guide = """IVOID GitHub profile kit
========================

Files:
- README.md: profile layout
- assets/header.svg: self-contained animated neon header (SVG SMIL)
- assets/typing.svg: rotating animated taglines (SVG SMIL)
- assets/footer.svg: animated footer (SVG SMIL)
- .github/workflows/snake.yml: GitHub Actions workflow to generate the contribution snake

Setup:
1. Create or use a PUBLIC repository named exactly like your GitHub username.
2. Upload README.md, assets/, and .github/ from this kit to the repository root.
3. In README.md, replace every YOUR_USERNAME with your exact GitHub username.
4. Replace REPO_ONE and REPO_TWO with real repository names, or remove those two project cards.
5. Change the social links to your real profile URLs.
6. Open the repository Settings > Actions > General and ensure Actions are allowed. Run the
   "Generate contribution snake" workflow from the Actions tab once. It publishes the SVGs
   to an output branch. If your default branch isn't main, edit the workflow's push branch.
7. Check that all screenshot URLs still work. Those images were retained from the original snippet.

Animation note:
The header, taglines, and footer use SVG animation primitives and are stored in your repository,
so they don't depend on an external animation service. GitHub's README renderer doesn't run
arbitrary JavaScript, so interactive JS effects aren't available directly inside README content.
The stats cards and skill icons still use external services and may be cached or temporarily down.
"""
with open(os.path.join(base, "SETUP.txt"), "w", encoding="utf-8") as f:
    f.write(guide)

zip_path = "/mnt/data/ivoid_github_profile_animated_kit.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as z:
    for root, dirs, files in os.walk(base):
        for name in files:
            full = os.path.join(root, name)
            z.write(full, os.path.relpath(full, base))

print("Created:", zip_path)
print("Included README.md, animated SVG assets, contribution-snake workflow, and setup guide.")
