# BlackJack Dealer Experience - PowerPoint Presentation Outline
## CSC 4370/6370 Web Programming - Fall 2025

**Team Name:** CSS Dealers (Web Tech Gaming Division)  
**Presenters:** Carter Tierney & Adnan  
**Duration:** 10-15 minutes

---

## 📊 SLIDE STRUCTURE

### SLIDE 1: Title Slide
**Speaker: CARTER**

**Slide Content:**
```
BlackJack Dealer Experience
Pure CSS Animation & Interactivity

Team: CSS Dealers
Carter Tierney - Lead Developer & Presenter
Adnan - QA Tester & Presenter

CSC 4370/6370 Web Programming
Fall 2025
```

**Speaker Notes:**
"Good morning/afternoon everyone. I'm Carter Tierney, and this is Adnan. We're the CSS Dealers, and today we're presenting our BlackJack Dealer Experience - a fully animated, interactive casino table built with HTML and CSS only."

---

## 🎯 SECTION 1: USER / PROBLEM STATEMENT

### SLIDE 2: Problem Statement
**Speaker: ADNAN**

**Slide Content:**
```
THE CHALLENGE

Problem:
Create an interactive, animated card dealing experience
WITHOUT using JavaScript

Constraints:
✗ No JavaScript logic
✗ No external libraries
✗ No frameworks
✓ Pure HTML & CSS only

Goal:
Simulate authentic casino blackjack dealing with:
• Realistic card animations
• 3D visual effects
• Interactive hover responses
• Theme customization
```

**Speaker Notes:**
"The core challenge was to create interactivity and animations without JavaScript. Everything you'll see - the card dealing, 3D effects, hover interactions - is achieved purely through CSS transforms, transitions, and keyframe animations."

---

### SLIDE 3: User Requirements
**Speaker: ADNAN**

**Slide Content:**
```
USER REQUIREMENTS

INPUTS:
• User navigation (Enter Casino button)
• Mouse hover interactions on cards
• Mouse hover on chips
• Theme selection clicks

OUTPUTS:
• Animated card shuffle in dealer shoe
• Sequential card dealing (8 cards total)
• 3D card perspective effects
• Interactive hover "peek" on player cards
• Glowing chip animations
• Dynamic theme color changes

USER EXPERIENCE:
• Smooth, fluid animations
• Responsive across all devices
• Accessible (reduced motion support)
• Intuitive interactions
```

**Speaker Notes:**
"From a user perspective, they interact through hovering and clicking. The system responds with animated feedback - cards deal automatically, hovering reveals card perspectives, and themes change instantly. All outputs are visual animations driven by CSS."

---

## 🎨 SECTION 2: DESIGN & SOLUTION

### SLIDE 4: Solution Overview
**Speaker: CARTER**

**Slide Content:**
```
SOLUTION ARCHITECTURE

Two-Page Structure:
1. index.html - Introduction & team info
2. blackjack.html - Interactive dealer table

Technology Stack:
• Semantic HTML5
• Pure CSS3 (no preprocessors)
• CSS Custom Properties (Variables)
• Flexbox responsive layout

Core CSS Techniques:
✓ Transforms (translate, rotate, scale)
✓ Transitions (smooth hover effects)
✓ @keyframes Animations (card dealing)
✓ 3D Perspective
✓ CSS Variables (theming)
```

**Speaker Notes:**
"Our solution uses a clean two-page structure. The technical architecture relies heavily on CSS3 features - transforms for movement, transitions for smooth interactions, and keyframes for complex sequences."

---

### SLIDE 5: Key Design Features
**Speaker: CARTER**

**Slide Content:**
```
KEY DESIGN FEATURES

1. DEALER SHOE & DECK
   • Positioned absolutely on table
   • Continuous shuffle animation
   • Multi-layered cards for depth

2. CARD DEALING SYSTEM
   • 15+ unique @keyframe animations
   • Staggered timing (0.3s intervals)
   • Path: Shoe → Dealer → Players

3. 3D PERSPECTIVE
   • perspective: 1000px on container
   • transform-style: preserve-3d on cards
   • Multi-axis rotations (X, Y, Z)

4. INTERACTIVE ELEMENTS
   • Hover peek: Cards lift & tilt
   • Chip glow: Scale + animated shadow
   • Theme switcher: CSS variable updates
```

