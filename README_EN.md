# HimDocs-Builder

[繁體中文](README.md) | [English](README_EN.md)

# HimDocs-Builder

## Introduction

HimDocs-Builder is a simple yet powerful documentation site generator built using HTML, CSS, and JavaScript. It supports a dynamic sidebar, table of contents (TOC), theme switching (light/dark mode), progress bar, and Markdown content rendering. Users can define the site structure and content by modifying the `pages.json` configuration file, with support for customizing footer copyright information.

### Features
- **Dynamic Sidebar**: Automatically generates a nested menu based on `pages.json`.
- **Routing Support**: Updates the URL hash (e.g., `#page1`) when clicking menu items, supporting browser forward/back navigation.
- **Theme Switching**: Supports light and dark modes with smooth transition effects.
- **Markdown Rendering**: Uses `marked.js` to render `.md` files into HTML.
- **Progress Bar**: Displays the scroll progress of the content area.
- **Footer Animation**: The footer pops up when scrolling past the bottom of the content.
- **Customizability**: Supports custom titles, footer copyright text, and menu icons.

You can preview the latest version of HimDocs-Builder here:  
https://himservice-docs.himserver.com/

(I’m very sorry, but the website currently only has a Chinese README.md. However, you can download the project yourself, and we provide English versions of the files.)

## Installation

### Requirements
- Python 3.9 or higher.

### Steps
1. **Copy Project Files**
   - Place the following files into your project directory:
     - `index.html`: Main page structure.
     - `style.css`: Stylesheet file.
     - `script.js`: Core logic.
     - `pages.json`: Site configuration and page settings.
     - `content/`: Directory for storing Markdown files (e.g., `page1.md`).
     - `server.py`: Server startup and port configuration.
     - `assets/`: You can place your logo here, named as a `.png` file (e.g., `logo.png`).
2. **Set Up Content**
   - Create Markdown files in the `content/` directory, for example:
     ```
     # Welcome Page
     This is my first documentation page.
     ```
     The filename should correspond to the `path` in `pages.json` (e.g., `page1.md`).
3. **Configure Startup Port**
   - Edit `server.py`:
     ```bash
     # Define server port
     PORT = 8000
     ```
     Change `PORT = 8000` to your desired port.
4. **Start the Server**
   - Run the following in the project directory:
     ```bash
     py server.py
     ```
   - The console will display `Server running at http://localhost:8000`.
   - Open `http://localhost:8000` in your browser.

## Usage

### Navigating the Site
- **Homepage**: Open `http://localhost:8000` to load the first page with a `path` defined in `pages.json` by default.
- **Switch Pages**: Click sidebar menu items to update the URL (e.g., `#page2`) and display the corresponding Markdown file in the content area.
- **Theme Switching**: Click the `🌙` (dark mode) or `☀️` (light mode) button in the top-right corner.
- **Search**: Enter keywords in the search bar to filter sidebar menu items.
- **Footer**: Scroll past the bottom of the content to trigger the footer pop-up.

### Example Markdown Content
In `content/page1.md`:
```
# Page One
This is my documentation content.

## Subsection
- Item 1
- Item 2
```

After rendering:
- Headings and lists are displayed correctly.
- Links are rendered as clickable hyperlinks.

## Customization Options

### Customizing `pages.json`
The configuration file is located at `pages.json`, with the following structure:
```json
{
    "title": "My Documentation Site",
    "footerCopyright": "© 2025 My Documentation Site",
    "sidebar": [
        {
            "name": "Project A",
            "path": "page1",
            "icon": "🏠",
            "children": [
                {
                    "name": "Module A-1",
                    "path": "subpage1-1"
                }
            ]
        },
        {
            "name": "Project B",
            "path": "page2",
            "icon": "🚀"
        }
    ],
    "settings": {
        "theme": "light",
        "language": "zh",
        "showIcons": true
    }
}
```
- **`title`**: Site title, displayed in the page title and header.
- **`footerCopyright`**: Footer copyright text (only this part is editable; the suffix is fixed as `| Powered by HimService`).
- **`sidebar`**: Defines the sidebar menu, supporting nested structures.
  - `name`: Menu item name.
  - `path`: Corresponding Markdown filename (without `.md`).
  - `icon`: Optional icon (e.g., an emoji).
  - `children`: Submenu items.
- **`settings`**:
  - `theme`: Default theme (`light` or `dark`).
  - `language`: Language setting (currently only supports `zh`).
  - `showIcons`: Whether to display icons (`true` or `false`).

### Customizing Styles
Edit `style.css`:
- **Theme Colors**: Modify `background` and `color` in `body.dark`.
- **Link Colors**: Adjust `color` in `.content a` and `body.dark .content a`.

## Known Issues

## Development and Contribution

### Reporting Issues
If you encounter a bug or have a feature suggestion, please create an Issue on GitHub with a detailed description and reproduction steps.

## License
Please read the `LICENSE` file.
