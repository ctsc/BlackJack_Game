# BlackJack Dealer Experience
## CSC 4370/6370 Web Programming - Fall 2025

---

## 📋 Project Overview

**Project Title:** Black Jack Dealer HTML/CSS  
**Team Leader:** Carter Tierney  
**Team Members:**
- Carter Tierney - Coder / Presenter
- Adnan - Tester / Model / Presenter

**Due Date:** October 22, 2025

---

## 🎯 Project Description

This project is an interactive HTML/CSS-only web application that simulates an authentic blackjack card dealing experience. Without using any JavaScript, we've created a visually engaging and animated casino card table that demonstrates mastery of CSS transforms, transitions, and keyframe animations.

The application features realistic card dealing sequences, 3D card perspectives, interactive chip animations, and customizable table themes - all achieved through pure CSS.

---

## ✨ Features Implemented

### Core Features (Required)

✅ **Shuffle Animation**
- Deck cards feature continuous shuffle animation using `@keyframes`
- Cards subtly rotate and scale to simulate shuffling motion
- Multiple card layers create realistic depth

✅ **Deal Sequence**
- Cards slide from the dealer shoe to player positions
- Implemented using `transform: translate()` with staggered `animation-delay`
- Each card follows a unique path with rotation effects
- 8 total cards dealt in sequence (2 to dealer, 2 to each of 3 players)

✅ **Chip Hover Effect**
- Interactive chips scale up on hover
- Glowing effect using animated `box-shadow`
- Smooth transitions for professional feel

✅ **Theme Customization**
- CSS variables for easy theme switching
- Three color schemes: Classic Green, Royal Blue, Ruby Red
- Customizable felt color, chip colors, and table border
- Instant theme changes without page reload

### Stretch Goals (All 3 Implemented for Extra Credit)

✅ **3D Perspective**
- Applied `perspective: 1000px` to table container
- Cards use `transform: rotateY()` and `rotateX()` for realistic angles
- `transform-style: preserve-3d` maintains 3D space
- Cards appear to lift off the table surface

✅ **Dealer Burn Card**
- Animated card slides off the deck before dealing begins
- Uses complex keyframe animation with rotation and translation
- Fades out as it moves away from deck
- Loops continuously to show the effect

✅ **Hover Peek**
- Player cards lift and tilt when hovered
- Combined `translateY()`, `rotateY()`, `rotateX()`, and `rotateZ()`
- Cursor changes to pointer for better UX
- Smooth transition effects

### Additional Features

✅ **Responsive Design**
- Mobile-first approach with breakpoints at 1200px, 768px, and 480px
- Layout adapts to all screen sizes
- Cards and chips scale appropriately
- Navigation reorganizes for mobile views

✅ **Accessibility**
- `@media (prefers-reduced-motion)` support
- Reduced animations for users with motion sensitivity
- Semantic HTML structure
- Proper color contrast ratios

✅ **Professional UI/UX**
- Introduction page with project information
- Smooth page transitions and animations
- Visual feedback on all interactive elements
- Casino-themed color palette

---

## 🏗️ Project Structure

```
BlackJackWeb/
├── index.html              # Introduction page with team info
├── blackjack.html         # Main dealer table simulation
├── styles.css             # All CSS styling, animations, and themes
├── README.md              # Project documentation (this file)
└── projectinstructions.md # Original project requirements
```

---

## 🎨 CSS Techniques Used

### Transforms
- `translate()` - Card dealing movement
- `rotate()` / `rotateX()` / `rotateY()` / `rotateZ()` - 3D card rotations
- `scale()` - Chip hover effects and card animations
- `perspective()` - 3D depth perception

### Transitions
- Smooth hover effects on all interactive elements
- Duration: 0.3s - 0.6s for natural feel
- Easing functions: `ease`, `ease-out`, `ease-in-out`

### Animations (@keyframes)
- `burnCardSlide` - Burn card sliding animation
- `deckShuffle` - Continuous deck shuffling
- `dealToDealer1/2` - Dealer card dealing sequences
- `dealToPlayer1Card1/2` - Player 1 cards
- `dealToPlayer2Card1/2` - Player 2 cards
- `dealToPlayer3Card1/2` - Player 3 cards
- `fadeInDown` / `fadeInUp` / `fadeIn` - Page entrance animations

### Advanced CSS Features
- CSS Custom Properties (Variables)
- Flexbox for responsive layouts
- Radial and linear gradients
- Box shadows with multiple layers
- Backdrop filters
- Pseudo-elements (::before, ::after)