**Visual on Slide:**
[Include screenshot of blackjack table with arrows pointing to these features]

**Speaker Notes:**
"Let me break down the four key design features. The dealer shoe contains a shuffling deck, cards deal in sequence with precise timing, 3D perspective makes everything pop, and all interactive elements respond smoothly to user input."

---

### SLIDE 6: User Interface Design
**Speaker: ADNAN**

**Slide Content:**
```
USER INTERFACE

Layout Components:
┌─────────────────────────────────┐
│     Navigation & Theme Bar      │
├─────────────────────────────────┤
│  [Deck]      DEALER              │
│              ♠A  ♠K              │
│                                  │
│                                  │
│    PLAYER 1    PLAYER 2    P3   │
│     🃏🃏       🃏🃏        🃏🃏     │
│      💰         💰          💰    │
│                                  │
│  [Chip Bank: 💰💰💰💰💰]        │
└─────────────────────────────────┘

Color Palette:
• Gold (#FFD700) - Highlights
• Green Felt (#0D5E2A) - Table
• Dark (#0F1419) - Background
• High Contrast - Accessibility
```

**Visual on Slide:**
[Include actual screenshot or mockup of table layout]

**Speaker Notes:**
"The UI follows classic casino table design - dealer at top, players at bottom, chip bank on the right. We use a gold and green casino color scheme with high contrast for readability. The layout is fully responsive."

---

### SLIDE 7: CSS Transforms - Pseudo Code
**Speaker: CARTER**

**Slide Content:**
```css
/* TRANSFORM TECHNIQUES */

/* 1. CARD TRANSLATION (Movement) */
.card {
    /* Move card from shoe to player position */
    transform: translate(200px, 150px);
    /* Translate moves without affecting document flow */
}

/* 2. CARD ROTATION (3D Effect) */
.card {
    /* Rotate on multiple axes for realism */
    transform: rotateY(-5deg)    /* Horizontal tilt */
              rotateX(2deg)      /* Vertical tilt */
              rotateZ(3deg);     /* Z-axis rotation */
}

/* 3. CHIP SCALING (Size Change) */
.chip:hover {
    /* Grow chip on hover */
    transform: scale(1.2);
    /* 1.2 = 120% of original size */
}

/* 4. COMBINED TRANSFORMS */
.player-cards .card:hover {
    /* Lift + Tilt + Rotate */
    transform: translateY(-30px)    /* Lift up */
              rotateY(-10deg)       /* Tilt left */
              rotateX(5deg)         /* Tilt back */
              rotateZ(-2deg);       /* Slight rotation */
}
```

**Speaker Notes:**
"Here's the pseudo code for our transforms. Translate moves cards across the table, rotate creates 3D angles, scale changes size, and we can combine all three for complex effects like the hover peek."

---

### SLIDE 8: CSS Transitions - Pseudo Code
**Speaker: CARTER**

**Slide Content:**
```css
/* TRANSITION TECHNIQUES */

/* 1. SMOOTH HOVER EFFECTS */
.card {
    /* Default state */
    transform: translateY(0);
    /* Define transition parameters */
    transition: transform 0.3s ease-out,
                box-shadow 0.3s ease-out;
    /*          property  duration timing-function */
}

.card:hover {
    /* Hover state - transition automatically animates */
    transform: translateY(-30px);
    box-shadow: 0 10px 30px rgba(0,0,0,0.5);
}

/* 2. CHIP GLOW TRANSITION */
.chip {
    transition: all 0.4s ease;
    /*          ↑ animates ALL properties */
}

.chip:hover {
    transform: scale(1.15);
    box-shadow: 0 0 20px #ffd700,
                0 0 40px #ffd700;
}

/* 3. THEME CHANGE TRANSITIONS */
.table {
    background: var(--felt-color);
    transition: background 0.5s ease-in-out;
    /* Smoothly animates color changes */
}
```

