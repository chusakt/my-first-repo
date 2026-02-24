# Project Configuration

This file provides configuration guidelines for the Typing Speed Challenge project.

## Current Configuration (v0.1)

No external configuration required - pure HTML/CSS/JavaScript implementation.

## Browser Settings

**Recommended**: Modern browsers (2020+)
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

**Minimum**: Any browser with ES6+ support

## Development Configuration

### VS Code Settings (Optional)

Create `.vscode/settings.json`:
```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[css]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

### Recommended Extensions

- Live Server (5 Stars Registry)
- Prettier - Code formatter
- ES7+ React/Redux/React-Native snippets
- WallabyJS (optional, for testing)

## localStorage Configuration

### Available Space
- Chrome: 10MB
- Firefox: 10MB
- Safari: 5MB
- Edge: 10MB

### Current Usage (v0.1)
- Approximate: 2-5KB per 100 scores
- Storage key: `'typingScores'`
- Format: JSON array of WPM values

### Quota Management
For users who play frequently:
- ~500 scores = ~50KB usage
- Well within limits for modern browsers

To clear storage manually:
```javascript
localStorage.removeItem('typingScores')
// OR
localStorage.clear()
```

## Environment Variables (Future)

For v0.2+, if needed:
```env
# .env file
REACT_APP_API_URL=https://api.example.com
REACT_APP_VERSION=0.2.0
REACT_APP_ENV=production
```

## Performance Configuration

### Recommended Settings

- **Font Loading**: System fonts (no external CDN)
- **Image Optimization**: Keep <1MB total
- **Bundle Size**: Keep source <50KB
- **Memory Usage**: Target <10MB runtime

## Deployment Configuration

### Hosting Providers

1. **GitHub Pages** (Recommended for v0.1)
   - Free hosting
   - Auto-deploy on push
   - URL: `username.github.io/typegame`

2. **Netlify**
   - Free tier
   - CLI deployment
   - URL: `your-site.netlify.app`

3. **Vercel**
   - Free tier
   - Git integration
   - URL: `your-site.vercel.app`

### Environment-Specific Config

```javascript
// Get environment (future use)
const isDevelopment = window.location.hostname === 'localhost'
const isProduction = !isDevelopment

if (isDevelopment) {
  console.log('Development mode')
}
```

## Version Management

Current version: **v0.1**

Versioning locations:
- `src/index.html` - Version display
- `docs/CHANGELOG.md` - Version history
- Git tags: `v0.1`, `v0.2`, etc.

### Update Process for New Version

1. Update src/index.html version
2. Update CHANGELOG.md
3. Commit: "Release v0.X"
4. Create Git tag: `git tag v0.X`
5. Deploy to production

---

**Last Updated**: 2026-02-24  
**Version**: v0.1 configuration