---

## 🎬 How It Works

### Initial Load
1. User lands on `index.html` with project information
2. Introduction card fades in with staggered animations
3. "Enter Casino" button invites user to main experience

### Casino Table Experience
1. Table loads with dealer shoe on the left
2. Burn card begins sliding animation immediately
3. Deck shuffles continuously in the background
4. Cards deal automatically in sequence:
   - First to dealer (face up Ace of Spades)
   - Second to dealer (face up King of Spades)
   - Then to each player position with delays
5. Chips are positioned in betting areas
6. User can interact:
   - Hover over player cards to "peek" at them
   - Hover over chips in the chip bank for glow effect
   - Click theme switcher to change table colors

---

## 🎓 Design Decisions

### Color Palette
- **Gold (#ffd700)** - Premium casino feel, highlights important elements
- **Dark Background** - Focuses attention on the table
- **Green Felt** - Traditional casino aesthetic
- **High Contrast** - Ensures readability

### Animation Timing
- **Staggered Delays** - Cards deal one at a time (0.3s intervals)
- **Smooth Transitions** - 0.3s-0.6s feels natural, not jarring
- **Continuous Loops** - Shuffle and burn card repeat infinitely
- **Hover Responses** - Instant feedback (<0.3s)

### Layout Approach
- **Centered Design** - Natural focus point
- **Elliptical Table** - Authentic casino table shape
- **Strategic Positioning** - Dealer at top, players at bottom
- **Absolute Positioning** - Deck and chip bank anchored to table

### User Experience
- **Visual Feedback** - All interactive elements respond to hover
- **Clear Navigation** - Easy return to intro page
- **Instructions** - Helper text explains interactions
- **Theme Options** - Personalization increases engagement

---

## 📱 Responsive Breakpoints

| Breakpoint | Changes |
|------------|---------|
| **1200px** | Reduce spacing, adjust chip bank position |
| **768px** | Stack navigation, smaller cards, repositioned deck |
| **480px** | Vertical player layout, simplified animations |

---

## ♿ Accessibility Features

- **Reduced Motion**: Respects user's system preferences
- **Semantic HTML**: Proper document structure
- **Color Contrast**: WCAG AA compliant
- **Hover States**: Clear interactive element identification
- **Keyboard Navigation**: Links are keyboard accessible

---

## 🔧 Technical Highlights

### CSS Variables Implementation
```css
:root {
    --felt-color: #0d5e2a;
    --chip-red: #dc143c;
    --table-border: #8b6914;
}
```
This allows instant theme switching by modifying a few variables.

### 3D Card Perspective
```css
.table-container {
    perspective: 1000px;
}
.card {
    transform-style: preserve-3d;
    transform: rotateY(-5deg) rotateX(2deg);
}
```
Creates realistic card depth without JavaScript.

### Staggered Deal Animation
```css
.player1-card-1 {
    animation: dealToPlayer1Card1 1.5s ease-out 0.6s both;
}
```
Sequential delays create natural dealing rhythm.

---

## 🧪 Testing Process

### Tester: Adnan

**Browser Compatibility Testing**
- ✅ Chrome (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ✅ Edge (latest)

**Device Testing**
- ✅ Desktop (1920x1080)
- ✅ Laptop (1366x768)
- ✅ Tablet (768x1024)
- ✅ Mobile (375x667)

**Feature Verification**
- ✅ All cards deal in correct sequence
- ✅ Hover effects work on all interactive elements
- ✅ Theme switcher changes colors correctly
- ✅ Animations play smoothly without lag
- ✅ Responsive layout adapts properly
- ✅ Reduced motion preference works

**Issues Found & Fixed**
1. Initial card sizes too large on mobile → Reduced to 60px width
2. Deck positioning overlapped on tablets → Changed to static positioning on mobile
3. Animation timing felt rushed → Adjusted delays to 0.3s intervals
4. Theme colors not applying → Fixed CSS variable scoping

---

## 📊 Project Management

### Team Roles

**Carter Tierney**
- Primary coder
- HTML/CSS implementation
- Animation development
- Presentation preparation

**Adnan**
- Quality assurance testing
- Cross-browser compatibility
- User experience feedback
- Presentation support

### Methodology: Kanban

We used a Kanban approach for this project:

**Benefits:**
- Visual workflow management
- Clear task priorities
- Flexible adaptation to changes
- Continuous delivery mindset

**Our Workflow:**
1. **To Do**: Core features, stretch goals, documentation
2. **In Progress**: Active coding and testing
3. **Review**: Code review and browser testing
4. **Done**: Completed and verified features

**Daily Check-ins:**
- Morning: Plan day's work
- Evening: Review progress and blockers
- Continuous: Update task board

---

## 🚀 Future Enhancements

If we were to expand this project, we could add:
- Sound effects (card shuffling, chip clicks)
- JavaScript for actual gameplay logic
- Score tracking and game state
- Multiplayer functionality
- More card games (Poker, Baccarat)
- Save/load table preferences
- Tutorial mode for new players

---

## 📚 Resources & References

**CSS Techniques**
- MDN Web Docs - CSS Transforms
- MDN Web Docs - CSS Animations
- CSS-Tricks - Complete Guide to Flexbox

**Design Inspiration**
- Casino table layouts
- Playing card design standards
- Material design principles

**Accessibility**
- WCAG 2.1 Guidelines
- WebAIM Color Contrast Checker
- MDN Accessibility Documentation

---

## 📝 Code Statistics

- **Total Lines of Code**: ~1,100
- **HTML Files**: 2
- **CSS Files**: 1
- **CSS Animations**: 15+
- **Responsive Breakpoints**: 3
- **Color Themes**: 3
- **Interactive Elements**: 15+

---

## 🎓 Learning Outcomes

Through this project, we gained proficiency in:
1. Advanced CSS animations and keyframes
2. 3D transforms and perspective
3. CSS custom properties for theming
4. Responsive design techniques
5. Accessibility best practices
6. Team collaboration and Kanban methodology
7. Clean, maintainable CSS architecture

---

## 📦 Deployment

### Running the Project

1. **Clone/Download** the project folder
2. **Open** `index.html` in any modern web browser
3. **Click** "Enter Casino" to view the blackjack table
4. **Interact** with cards and chips to see animations

No build process or dependencies required - it's pure HTML/CSS!

### File Requirements
- All files must be in the same directory
- `styles.css` must be in the root folder
- No external dependencies or libraries needed

---

## ✅ Requirements Checklist

### Core Requirements
- ✅ HTML/CSS only (no JavaScript)
- ✅ CSS Transforms implementation
- ✅ CSS Transitions implementation
- ✅ CSS Animations (@keyframes)
- ✅ Responsive design
- ✅ Accessibility features
- ✅ Theme customization
- ✅ Professional design

### Project Requirements
- ✅ Introduction page with team info
- ✅ All core features implemented
- ✅ All 3 stretch goals implemented
- ✅ Proper file structure
- ✅ Documentation provided
- ✅ Clean, commented code
- ✅ Presentation-ready

---

## 🎤 Presentation Outline (10-15 minutes)

### 1. Introduction (2 min)
- Team members and roles
- Project overview and goals
- Problem statement: Creating interactivity without JavaScript

### 2. Live Demo (4 min)
- Introduction page walkthrough
- Card dealing sequence demonstration
- Interactive features showcase
- Theme switching demonstration
- Responsive design display

### 3. Code Highlights (5 min)
- CSS variables for theming
- 3D perspective implementation
- Keyframe animation sequences
- Hover effect techniques
- Responsive design strategies

### 4. Technical Challenges (2 min)
- Timing card deal animations
- Achieving 3D effects with pure CSS
- Cross-browser compatibility
- Performance optimization

### 5. Conclusion (2 min)
- Achievement summary
- Learning outcomes
- Future possibilities
- Questions

---

## 👥 Team Credits

**Carter Tierney** - Lead Developer
- HTML structure and semantic markup
- CSS animations and transitions
- 3D transform implementation
- Theme customization system
- Documentation

**Adnan** - Quality Assurance
- Cross-browser testing
- Responsive design verification
- User experience evaluation
- Bug reporting and tracking
- Presentation support

---

## 📄 License

This project was created as a student assignment for CSC 4370/6370 Web Programming at [University Name], Fall 2025.

---

## 📞 Contact

For questions about this project:
- **Carter Tierney** - Lead Developer
- **Course**: CSC 4370/6370 Web Programming
- **Term**: Fall 2025

---

**Thank you for reviewing our BlackJack Dealer Experience project!**

*Created with ♠ ♥ ♣ ♦ by Carter Tierney & Adnan*