**Speaker Notes:**
"Transitions handle smooth changes between states. We define the duration and easing function. When hover states change or themes switch, the transition automatically animates between the values."

---

### SLIDE 9: CSS Animations - Pseudo Code
**Speaker: CARTER**

**Slide Content:**
```css
/* ANIMATION (@KEYFRAMES) TECHNIQUES */

/* 1. DEFINE ANIMATION SEQUENCE */
@keyframes dealToPlayer1Card1 {
    0% {  /* Starting point */
        left: 15%;
        top: 45%;
        opacity: 0;
        transform: rotateZ(0deg);
    }
    50% { /* Midpoint */
        opacity: 1;
    }
    100% { /* End point */
        left: 20%;
        top: 70%;
        opacity: 1;
        transform: rotateZ(2deg);
    }
}

/* 2. APPLY ANIMATION TO ELEMENT */
.player1-card-1 {
    animation: dealToPlayer1Card1    /* Name */
               1.5s                   /* Duration */
               ease-out               /* Timing function */
               0.6s                   /* Delay */
               both;                  /* Fill mode */
}

/* 3. CONTINUOUS SHUFFLE ANIMATION */
@keyframes deckShuffle {
    0%, 100% { 
        transform: scale(1) rotate(0deg); 
    }
    50% { 
        transform: scale(1.05) rotate(3deg); 
    }
}

.deck {
    animation: deckShuffle 2s ease-in-out infinite;
    /*                                     ↑ loops forever */
}
```

**Speaker Notes:**
"Keyframe animations define multi-step sequences. We created 15+ unique dealing animations - each card has its own path from the shoe to its final position. The shuffle animation loops infinitely."

---

### SLIDE 10: 3D Perspective Implementation
**Speaker: ADNAN**

**Slide Content:**
```css
/* 3D PERSPECTIVE SYSTEM */

/* STEP 1: Set perspective on parent container */
.table-container {
    perspective: 1000px;
    /* Lower values = more dramatic 3D effect */
    /* 1000px = moderate realistic depth */
}

/* STEP 2: Preserve 3D space for children */
.card {
    transform-style: preserve-3d;
    /* Allows child elements to exist in 3D space */
}

/* STEP 3: Apply 3D transforms */
.card {
    transform: rotateY(-5deg)     /* Horizontal rotation */
              rotateX(2deg)       /* Vertical rotation */
              translateZ(20px);   /* Depth */
}

/* HOVER PEEK - Enhanced 3D */
.player-cards .card:hover {
    transform: translateY(-30px)   /* Lift up */
              translateZ(50px)     /* Move toward viewer */
              rotateY(-10deg)      /* Tilt horizontally */
              rotateX(5deg)        /* Tilt vertically */
              rotateZ(-2deg);      /* Slight rotation */
    z-index: 10;                   /* Appear above others */
}
```

**Visual on Slide:**
[Diagram showing perspective: viewer → 1000px → table with cards in 3D space]

**Speaker Notes:**
"The 3D system works in three steps: set perspective on the container, preserve 3D space on children, then apply multi-axis transforms. This creates realistic depth where cards appear to exist in three-dimensional space."

---

### SLIDE 11: CSS Variables for Theming
**Speaker: CARTER**

**Slide Content:**
```css
/* THEME SYSTEM USING CSS VARIABLES */

/* 1. DEFINE DEFAULT THEME */
:root {
    --felt-color: #0d5e2a;      /* Green felt */
    --chip-red: #dc143c;
    --chip-blue: #1e90ff;
    --chip-black: #2c2c2c;
    --table-border: #8b6914;    /* Gold border */
}

/* 2. USE VARIABLES THROUGHOUT STYLESHEET */
.table {
    background: radial-gradient(
        ellipse at center,
        var(--felt-color),
        color-mix(in srgb, var(--felt-color) 70%, black)
    );
    border: 15px solid var(--table-border);
}

.chip-red {
    background: var(--chip-red);
}

/* 3. THEME SWITCHING (inline style on HTML) */
/* Classic Green - default values above */

/* Royal Blue Theme */
<style>
:root {
    --felt-color: #1a365d;
    --table-border: #4a5568;
}
</style>

/* Ruby Red Theme */
<style>
:root {
    --felt-color: #7f1d1d;
    --table-border: #991b1b;
}
</style>
```

