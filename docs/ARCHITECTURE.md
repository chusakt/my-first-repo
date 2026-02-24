# Software Architecture & Design Document
## Typing Speed Challenge v0.1

---

## 1. Architecture Overview

### 1.1 System Architecture Pattern
**Pattern**: Single-Page Application (SPA) with Client-Side State Management

**Architecture Diagram**:
```
┌─────────────────────────────────────┐
│      HTML Structure/UI Layer        │
│  (Semantic HTML with containers)    │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│    CSS Styling & Animations Layer   │
│  (Flexbox, Grid, Gradients)         │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│   JavaScript Logic Layer            │
│  - Game State Management            │
│  - Event Handling                   │
│  - Score Calculation                │
│  - DOM Manipulation                 │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│    Browser APIs                     │
│  - localStorage (Persistence)       │
│  - DOM API (UI Updates)             │
│  - setInterval/setTimeout (Timing)  │
└─────────────────────────────────────┘
```

### 1.2 Technology Stack
| Layer       | Technology      |
|-------------|-----------------|
| Frontend    | HTML5           |
| Styling     | CSS3            |
| Logic       | JavaScript (ES6)|
| Storage     | localStorage    |
| Deployment  | Static HTML     |

---

## 2. Component Design

### 2.1 UI Components

#### Score Panel Component
```
Location: Left sidebar
Responsibility: Display persistent score history
Children:
  - Header: "📊 Scores"
  - Score List: Scrollable container with score items
  - Empty State: Placeholder message
```

#### Game Area Component
```
Location: Main content area
Sections:
  1. Title: "⚡ Typing Speed Challenge"
  2. Timer Display: Large countdown (3.5rem)
  3. Sentence Box: Current sentence display
  4. Input Field: User typing input
  5. Statistics Panel: Words/Sentences/Progress
  6. Game Over Box: Results display (hidden until game ends)
  7. Button Group: START and Clear Scores buttons
  8. Version Info: Bottom center version display
```

### 2.2 State Management

#### Global Variables
```javascript
// Game State
let timeLeft = 60                    // Remaining seconds
let gameActive = false               // Is game running
let timerInterval = null             // Timer reference

// Sentence State
let currentSentence = ''             // Current sentence to type

// Score State
let scores = []                      // Array of all WPM scores (from localStorage)
let completedSentences = 0           // Count of completed sentences in current game
let totalWordsCompleted = 0          // Total words from completed sentences

// UI References
const elements = {                   // Cache of DOM elements
  timer, sentence, input, startBtn,
  wordCount, correctCount, accuracy,
  scoreList, gameOverBox, finalScore,
  finalAccuracy
}
```

#### State Transitions
```
Initial State: IDLE
    ↓ (user clicks START)
PLAYING: Timer running, input enabled
    ↓ (user completes sentences while timer > 0)
PLAYING: Update scores continuously
    ↓ (timer reaches 0)
GAME_OVER: Display results, save score
    ↓ (user clicks START again)
PLAYING: Reset and restart
```

---

## 3. Core Functions & Responsibilities

### 3.1 Game Initialization & Control

#### `startGame()`
**Responsibility**: Initialize new game session
```
Steps:
1. Set gameActive = true
2. Reset timeLeft = 60
3. Reset completedSentences = 0
4. Reset totalWordsCompleted = 0
5. Disable START button
6. Enable input field
7. Load random sentence
8. Clear input field
9. Start timer interval
```

#### `endGame()`
**Responsibility**: Finalize game and save results
```
Steps:
1. Set gameActive = false
2. Stop timer
3. Calculate final WPM = totalWordsCompleted
4. Save score to scores array
5. Persist to localStorage
6. Update score display
7. Show game-over box with results
8. Re-enable START button
```

#### `updateTimer()`
**Responsibility**: Decrement timer every 100ms
```
Steps:
1. Decrease timeLeft by 0.1
2. Update display
3. Check if timeLeft <= 0
4. Call endGame() if expired
```

### 3.2 Sentence Management

#### `getRandomSentence()`
**Responsibility**: Select random sentence from pool
```
Implementation:
- Use Math.random() to get index
- Return sentence from array
- Allows duplicates (with replacement)
```

#### `currentSentence` validation in input listener
**Responsibility**: Check if typed text matches sentence
```
Steps:
1. Sanitize input (split by spaces, filter empty)
2. Compare word count
3. Case-insensitive word comparison
4. On perfect match:
   - Increment completedSentences
   - Add word count to totalWordsCompleted
   - Show green feedback
   - Schedule sentence advance (500ms)
```

### 3.3 Score Management

#### `displayScores()`
**Responsibility**: Render score history in panel
```
Steps:
1. Check if scores array empty
2. If empty: Show placeholder message
3. If populated: Create HTML list of scores
4. Inject into DOM
```

#### `resetScores()`
**Responsibility**: Clear score history with confirmation
```
Steps:
1. Show confirmation dialog
2. If confirmed:
   - Clear scores array
   - Delete localStorage key
   - Call displayScores() to update UI
```

### 3.4 UI Updates

#### `updateDisplay()`
**Responsible**: Update statistics display
```
Updates:
- wordCount: totalWordsCompleted
- correctCount: completedSentences  
- accuracy: "X Done" format
```

#### `updateTimerDisplay()`
**Responsible**: Update timer and styling
```
Steps:
1. Calculate displayTime = ceil(timeLeft)
2. Update timer text
3. Apply color styling:
   - ≤10 seconds: Red + pulse animation
   - ≤20 seconds: Orange
   - >20 seconds: Blue
```

---

## 4. Data Flow

