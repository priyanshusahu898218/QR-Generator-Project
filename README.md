# QR Code Generator

A lightweight **Node.js CLI application** that turns any URL into a scannable QR code image. Enter a link in the terminal, and the app generates a PNG file you can share or print, while also saving the original URL for reference.

[![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](LICENSE)

---

## Features

- **Interactive CLI** — Prompts for a URL using a clean terminal interface
- **Instant QR generation** — Creates a PNG image from any valid URL string
- **URL persistence** — Saves the entered URL to a text file for later use
- **Zero configuration** — No API keys, databases, or external services required
- **Minimal footprint** — Small dependency set, easy to run locally

---

## How It Works

```
┌─────────────────┐     ┌──────────────┐     ┌─────────────────┐
│  Terminal input │ ──► │  qr-image    │ ──► │  qr_img.png     │
│  (your URL)     │     │  (encode)    │     │  (QR code PNG)  │
└─────────────────┘     └──────────────┘     └─────────────────┘
         │
         └──────────────────────────────────► URL.txt (saved URL)
```

1. You run the app and type a URL when prompted.
2. The URL is encoded into a QR code using the `qr-image` library.
3. The QR code is written to `qr_img.png`.
4. The same URL is saved to `URL.txt`.

---

## Tech Stack

| Technology | Purpose |
|------------|---------|
| [Node.js](https://nodejs.org/) | Runtime environment |
| [Inquirer](https://www.npmjs.com/package/inquirer) | Interactive terminal prompts |
| [qr-image](https://www.npmjs.com/package/qr-image) | QR code image generation |
| [fs](https://nodejs.org/api/fs.html) (native) | File read/write operations |

---

## Prerequisites

- **Node.js** v18 or higher ([download](https://nodejs.org/))
- **npm** (included with Node.js)

Verify your installation:

```bash
node --version
npm --version
```

---

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/priyanshusahu898218/QR-Generator-Project.git
   cd QR-Generator-Project
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

---

## Usage

Start the application from the project root:

```bash
node index.js
```

When prompted, enter the URL you want to encode:

```
? Type in your URL:  https://github.com/priyanshusahu898218/QR-Generator-Project
The file has been saved!
```

### Output Files

| File | Description |
|------|-------------|
| `qr_img.png` | Scannable QR code image for the URL you entered |
| `URL.txt` | Plain-text copy of the saved URL |

Open `qr_img.png` with any image viewer, or scan it with your phone's camera to visit the link.

---

## Project Structure

```
QR-Generator-Project/
├── index.js          # Main application entry point
├── package.json      # Project metadata and dependencies
├── package-lock.json # Locked dependency versions
├── URL.txt           # Last saved URL (generated at runtime)
├── qr_img.png        # Last generated QR code (generated at runtime)
└── README.md         # Project documentation
```

---

## Dependencies

```json
{
  "inquirer": "^14.0.2",
  "qr-image": "^3.2.0"
}
```

- **inquirer** — Handles user input in the terminal with validation and formatting.
- **qr-image** — Converts strings (URLs) into QR code image streams (PNG format).

> **Note:** The project also lists `fs` and `nodemon` in `package.json`. File I/O uses Node's built-in `fs` module; `nodemon` is optional for development auto-restart.

---

## Development

To auto-restart the app when you edit files during development:

```bash
npx nodemon index.js
```

---

## Example

**Input**

```
https://youtube.com
```

**Result**

- `qr_img.png` — QR code that opens YouTube when scanned
- `URL.txt` — Contains `https://youtube.com`

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| `Cannot find module 'inquirer'` | Run `npm install` in the project directory |
| Prompt does not appear | Run in a supported terminal (not all CI/non-TTY environments support Inquirer) |
| QR code does not scan | Ensure the URL is valid and the PNG file finished writing before opening it |

---

## Roadmap

Possible future enhancements:

- [ ] Validate URL format before generating the QR code
- [ ] Support custom output filename and image size
- [ ] Add a `--url` flag for non-interactive usage
- [ ] Export QR codes as SVG in addition to PNG

---

## License

This project is licensed under the **ISC License**.

---

## Author

**Priyanshu Sahu**

- GitHub: [@priyanshusahu898218](https://github.com/priyanshusahu898218)
- Repository: [QR-Generator-Project](https://github.com/priyanshusahu898218/QR-Generator-Project)

---

## Acknowledgments

Built as a hands-on Node.js exercise covering npm packages, the native `fs` module, and CLI-driven workflows.