**Speaker Notes:**
"CSS variables enable instant theme switching. We define colors once at :root, reference them throughout the stylesheet, and update them via inline styles when users click theme buttons. The entire page re-renders with new colors instantly."

---

## 🧪 SECTION 3: TESTING

### SLIDE 12: Testing Methodology
**Speaker: ADNAN**

**Slide Content:**
```
TESTING APPROACH

Test Lead: Adnan

1. BROWSER COMPATIBILITY TESTING
   Browsers Tested:
   ✅ Chrome 120+ (Windows, Mac)
   ✅ Firefox 121+
   ✅ Safari 17+ (Mac, iOS)
   ✅ Edge 120+

2. DEVICE TESTING
   ✅ Desktop: 1920x1080, 1366x768
   ✅ Tablet: 768x1024, 1024x768
   ✅ Mobile: 375x667, 414x896, 390x844

3. FEATURE VERIFICATION
   ✅ All 8 cards deal in correct sequence
   ✅ Hover effects work on all elements
   ✅ Theme switcher changes colors
   ✅ Animations play smoothly (60fps)
   ✅ Responsive layouts adapt properly
   ✅ Accessibility features function

4. PERFORMANCE TESTING
   ✅ Animation frame rates
   ✅ Page load times
   ✅ Repaint/reflow optimization
```

**Speaker Notes:**
"I led comprehensive testing across four major browsers and multiple device sizes. We verified every feature works consistently, animations run smoothly at 60fps, and the responsive design adapts properly on all screen sizes."

---

### SLIDE 13: Test Plan & Data
**Speaker: ADNAN**

**Slide Content:**
```
DETAILED TEST PLAN

Test Case 1: Card Dealing Sequence
├─ Expected: 8 cards deal in order with 0.3s intervals
├─ Test Data: Visual observation, timing measurements
├─ Result: ✅ PASS (all browsers)
└─ Issues: None

Test Case 2: 3D Hover Peek
├─ Expected: Cards lift 30px, rotate on multiple axes
├─ Test Data: Hover each player card position
├─ Result: ✅ PASS (desktop/tablet), ⚠️ ISSUE (mobile)
└─ Fix: Disabled hover on touch devices (no hover state)

Test Case 3: Theme Switching
├─ Expected: All colors update instantly
├─ Test Data: Click all 3 theme buttons
├─ Result: ⚠️ ISSUE - Some colors not updating
└─ Fix: CSS variable scoping issue - moved to :root

Test Case 4: Responsive Layout
├─ Expected: Layout adapts at 1200px, 768px, 480px
├─ Test Data: Resize browser, test on real devices
├─ Result: ⚠️ ISSUES - Multiple problems
│   • Cards too large on mobile
│   • Deck overlapping on tablets
│   • Navigation breaking at 768px
└─ Fixes: Applied (see next slide)

Test Case 5: Accessibility
├─ Expected: Reduced motion disables animations
├─ Test Data: Enable "Reduce motion" in system prefs
├─ Result: ✅ PASS (Chrome, Safari, Firefox)
└─ Issues: None
```

**Speaker Notes:**
"I created detailed test cases for each feature. Most passed on first try, but we found issues with theme switching, mobile responsive design, and touch device hover states. Each issue was documented, tracked, and fixed."

---

### SLIDE 14: Bugs Found & Fixed
**Speaker: ADNAN**

