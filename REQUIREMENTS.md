# Software Requirements Specification (SRS)
## Typing Speed Challenge v0.1

---

## 1. Introduction

### 1.1 Purpose
This document specifies the functional and non-functional requirements for the Typing Speed Challenge application, a web-based typing speed test game.

### 1.2 Scope
The application is designed to be a browser-based tool for users to practice and test their typing speed with real-world sentences. Features include real-time feedback, score tracking, and persistent storage of results.

### 1.3 Document Conventions
- **SHALL**: Mandatory requirement
- **SHOULD**: Recommended requirement
- **MAY**: Optional feature

---

## 2. Overall Description

### 2.1 User Classes and Characteristics
- **Primary Users**: Individuals aged 13+ interested in improving typing speed
- **Skill Levels**: Beginner to Advanced typists
- **Technical Proficiency**: Basic computer literacy required

### 2.2 Operating Environment
- **Platform**: Web browsers (Desktop/Laptop)
- **Browser Support**: Modern browsers (Chrome, Firefox, Safari, Edge)
- **Network**: Requires internet connection for initial load; works offline after caching
- **Storage**: Browser local storage for score persistence

---

## 3. Functional Requirements

### 3.1 Game Session Management

#### FR-1.1: Start Game Session
- **Description**: User shall be able to start a new typing game
- **Preconditions**: Application is loaded, no game in progress
- **Post-conditions**: Timer starts at 60 seconds, first sentence is displayed
- **Steps**:
  1. User clicks "START" button
  2. Button becomes disabled
  3. Input field becomes enabled and focused
  4. Timer begins countdown
  5. Random sentence appears in sentence box

#### FR-1.2: Game Timer
- **Description**: Game shall maintain a 60-second countdown timer
- **Details**:
  - Timer displays in large format at top
  - Timer changes color (orange at 10s, red below 10s)
  - Timer animates/pulses when in danger zone
  - Game ends automatically when timer reaches 0

#### FR-1.3: End Game Session
- **Description**: Game shall automatically end when time expires
- **Post-conditions**:
  - Input field disabled
  - Final score calculated and displayed
  - Score saved to history
  - START button re-enabled for next game

### 3.2 Sentence Management

#### FR-2.1: Display Random Sentence
- **Description**: Application shall display one random sentence at a time
- **Details**:
  - Sentences sourced from predefined list of 30 everyday sentences
  - Sentences are approximately 10-15 words each
  - New sentence appears after correct completion of previous one
  - Sentences can repeat (with replacement)

#### FR-2.2: Sentence Validation
- **Description**: System shall check if typed text matches the displayed sentence
- **Validation Rules**:
  - Case-insensitive matching
  - Must match word-for-word exactly
  - Punctuation must match exactly
  - Whitespace handled automatically

#### FR-2.3: Visual Sentence Feedback
- **Description**: Display visual indication of sentence status
- **States**:
  - Normal: White border, neutral display
  - Correct (on completion): Green border, light green background
  - Sentence auto-advances after 500ms delay

### 3.3 Input and Typing

#### FR-3.1: Text Input Field
- **Description**: User shall type sentences in a text input field
- **Details**:
  - Field disabled until game starts
  - Field focused automatically when game starts
  - Placeholder text guides user
  - Field cleared when sentence is completed correctly

#### FR-3.2: Character Input Validation
- **Description**: System shall validate typed input in real-time
- **Behavior**:
  - Accepts all keyboard input
  - Shows red border if typed words exceed sentence words
  - Shows normal border if typing is within bounds
  - Shows green border when sentence matches exactly

#### FR-3.3: Word Counting
- **Description**: System shall count words as they are typed
- **Logic**:
  - Words separated by spaces
  - Multiple spaces treated as single separator
  - Empty strings filtered out

### 3.4 Statistics and Scoring

#### FR-4.1: Real-Time Statistics Display
- **Description**: Display three key metrics during gameplay
- **Metrics**:
  1. **Words Typed**: Total words from all completed sentences
  2. **Sentences Completed**: Count of perfectly typed sentences
  3. **Progress Status**: Number of sentences completed

#### FR-4.2: Score Calculation
- **Description**: Calculate final score based on completed sentences
- **Formula**: 
  - Final Score = Total Words Completed
  - Represents words per minute equivalent (60 seconds = 1 minute)

#### FR-4.3: Final Score Display
- **Description**: Show final results when game ends
- **Display Elements**:
  - Final WPM Score
  - Number of sentences completed
  - Game over overlay with results

### 3.5 Score History

#### FR-5.1: Score Storage
- **Description**: System shall persist all scores to browser storage
- **Storage Method**: Browser localStorage API
- **Data Format**: JSON array of WPM scores
- **Persistence**: Scores survive browser close/reopen until explicitly cleared

#### FR-5.2: Display Score History
- **Description**: Show all previous scores in a dedicated panel
- **Display Location**: Left sidebar of application
- **Format**: List of scores with WPM values
- **Layout**: Vertical scrollable list with max-height 600px
- **Animation**: New scores slide in smoothly
- **Initial State**: "No scores yet" message when empty

