# Source Code Directory

This folder contains the main application source code.

## Files

- **index.html** - Main application file (HTML + CSS + JavaScript combined)
  - Single-page application (SPA)
  - No build process required
  - Works in all modern browsers

## Running the Application

### Method 1: Direct File
- Double-click `index.html` to open in default browser

### Method 2: VS Code Live Server
- Right-click `index.html`
- Select "Open with Live Server"
- Auto-refreshes on save

### Method 3: Local HTTP Server
```bash
python -m http.server 8000
# Then visit http://localhost:8000
```

## Development Notes

The application is a pure HTML/CSS/JavaScript implementation with no external dependencies.

- **HTML**: Semantic structure, accessibility-focused
- **CSS**: Modern layout (Flexbox, Grid), responsive design
- **JavaScript**: ES6+, vanilla implementation, no frameworks

For detailed development information, see `../docs/DEVELOPMENT.md`