**Slide Content:**
```
BUG TRACKING & RESOLUTION

BUG #1: Cards Too Large on Mobile
├─ Status: ✅ FIXED
├─ Description: Cards were 100px wide, overlapping on <480px screens
├─ Root Cause: No scaling in mobile media query
└─ Fix Applied:
    @media (max-width: 480px) {
        .card { width: 60px; height: 84px; }
    }

BUG #2: Deck Overlapping Content on Tablets
├─ Status: ✅ FIXED
├─ Description: Absolutely positioned deck covered player cards
├─ Root Cause: Fixed left: 15% didn't account for smaller screens
└─ Fix Applied:
    @media (max-width: 768px) {
        .deck { position: static; margin: 20px auto; }
    }

BUG #3: Theme Colors Not Updating
├─ Status: ✅ FIXED
├─ Description: Some elements kept default colors after theme change
├─ Root Cause: CSS variables defined in wrong scope
└─ Fix Applied:
    Moved all --variables from .table to :root selector

BUG #4: Animation Timing Felt Rushed
├─ Status: ✅ FIXED
├─ Description: Cards dealing too quickly, chaotic feel
├─ Root Cause: 0.1s delays were too short
└─ Fix Applied:
    Increased delays from 0.1s to 0.3s intervals

BUG #5: Hover Peek on Touch Devices
├─ Status: ✅ FIXED
├─ Description: :hover stuck "on" after tap on mobile
├─ Root Cause: Touch doesn't have hover state
└─ Fix Applied:
    @media (hover: none) {
        .card:hover { transform: none; }
    }
```

**Speaker Notes:**
"We found and fixed five significant bugs. The most critical were mobile card sizing, deck positioning on tablets, and theme variable scoping. Each bug was tracked, root cause identified, and a proper fix implemented and verified."

---

### SLIDE 15: Testing Results Summary
**Speaker: ADNAN**

**Slide Content:**
```
FINAL TEST RESULTS

✅ PASSED TESTS (95%+)
• Card dealing animations - all browsers
• 3D perspective effects - all platforms
• Chip hover animations - all browsers
• Burn card animation - all browsers
• Theme switching - all browsers (after fix)
• Responsive layouts - all breakpoints (after fixes)
• Accessibility - reduced motion works
• Performance - 60fps animations maintained

⚠️ KNOWN LIMITATIONS
• Hover effects disabled on touch devices (by design)
• Safari requires -webkit- prefixes for some properties
• Internet Explorer not supported (outdated browser)

📊 TESTING METRICS
• Total Test Cases: 25
• Passed on First Try: 20 (80%)
• Bugs Found: 5
• Bugs Fixed: 5
• Bugs Outstanding: 0
• Browser Compatibility: 100% (modern browsers)
• Device Compatibility: 100% (tested devices)

🎯 QUALITY ASSURANCE
All core features and stretch goals working correctly
across all modern browsers and device sizes.
```

**Speaker Notes:**
"Final testing showed 95%+ success rate. All bugs were fixed, all features work correctly, and we achieved 100% compatibility with modern browsers and tested devices. The product is production-ready."

---

## 🎬 SECTION 4: DEMO & WRAP-UP

### SLIDE 16: Live Demo
**Speaker: CARTER**

**Slide Content:**
```
LIVE DEMONSTRATION

We'll now show you the working application:

1. Introduction Page
   ↓
2. Card Dealing Animation
   ↓
3. Interactive Hover Effects
   ↓
4. Theme Switching
   ↓
5. Responsive Design

[SWITCH TO BROWSER]
```

**Speaker Notes:**
"Now let me show you the actual application in action. I'll walk through each feature we've discussed..."

[Perform live demo per original script - 4 minutes]

---

### SLIDE 17: Technical Achievements
**Speaker: CARTER**

**Slide Content:**
```
WHAT WE ACCOMPLISHED

CORE REQUIREMENTS ✅
✓ CSS Transforms (translate, rotate, scale)
✓ CSS Transitions (smooth hover effects)
✓ CSS Animations (15+ @keyframes)
✓ Responsive Design (3 breakpoints)
✓ Accessibility Features

STRETCH GOALS ✅ (All 3 for Extra Credit)
✓ 3D Perspective Effects
✓ Dealer Burn Card Animation
✓ Interactive Hover Peek

ADDITIONAL FEATURES ✅
✓ Theme Customization System
✓ Professional UI/UX Design
✓ Cross-Browser Compatibility
✓ Performance Optimization
✓ Comprehensive Documentation

CODE STATISTICS:
• 1,100+ lines of code
• 15+ keyframe animations
• 3 responsive breakpoints
• 3 color themes
• 0 JavaScript files
```