#### FR-5.3: Clear Score History
- **Description**: User can clear all stored scores
- **Behavior**:
  - Triggered by "Clear Scores" button
  - Confirmation dialog appears (prevent accidental deletion)
  - Clears localStorage and resets display
  - Cannot be undone

### 3.6 User Interface

#### FR-6.1: Responsive Layout
- **Description**: Application shall adapt to different screen sizes
- **Breakpoints**:
  - Desktop (>1024px): Side-by-side layout
  - Tablet/Mobile (<1024px): Stacked vertical layout

#### FR-6.2: Visual Feedback
- **Description**: Provide clear visual cues for all states
- **Feedback Types**:
  - Color changes for timer states
  - Border color changes for input validation
  - Button hover effects
  - Animation for score entries

#### FR-6.3: Version Display
- **Description**: Display current application version
- **Location**: Bottom center of game area
- **Format**: "Typing Speed Challenge - vX.X"

---

## 4. Non-Functional Requirements

### 4.1 Performance
- **NFR-1.1**: Application shall load in under 2 seconds
- **NFR-1.2**: Sentence transitions shall be smooth (<500ms)
- **NFR-1.3**: Real-time statistics update with <100ms latency

### 4.2 Usability
- **NFR-2.1**: Learning curve minimal (< 1 minute to understand)
- **NFR-2.2**: Text should be readable (minimum font size 14pt for body text)
- **NFR-2.3**: Color contrast ratio minimum 4.5:1 for accessibility

### 4.3 Reliability
- **NFR-3.1**: Application shall not crash during normal operation
- **NFR-3.2**: Score data shall not be lost during session
- **NFR-3.3**: Timer shall be accurate to within ±100ms

### 4.4 Maintainability
- **NFR-4.1**: Code shall be well-commented
- **NFR-4.2**: Functions shall have single responsibility
- **NFR-4.3**: Variable names shall be descriptive

### 4.5 Security
- **NFR-5.1**: No sensitive data transmitted
- **NFR-5.2**: XSS protection through input sanitization
- **NFR-5.3**: No external API dependencies

### 4.6 Compatibility
- **NFR-6.1**: Support for modern browsers (ES6+)
- **NFR-6.2**: No requirement for backend server
- **NFR-6.3**: Local storage (localStorage API) required

---

## 5. Use Cases

### UC-1: Play Typing Game
**Actor**: User (Typist)
**Preconditions**: Application loaded
**Main Flow**:
1. User clicks START button
2. Timer begins, sentence appears
3. User types the sentence
4. System validates typed text
5. On correct match, next sentence appears
6. Steps 3-5 repeat until time expires
7. System displays final score
8. Score is added to history

**Alternate Flow**: User makes typo
- System shows red border around input
- User corrects and continues
- On correction, border returns to normal

### UC-2: View Score History
**Actor**: User
**Preconditions**: Application loaded
**Main Flow**:
1. User views left panel
2. Previous scores visible as list
3. Most recent score at top

### UC-3: Clear Score History
**Actor**: User
**Preconditions**: Scores exist in history
**Main Flow**:
1. User clicks "Clear Scores" button
2. Confirmation dialog appears
3. User confirms
4. All scores deleted
5. Panel shows "No scores yet" message

---

## 6. Data Requirements

### 6.1 Sentence Database
- **Size**: 30 sentences minimum
- **Format**: Text strings, 10-15 words each
- **Content**: Everyday, conversational English sentences
- **Storage**: Hardcoded in JavaScript array

### 6.2 Score Data
- **Format**: Positive integer (WPM value)
- **Storage**: JSON array in localStorage
- **Key**: 'typingScores'
- **Retention**: Until user clears

---

## 7. Constraints

### 7.1 Technical Constraints
- Must work as single HTML file (no build process)
- No external dependencies allowed (CDNs acceptable)
- Pure HTML/CSS/JavaScript only

### 7.2 Business Constraints
- Free, open-source application
- No monetization or ads
- No user registration or authentication required

### 7.3 Design Constraints
- Mobile-friendly layout
- Accessible(WCAG 2.1 Level AA target)
- Modern, clean aesthetic

---

## 8. Acceptance Criteria

- [x] Game runs for exactly 60 seconds
- [x] Sentences load and cycle correctly
- [x] Score calculation accurately counts complete sentences
- [x] Scores persist in storage across sessions
- [x] UI is responsive and visually appealing
- [x] Timer shows accurate countdown
- [x] Version display shows current version
- [x] All buttons function as intended
- [x] No runtime errors in console
- [x] Works in all major browsers

---

## 9. Version History

| Version | Date       | Changes |
|---------|------------|---------|
| v0.1    | 2026-02-24 | Initial release with core features |

---

**Document Status**: Final for v0.1
**Last Updated**: 2026-02-24
