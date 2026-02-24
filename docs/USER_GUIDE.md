# User Guide
## Typing Speed Challenge v0.1

---

## Table of Contents
1. [Getting Started](#getting-started)
2. [How to Play](#how-to-play)
3. [Understanding Your Stats](#understanding-your-stats)
4. [Tips & Tricks](#tips--tricks)
5. [Troubleshooting](#troubleshooting)
6. [FAQ](#faq)

---

## Getting Started

### System Requirements
- **Computer**: Desktop or Laptop (Mobile browser may be challenging due to typing)
- **Browser**: Any modern web browser:
  - Google Chrome (recommended)
  - Mozilla Firefox
  - Safari
  - Microsoft Edge
  - Opera
- **JavaS** cript: Must be enabled
- **Storage**: Browser must support localStorage

### Loading the Application
1. Navigate to the `index.html` file
2. Open it in your web browser (double-click or right-click → Open with → Browser)
3. The application loads instantly (no installation needed)
4. Page displays with purple gradient background

### First Time Setup
- The application works immediately with no setup
- Your first game will show "No scores yet" in the left panel
- Start playing by clicking the green "START" button

---

## How to Play

### Step 1: Start a Game
```
1. Click the green "START" button at the bottom
2. The button becomes grayed out (disabled)
3. Timer starts at 60 seconds and begins counting down
4. Your cursor is automatically focused in the typing input field
5. A random sentence appears in the display box
```

**Visual Cues**:
- START button turns gray → Game has begun
- Input field shows focus (blue border) → Ready to type
- Timer shows "60" → Full minute remaining

### Step 2: Type the Sentence
```
1. Read the sentence displayed in the white box
2. Type the exact same sentence in the input field below it
3. Typing is CASE-INSENSITIVE (capitals don't matter)
4. You must include all punctuation and spacing
```

**Example**:
- Displayed: `"The quick brown fox jumps over the lazy dog."`
- You can type: `"the quick brown fox jumps over the lazy dog."` ✅
- You cannot type: `"the quick brown fox jumps over the lazy dog"` ❌ (missing period)

### Step 3: Visual Feedback While Typing
As you type, the input field shows your progress:

| State | Border Color | Background | Meaning |
|-------|-------------|-----------|---------|
| Normal | Gray | White | Typing in progress |
| Good | Green | Light Green | Sentence matches! |
| Error | Red | Light Red | Too many words typed |

### Step 4: Complete the Sentence
When you type the sentence correctly:
```
1. Input field turns GREEN
2. System confirms the match (0.5 second delay)
3. Input field automatically clears
4. Next random sentence appears
5. Continue typing the next sentence
```

### Step 5: Race Against Time
- Keep typing sentences for the full 60 seconds
- The timer counts down in the center
- Watch for color changes:
  - Blue: 60-21 seconds remaining (normal pace)
  - Orange: 20-11 seconds remaining (hurry up!)
  - Red + Pulsing: 10 seconds or less (FINAL SPRINT!)

### Step 6: Game Ends
When time expires:
```
1. Timer reaches "0"
2. Input field disables (stops accepting input)
3. Red box appears with your results:
   - Final Score (Words Typed)
   - Sentences Completed
4. START button re-enables for next game
5. Your score is automatically saved to the left panel
```

---

## Understanding Your Stats

### Real-Time Statistics (During Game)

The game displays three live metrics while you play:

#### 1. Words Typed
```
Shows: Total words from all completed sentences
Example: If you completed 3 sentences (10 words + 9 words + 8 words)
         = 27 Words Typed displayed
Updates: Each time you complete a sentence
```

#### 2. Sentences Completed
```
Shows: Number of sentences successfully typed
Example: If you perfectly typed "The quick brown..." and "I need to buy..."
         = 2 sentences completed
Updates: Instantly when you finish a sentence
Resets: When you start a new game
```

#### 3. Progress Status
```
Shows: "X Done" format
Example: Displays "3 Done" after completing 3 sentences
Purpose: Quick visual reference of how many sentences finished
```

### Final Score Display

When time expires, you see:

#### Final Score
- **Name**: Displayed as "Final Score: XXX WPM"
- **Meaning**: Words per minute equivalent
- **Calculation**: Total words completed in 60 seconds
- **Example**: 75 WPM = Typed 75 words worth of sentences in 60 seconds
- **Performance Scale**:
  - 0-30 WPM: Just starting
  - 30-60 WPM: Beginner level
  - 60-80 WPM: Good average
  - 80-100 WPM: Above average
  - 100+ WPM: Expert typist

#### Continued Score Display
- Shows detailed breakdown (Sentences: X)
- Your score is added to the history panel automatically

---

## Score History Panel (Left Side)

### What It Shows
- A scrollable list of all your scores from every game session
- Most recent scores appear at the top
- Scores in purple boxes with white text
- Each box shows the WPM value

### Score Persistence
- **Automatically Saved**: Each score saves when a game ends
- **Survives Close**: Scores remain even if you close the browser
- **Stored Locally**: Data stored on your computer only
- **Survives Reload**: If you refresh the page, scores remain

### Example History
```
📊 Scores

85 WPM    ← Most recent game
72 WPM    ← Previous game
93 WPM    ← Game before that
...
```

### Clear Scores
```
To delete all scores:
1. Click "Clear Scores" button (blue, right of START button)
2. Confirmation dialog appears asking "Are you sure?"
3. Click "OK" to confirm deletion
4. All scores erased, panel shows "No scores yet"
⚠️ WARNING: This cannot be undone!
```

---

## Tips & Tricks

### Improving Your Typing Speed

#### 1. **Accuracy First, Speed Second**
- The system only counts *complete, correct* sentences
- One mistake means the sentence doesn't count
- Focus on accuracy; speed will follow naturally

#### 2. **Know Common Phrases**
- Many sentences use everyday English
- Recognizing patterns helps you type faster
- Practice builds muscle memory

#### 3. **Keep Eyes on Screen**
- Read ahead while your fingers finish typing
- Minimize the gap between reading and typing
- Practice "touch typing" (not looking at keyboard)

#### 4. **Punctuation Matters**
- Periods, commas, apostrophes must match exactly
- Don't skip punctuation to save time
- Include all spaces as shown

#### 5. **Warm Up First**
- Play a practice round before competing
- Your first game is often slower (familiarity effect)
- Successive games usually show improvement

#### 6. **Maintain Good Posture**
- Sit up straight with arms at 90 degrees
- Wrists should be neutral (not bent)
- Feet flat on ground
- Monitor at eye level

#### 7. **Practice Regularly**
- 5-10 minutes daily improves speed
- Weekly tracking shows trends
- Compare scores across sessions

### Quick Controls During Game
```
Keyboard:
- [Spacebar] - Continue typing (normal word separator)
- [Backspace] - Delete character
- [Tab] - Disable (don't use to navigate input)

Mouse:
- [Click input field] - Bring focus back if lost
- [Clear input] - Click the input and Ctrl+A then Delete
```

---

## Troubleshooting

### Issue: "Input field won't work"
**Diagnosis**: 
- Input disabled until you click START
- Browser may need focus on the page

**Solution**:
1. Click the green START button
2. Wait 1 second for button to disable
3. Input field should now accept typing
4. If not, click directly inside the input field

---

### Issue: "My score seems too low"
**Diagnosis**:
- Only completed (perfectly typed) sentences count
- Incomplete or incorrect sentences don't contribute

**Solution**:
1. Check stats during game - verify sentences completed
2. Read sentence completely before typing
3. Match punctuation exactly
4. Example: Missing one comma = sentence doesn't count

---

### Issue: "Timer stopped/doesn't update"
**Diagnosis**:
- Browser refresh issue
- JavaScript error

**Solution**:
1. Refresh the page (F5 or Ctrl+R)
2. Try in a different browser
3. Disable browser extensions (they can interfere)

---

### Issue: "Scores disappeared after closing browser"
**Diagnosis**:
- localStorage might be disabled
- Browser in private/incognito mode
- Storage limit exceeded (unlikely)

**Solution**:
1. Check if browser supports localStorage:
   - Chrome, Firefox, Safari, Edge: ✅ Supported
2. Turn off private/incognito mode
3. Check browser storage settings aren't blocking it

---

### Issue: "Can't clear scores"
**Diagnosis**:
- Confirmation dialog not appearing
- Browser clipboard blocked

**Solution**:
1. Refresh page and try again
2. Disable browser extensions temporarily
3. Try in a different browser

---

### Issue: "Application won't load"
**Diagnosis**:
- Browser doesn't support HTML5
- JavaScript disabled
- Corrupted file

**Solution**:
1. Use modern browser (Chrome, Firefox, Edge recommended)
2. Enable JavaScript in browser settings:
   - Chrome: Settings → Privacy & Security → JavaScript
   - Firefox: about:config → javascript.enabled = true
3. Re-download the file if corrupted

---

## FAQ

### Q: Can I use this on my phone?
**A**: Technically yes, but it's designed for desktop/laptop keyboards. Mobile touch keyboards are much slower and harder to use for typing tests.

---

### Q: What happens if I close the browser mid-game?
**A**: Your game ends immediately and is not counted. Only completed games save scores.

---

### Q: Can I modify the sentences?
**A**: In the current version (v0.1), sentences are hardcoded. Future versions may allow custom sentence imports.

---

### Q: Is my data shared or tracked?
**A**: No. All scores are stored locally on your computer only. The application doesn't connect to any server or collect personal data.

---

### Q: Can I play offline?
**A**: Yes! After the first load, the page is cached by your browser and works completely offline.

---

### Q: Why is my score in "words" and not "WPM"?
**A**: Since the game is exactly 60 seconds, the total words typed equals WPM (words per 60 seconds = 1 minute).

---

### Q: How are words counted?
**A**: Words are separated by spaces. Extra spaces are collapsed into a single separator. Empty strings don't count.

---

### Q: Can I undo a score deletion?
**A**: Unfortunately, no. The "Clear Scores" action is permanent. Be careful when clicking that button!

---

### Q: What's the highest score possible?
**A**: Theoretically unlimited! There's no cap. If you completed 100+ word sentences perfectly, your score could be 400+ WPM.

---

### Q: Why do I see version "v0.1"?
**A**: This indicates the release version. v0.1 is the first stable release. Future updates will be v0.2, v0.3, etc.

---

### Q: Is this game available on app stores?
**A**: Not currently. This is a web-only application for now.

---

### Q: Can I practice specific topics?
**A**: Not in v0.1. Sentences are random and general. Future versions may include difficulty levels or categories.

---

## Support & Feedback

For questions, suggestions, or issues not covered here:
1. Review the [Architecture](ARCHITECTURE.md) document (for technical details)
2. Check [Requirements](REQUIREMENTS.md) (for feature specifications)
3. Review source code comments in `index.html`

---

**Last Updated**: 2026-02-24  
**Version**: v0.1  
**Document Type**: User Manual