**Speaker Notes:**
"We accomplished all core requirements, implemented all three stretch goals for extra credit, and added professional polish with themes, accessibility, and comprehensive testing."

---

### SLIDE 18: Project Management
**Speaker: BOTH**

**Slide Content:**
```
TEAM: CSS DEALERS

METHODOLOGY: Kanban

Carter Tierney - Lead Developer
├─ HTML structure & semantic markup
├─ CSS animations & transitions
├─ 3D transform implementation
├─ Theme customization system
└─ Documentation & presentation

Adnan - QA Tester & UX
├─ Cross-browser testing
├─ Device compatibility testing
├─ User experience evaluation
├─ Bug tracking & reporting
└─ Presentation support

WORKFLOW:
┌──────────┐   ┌────────────┐   ┌────────┐   ┌──────┐
│  TO DO   │ → │ IN PROGRESS│ → │ REVIEW │ → │ DONE │
└──────────┘   └────────────┘   └────────┘   └──────┘

Daily check-ins, continuous testing, clear communication
```

**Speaker Notes:**
**CARTER:** "We used Kanban for project management with clear role divisions."
**ADNAN:** "Daily check-ins and continuous testing kept us on track and ensured quality."

---

### SLIDE 19: Learning Outcomes
**Speaker: CARTER**

**Slide Content:**
```
KEY LEARNINGS

TECHNICAL SKILLS:
• Mastery of CSS transforms, transitions, animations
• 3D perspective and transform-style: preserve-3d
• CSS custom properties for dynamic theming
• Performance optimization with GPU-accelerated properties
• Responsive design patterns and breakpoint strategies
• Accessibility implementation (prefers-reduced-motion)

COLLABORATION SKILLS:
• Role division and task management
• Continuous testing and feedback loops
• Bug tracking and resolution processes
• Effective technical communication

CSS POWER:
JavaScript isn't always necessary!
Rich, interactive experiences can be built
with pure HTML & CSS.

FUTURE APPLICATIONS:
These techniques apply to any web project:
• Loading animations
• UI transitions
• Interactive components
• Responsive layouts
• Theme systems
```

**Speaker Notes:**
"This project taught us that CSS is incredibly powerful. We mastered advanced animations, 3D effects, and responsive design. We also learned valuable collaboration skills that we'll use in future projects."

---

### SLIDE 20: Future Enhancements
**Speaker: ADNAN**

**Slide Content:**
```
IF WE HAD MORE TIME...

SHORT-TERM ADDITIONS:
• Sound effects (card shuffle, chip clinks)
• More theme options (5+ color schemes)
• Card flip animations (face down → face up)
• Chip stacking animations
• More card games (Poker, Baccarat)

LONG-TERM ENHANCEMENTS:
• Add JavaScript for gameplay logic
• Score tracking and betting system
• Multiplayer functionality
• User accounts and saved preferences
• Real-time game state management
• AI dealer with game rules
• Tutorial mode for new players

SCALABILITY:
The current CSS architecture is modular
and could easily integrate with JavaScript
game logic for full functionality.
```

**Speaker Notes:**
"While we're proud of the current implementation, there's room to grow. Short-term we could add sounds and more themes. Long-term, JavaScript could add actual gameplay. Our clean CSS architecture makes this scalable."

---

### SLIDE 21: Conclusion & Questions
**Speaker: BOTH**

**Slide Content:**
```
THANK YOU!

PROJECT SUMMARY:
BlackJack Dealer Experience - Pure HTML/CSS
✅ All requirements met
✅ All stretch goals achieved
✅ Professional quality
✅ Fully tested and documented

TEAM: CSS DEALERS
Carter Tierney - Lead Developer
Adnan - QA Tester & UX

VIEW THE CODE:
github.com/[your-repo] (if applicable)

QUESTIONS?

We're happy to discuss:
• Technical implementation details
• Design decisions
• Testing challenges
• CSS techniques
• Future enhancements
```

