# Poster Workbench

A minimal browser-based poster editor with editable text, customizable background colors, and PNG export.

I built Poster Workbench to make a small design idea immediately usable: start with a title, adjust the atmosphere with color, and download the result. It keeps the interface simple so the poster remains the focus.

**[Try the live demo](https://sshnox.github.io/poster-workbench/)**

## Features

- Editable poster title and body text.
- Three color pickers for changing the background palette.
- An animated WebGL fluid shader.
- A static, editable gradient fallback when WebGL is unavailable.
- DM Sans typography with system-font fallbacks.
- PNG download with the background included and editor controls excluded.
- Responsive layout and accessible editor labels.
- No build step, backend, accounts, or API keys.

The default title is **“Everything is a plugin”**.

## Getting started

### Open the demo

Visit the [live site](https://sshnox.github.io/poster-workbench/) in a modern browser.

### Run locally

```bash
git clone https://github.com/sshnox/poster-workbench.git
cd poster-workbench
python3 -m http.server 8000
```

Open `http://localhost:8000`. Alternatively, download the repository ZIP, extract it, and double-click `index.html`.

Internet access is needed to load DM Sans from Google Fonts and html2canvas from cdnjs. If the font is unavailable, the app uses a system font. PNG export requires html2canvas to load successfully.

## How to use it

1. Click the title and type your headline.
2. Click the body text to edit the supporting copy.
3. Adjust the three color pickers at the bottom.
4. Click **Download** to save the current composition as a PNG.

Pressing Enter while editing the title finishes title editing rather than inserting a new line. The body text supports multiple lines.

Edits are kept in memory only. Refreshing the page restores the defaults, so download your poster before leaving.

## PNG export

The export captures the current viewport, including the background and poster card, while excluding the color controls, download button, and editing hint.

- Resolution is up to 2× the viewport size.
- The longest exported side is capped at 4096 pixels.
- The PNG is generated in your browser and downloaded through a Blob URL.
- The result is a static image, even when the background is animated.
- Glass blur and some effects can differ from the on-screen view because html2canvas does not fully reproduce backdrop filters.

The output follows your browser's viewport rather than a fixed print size or social-media aspect ratio.

## Tech stack

- HTML, CSS, and plain JavaScript
- WebGL and GLSL for the animated background
- html2canvas 1.4.1 for PNG export
- DM Sans through Google Fonts
- GitHub Pages for static hosting

## Project structure

```text
poster-workbench/
├── index.html            # Editor, shader, fallback, and PNG export
├── README.md
├── RESOURCES.md          # Source and dependency references
├── .nojekyll             # Static GitHub Pages publishing
└── reference/
    └── original.html     # Original HTML from the source conversation
```

## How it works

The title and body are editable HTML elements. Three color inputs feed the shader's color uniforms. Where WebGL is unavailable, the same inputs update a CSS gradient instead.

The shader uses layered value noise to create a slowly changing background. It is an approximation supplied by the original conversation, not a verified copy of DeepSeek's official shader or visual identity.

For export, the app waits for fonts, captures the composition with html2canvas, encodes it as a PNG, and starts a browser download.

## Deployment

GitHub Pages publishes the root of the `main` branch. Changes pushed to `main` are automatically redeployed. The editor is public; the source repository is currently private.

## Privacy and limitations

Poster text and colors are processed in your browser. There is no app backend or upload service. Third-party requests are made to load the font and export library.

The project is a standalone web app. It does not install into DeepSeek Harness or add controls to another application's conversation interface.

Text editing, PNG download, and the gradient fallback were verified during setup. The animated WebGL shader remains unverified in the cloud browser.

## Troubleshooting

- **Download does not work:** check your internet connection, reload, and try again after the export library loads.
- **The background does not animate:** your browser may be using the gradient fallback because WebGL is unavailable.
- **The PNG looks slightly different:** glass blur and some browser effects are not reproduced exactly by html2canvas.

## Author and acknowledgments

Built and maintained by **Shoaib Shah** ([sshnox](https://github.com/sshnox)). I developed this project with AI assistance, starting from [this DeepSeek conversation](https://chat.deepseek.com/share/189c22gt33w1sizvcf), and adapted it into a working browser editor.

html2canvas is provided by its contributors under the MIT license. DM Sans is used under its own font license. See `RESOURCES.md` for the source and dependency links.

## Contributing

Ideas, export improvements, and accessibility fixes are welcome. Open an issue with your browser, viewport size, expected behavior, and what happened. Include an example or screenshot when reporting a visual or export issue.