### 4.1 Game Flow Sequence Diagram
```
User Action      System Response      State Change
─────────────    ─────────────────    ────────────
Click START  →   startGame()    →    gameActive=true
             →   Reset vars    →    Counters=0
             →   Load sentence →    Display random sentence
             →   Start timer   →    Timer counts down

Type text    →   Input listener→    Check validation
             →   Match check   →    
                 (No) Keep typing
                 (Yes) sentence++
                       words += count
             
             →   Display update →   UI updates stats
Timer ends   →   endGame()     →    gameActive=false
             →   Calculate WPM →    scores.unshift(wpm)
             →   Save to store →    localStorage update
             →   Show results  →    Display final score
```

### 4.2 Data Storage Flow
```
Scores Array (In Memory)
    ↓ (User completes game)
scores.unshift(newWPM)
    ↓ (Convert to JSON)
JSON.stringify(scores)
    ↓ (Save to browser)
localStorage.setItem('typingScores', jsonString)
    ↓ (On next load)
JSON.parse(localStorage.getItem('typingScores'))
    ↓ (Populate scores array)
    ↓ (Display in panel)
displayScores()
```

---

## 5. File Structure

```
Single File Application:
index.html (549 lines total)
├── HTML Structure (lines 1-385)
│   ├── Head
│   │   ├── Meta tags
│   │   └── Embedded CSS (lines 5-285)
│   │       ├── Root styles
│   │       ├── Layout (flexbox/grid)
│   │       ├── Component styles
│   │       ├── Animations
│   │       └── Media queries
│   └── Body
│       ├── Score Panel (div .score-panel)
│       ├── Game Area (div .game-area)
│       │   ├── Title
│       │   ├── Timer
│       │   ├── Sentence Box
│       │   ├── Input Field
│       │   ├── Statistics
│       │   ├── Game Over Box
│       │   ├── Buttons
│       │   └── Version Info
│       └── Embedded JavaScript (lines 363-549)
│           ├── Data (Sentence array, Variables)
│           ├── DOM Cache (elements object)
│           ├── Game Logic Functions
│           ├── UI Update Functions
│           └── Event Listeners
```

---

## 6. Design Patterns Used

### 6.1 Module Pattern
All code within single `<script>` block with encapsulated state (global scope minimized with `const/let`).

### 6.2 Event Delegation
Input listener delegates validation logic for real-time feedback.

### 6.3 State Management Pattern
Centralized state variables track game progress and update UI accordingly.

### 6.4 Singleton Pattern
Single instance of game, timer, and score manager.

---

## 7. Styling Architecture

### 7.1 CSS Layout
- **Primary Layout**: CSS Flexbox for main container
- **Grid System**: CSS Grid for statistics boxes and buttons
- **Responsive**: Media queries at 1024px breakpoint

### 7.2 Color Scheme
```
Primary: #667eea (Purple-blue)
Secondary: #764ba2 (Purple)
Success: #48bb78 (Green)
Warning: #f6ad55 (Orange)
Error: #f56565 (Red)
Neutral: #f7fafc (Light gray)
Text: #2d3748 (Dark gray)
Disabled: #cbd5e0 (Gray)
```

### 7.3 Typography
```
Font Family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif
Monospace: 'Courier New' (for input/timer)

Sizes:
- H1: 2.5rem (Title)
- Timer: 3.5rem
- Buttons: 1rem
- Labels: 0.9rem
- Body: 1rem
```

### 7.4 Animations
- **Slide In**: Score entries (0.3s ease-out)
- **Pulse**: Timer in danger zone (0.5s infinite)
- **Hover**: Button shift up (0.2s)

---

## 8. Performance Considerations

### 8.1 Optimization Strategies
1. **DOM Caching**: Elements stored in object to avoid repeated queries
2. **Event Delegation**: Single listener instead of multiple
3. **Debounced Updates**: Stats update on input, not per keystroke
4. **Efficient Selectors**: Direct ID queries (fastest)

### 8.2 Critical Rendering Path
```
HTML Parse → CSS Parse → DOM+CSSOM → Layout → Paint → Composite
(Single file minimizes: HTTP requests, redirects, DNS lookups)
```

---

## 9. Security Considerations

### 9.1 Input Validation
- No direct DOM manipulation from user input
- Text comparison done via string methods (no eval)
- localStorage data is JSON-safe

### 9.2 XSS Prevention
- No `innerHTML` used with user data
- Text content set via `textContent` (safe)
- JSON parse/stringify validated

### 9.3 Data Protection
- Local storage only (no remote transmission)
- No sensitive personal data collected
- Scores are anonymous (no user identification)

---

## 10. Extensibility Points

For future versions, these areas can be extended:

1. **Sentence Management**: Replace hardcoded array with API call
2. **Difficulty Levels**: Add sentence filtering based on complexity
3. **User Profiles**: Add localStorage-based user data
4. **Analytics**: Track additional metrics (WPM history, trends)
5. **Themes**: Add CSS variable system for theme switching
6. **Internationalization**: Support multiple languages

---

## 11. Testing Considerations

### 11.1 Unit Test Areas
- Score calculation logic
- Sentence matching algorithm
- Timer countdown logic
- Statistics updates

### 11.2 Integration Test Areas
- Game flow complete cycle
- Score persistence and retrieval
- UI updates across all states

### 11.3 Performance Test Areas
- Page load time
- Memory usage over extended play
- DOM update frequency

---

**Document Status**: Final for v0.1  
**Architecture Reviewed**: 2026-02-24
**Complexity Level**: Low to Medium (Single-page, no backend)
