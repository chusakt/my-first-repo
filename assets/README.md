# Assets Directory

This folder contains static assets for the project.

## Current Contents

Currently empty (reserved for future use).

## Planned Assets

- **images/** - Screenshots, logos, icons
- **sounds/** - Audio effects (if added in future versions)
- **fonts/** - Custom fonts (if needed)
- **data/** - Sentence databases or other static data files

## Usage Examples

```html
<!-- Images -->
<img src="../assets/images/logo.png" alt="Logo">

<!-- Fonts -->
@font-face {
  font-family: 'CustomFont';
  src: url('../assets/fonts/custom.woff2');
}

<!-- Sounds -->
new Audio('../assets/sounds/complete.mp3').play()
```

## Size Considerations

Keep assets optimized:
- Images: <1MB each (prefer WebP or optimized PNG)
- Sounds: <500KB each (prefer MP3 with good compression)
- Fonts: <500KB each (prefer WOFF2 format)

This keeps project lightweight and performant.