**Speaker Notes:**
**CARTER:** "Thank you for your time. We're proud of what we built."
**ADNAN:** "We're happy to answer any questions about the code, testing process, or design decisions."
**BOTH:** [Wait for questions]

---

## 📝 SPEAKER ASSIGNMENTS

### CARTER PRESENTS:
- Slide 1: Title
- Slide 4: Solution Overview
- Slide 5: Key Design Features
- Slide 7: CSS Transforms
- Slide 8: CSS Transitions
- Slide 9: CSS Animations
- Slide 11: CSS Variables
- Slide 16: Live Demo
- Slide 17: Technical Achievements
- Slide 19: Learning Outcomes
- Slide 21: Conclusion

### ADNAN PRESENTS:
- Slide 2: Problem Statement
- Slide 3: User Requirements
- Slide 6: User Interface
- Slide 10: 3D Perspective
- Slide 12: Testing Methodology
- Slide 13: Test Plan
- Slide 14: Bugs Fixed
- Slide 15: Testing Results
- Slide 18: Project Management (with Carter)
- Slide 20: Future Enhancements
- Slide 21: Questions (with Carter)

---

## 🎨 POWERPOINT DESIGN TIPS

### VISUAL STYLE:
- **Color Scheme:** Dark backgrounds with gold (#FFD700) and green (#0D5E2A) accents (casino theme)
- **Fonts:** 
  - Titles: Bold, 44pt
  - Body: Clean sans-serif, 24-28pt
  - Code: Monospace, 18-20pt
- **Layout:** Consistent spacing, lots of white (dark) space
- **Images:** Include screenshots of the actual application

### CODE SNIPPETS:
- Use dark theme code highlighting (VS Code style)
- Syntax highlighting for CSS
- Keep snippets short and focused (10-15 lines max)
- Add comments in code for clarity

### ANIMATIONS (IN POWERPOINT):
- Keep PowerPoint animations minimal (ironic, right?)
- Use simple fade-ins for bullet points
- Avoid distracting transitions between slides

### VISUALS TO INCLUDE:
- Screenshot of blackjack table (multiple slides)
- Diagram of 3D perspective system (Slide 10)
- Before/After of bugs fixed (Slide 14)
- Team photo or headshots (if available)

---

## ⏱️ TIMING GUIDE

| Section | Slides | Time | Presenter |
|---------|--------|------|-----------|
| Title & Intro | 1 | 0:30 | Carter |
| Problem Statement | 2-3 | 2:00 | Adnan |
| Solution & Design | 4-6 | 3:00 | Carter/Adnan |
| Code Details | 7-11 | 4:00 | Carter |
| Testing | 12-15 | 3:00 | Adnan |
| Demo | 16 | 2:00 | Carter |
| Wrap-up | 17-21 | 2:00 | Both |
| **TOTAL** | **21 slides** | **~16 min** | **+ Q&A** |

**Note:** Aim for 12-14 minutes to leave 2-3 minutes for questions.

---

## 🎤 PRESENTATION CHECKLIST

**BEFORE PRESENTATION:**
- [ ] PowerPoint file tested and working
- [ ] Code snippets are readable and properly formatted
- [ ] Screenshots are high quality and clear
- [ ] Browser with live demo ready
- [ ] Backup browser open (just in case)
- [ ] Practiced timing (12-14 minutes)
- [ ] Both presenters know their slides
- [ ] Practiced handoffs between speakers
- [ ] Clicker/remote tested (if using)

**DURING PRESENTATION:**
- [ ] Speak clearly and at moderate pace
- [ ] Make eye contact with audience
- [ ] Point to specific elements on screen
- [ ] Show enthusiasm - you built something cool!
- [ ] Support each other during transitions
- [ ] Stay within time limit
- [ ] Invite questions at end

---

**Good luck, CSS Dealers! Show them what pure CSS can do! 🎰♠️♥️♣️♦️**

