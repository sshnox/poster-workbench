# Poster Workbench

A minimal poster editor adapted from [this DeepSeek conversation](https://chat.deepseek.com/share/189c22gt33w1sizvcf).

Click the title or body to edit. Use the three color pickers to recolor the animated shader background. Click **Download** to save a PNG of the current viewport without editor controls.

The default title is “Everything is a plugin”. DM Sans is loaded from Google Fonts; a system font is used if unavailable. The flowing shader is the approximation supplied in the chat, not a verified copy of DeepSeek’s official shader or branding.

## Run

Open `index.html` in a modern browser, or use the published GitHub Pages site. Internet access is needed for the font and the html2canvas export dependency. No build step is required.

WebGL browsers get an animated background. When WebGL is unavailable, a static gradient remains editable and exportable. Export dimensions follow your viewport at up to 2× scale (longest side capped at 4096 pixels). The glass blur can look different in the exported PNG because html2canvas does not fully reproduce backdrop filters.

## Source

- `index.html`: working app with fallback controls, full-background PNG export, accessible editor labels, and mobile layout fixes.
- `reference/original.html`: unchanged HTML downloaded from the shared chat.
- `RESOURCES.md`: project source and dependencies.

This is a standalone web app. The source conversation did not provide an installable DeepSeek Harness plugin or conversation integration.

Poster text and colors are processed in your browser. There is no app backend or upload service. Refreshing resets edits; download your poster before leaving.
