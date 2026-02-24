# Tests Directory

This folder contains test files and testing documentation.

## Current Contents

Currently empty (reserved for future use).

## Test Structure (for v0.2+)

When implementing tests, organize by type:

```
tests/
├── unit/
│   ├── score-calculation.test.js
│   ├── sentence-matching.test.js
│   └── timer.test.js
│
├── integration/
│   ├── game-flow.test.js
│   └── score-persistence.test.js
│
├── e2e/
│   ├── complete-game.test.js
│   └── browser-compatibility.test.js
│
└── README.md (this file)
```

## Testing Tools (Suggested for v0.2+)

- **Unit Testing**: Jest or Mocha
- **E2E Testing**: Cypress or Playwright
- **Coverage**: Istanbul/NYC

## Test Categories

### Unit Tests
- Score calculation logic
- Sentence matching algorithm
- Word counting
- Timer countdown

### Integration Tests
- Game flow (start → play → end → save)
- Score persistence
- UI updates

### E2E Tests
- Complete game session
- Cross-browser compatibility
- Mobile responsiveness
- Score history functionality

## Running Tests (Future)

```bash
# Unit tests
npm test

# E2E tests
npm run test:e2e

# Coverage report
npm run test:coverage
```

## Current Testing Approach (v0.1)

For v0.1, manual testing in browser using DevTools:
1. Open browser DevTools (F12)
2. Test game flow manually
3. Check Console for errors
4. Verify localStorage in Storage tab
5. Test across different browsers

See `../docs/DEVELOPMENT.md` for detailed testing guide.
