# Badge Studio

Badge Studio is a browser-based sticker maker for celebrating any milestone, accomplishment, joke, or delightfully specific life event. It was inspired by a friend who wanted to customize the familiar “I Demoed” style for her wedding, then expanded into a general-purpose design tool.

**Live demo:** https://made-together-sticker.maria648542.chatgpt.site/

## Features

- Generate three sticker concepts with the local **Badge Copilot**
- Choose playful, heartfelt, proud, or chaotic ideas
- Edit curved sticker text with automatic font fitting
- Set separate badge, frame, artwork-circle, and text colors
- Enter colors with a color wheel or hex code
- Toggle the artwork circle on or off
- Upload PNG, JPEG, WebP, or SVG artwork
- Resize uploaded artwork
- Export a 1200 × 1300 PNG or editable SVG
- Keep prompts and uploaded images in the browser

## Local, open-weight AI

Badge Copilot runs [SmolLM2-135M-Instruct](https://huggingface.co/onnx-community/SmolLM2-135M-Instruct-ONNX-MHA) in the browser with [Transformers.js](https://huggingface.co/docs/transformers.js/index). The quantized model is downloaded on first use and cached by the browser.

No inference server, API key, or per-request API is required. A small deterministic fallback keeps the constrained sticker interface useful when the tiny model does not return three valid phrases.

## Pixel-aware layout

Curved text does not occupy a simple rectangle. Badge Studio renders a text-only SVG to an offscreen canvas, scans the painted alpha pixels, and positions the artwork using the real letter shapes. This keeps the visual gap consistent as the phrase and font size change.

## Run locally

This is a static site with no build step. Serve the repository with any local web server, then open dist/index.html through that server.

For example:

```sh
npx serve dist
```

## Project structure

```text
dist/index.html       Complete static application
.openai/hosting.json  Site hosting configuration
```

## Privacy

- Sticker prompts are processed locally in the browser.
- Uploaded artwork is read with FileReader and is not uploaded by the app.
- Exports are generated on the user's device.

## Inspiration

The visual direction was inspired by MLH's [I Demoed Sticker Generator](https://idemoed.tools.mlh.com/). Badge Studio is an independent project and does not include MLH branding.

## License

MIT — see [LICENSE](LICENSE).
