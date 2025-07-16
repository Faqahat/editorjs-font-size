# Editor.js Font Size Plugin

[![](https://data.jsdelivr.com/v1/package/npm/editorjs-font-size/badge)](https://www.jsdelivr.com/package/npm/editorjs-font-size)

A versatile inline tool for [Editor.js](https://editorjs.io/) that allows you to apply custom font sizes to your content.

![Plugin Demo](https://shottr-uploads.s3.amazonaws.com/548/FQPy-SCR-20250716-nns.png?X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIASHY5OHU5UIVLCXXR%2F20250716%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250716T111908Z&X-Amz-SignedHeaders=host&X-Amz-Expires=600&X-Amz-Signature=8c8af772ccd9251f19f114bc2a2e0e9557c2fb26895dfc5c9eeca9a719bc9b4f)

**[Live Demo](https://faqahat.github.io/editorjs-font-size/)**

## Features

- **Font Size Selection**: Apply different font sizes from a configurable dropdown.
- **Custom Font Sizes**: Define your own font size options with custom labels.
- **Visual Feedback**: Current font size is highlighted in the dropdown.
- **Keyboard Shortcut**: Access the tool quickly with `CMD+SHIFT+F`.
- **Single File**: CSS is embedded in the JavaScript bundle for easy deployment.
- **Clean UI**: A modern and intuitive font size selector interface.

## Installation

### Install via npm

Get the package from npm and import it into your project.

```bash
npm install editorjs-font-size
```

### Load from CDN

You can also load the bundled script from the jsDelivr CDN.

```html
<script src="https://cdn.jsdelivr.net/npm/editorjs-font-size@latest/dist/bundle.js"></script>
```

## Usage

If you installed via npm, import the tool class into your project:

```javascript
import FontSizeTool from "editorjs-font-size";
```

Then, add the tool to your Editor.js instance's configuration:

```javascript
const editor = new EditorJS({
  holder: "editorjs",
  tools: {
    fontSize: {
      class: FontSizeTool,
      inlineToolbar: true, // Set to true to display in the inline toolbar
    },
    // ... other tools
  },
});
```

If you are loading the script from the CDN, the `FontSizeTool` class will be available on the `window` object.

## Configuration

You can customize the font size options by passing a `config` object.

```javascript
const editor = new EditorJS({
  // ... other configurations
  tools: {
    fontSize: {
      class: FontSizeTool,
      config: {
        fontSizes: [
          { size: "12px", label: "Small" },
          { size: "14px", label: "Normal" },
          { size: "16px", label: "Medium" },
          { size: "18px", label: "Large" },
          { size: "20px", label: "Extra Large" },
          { size: "24px", label: "XXL" },
          { size: "28px", label: "XXXL" },
          { size: "32px", label: "Huge" },
        ],
        defaultSize: "14px",
      },
    },
  },
});
```

- `fontSizes`: An array of objects, where each object has a `size` (CSS font-size value) and a `label` (display name).
- `defaultSize`: The default font size to use when none is specified.

If no config is provided, the plugin will use its default font size options.

## Output Data

The plugin saves the font-sized text within a `<span>` tag with the `font-size-tool` class and inline styles.

Example output for a paragraph block:

```json
{
  "type": "paragraph",
  "data": {
    "text": "This is some <span class=\"font-size-tool\" style=\"font-size: 18px;\">large text</span> with normal text."
  }
}
```
