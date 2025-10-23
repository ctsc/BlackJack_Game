# BlackJack Dealer Experience - Presentation Script
## CSC 4370/6370 Web Programming - Fall 2025
**Presenters:** Carter Tierney & Adnan  
**Duration:** 10-15 minutes

---

## 🎬 OPENING (2 minutes)

### **CARTER:**
"Good [morning/afternoon] everyone. Today we're excited to present our BlackJack Dealer Experience project. I'm Carter Tierney, the lead developer and team leader."

### **ADNAN:**
"And I'm Adnan, responsible for testing, quality assurance, and user experience validation. Together, we've created something pretty unique for this assignment."

### **CARTER:**
"So, what's the challenge we tackled? The project required us to create an interactive, animated blackjack card dealing experience using *only* HTML and CSS—absolutely no JavaScript. That means all the card animations, 3D effects, and interactivity you're about to see are achieved purely through CSS transforms, transitions, and keyframe animations."

### **ADNAN:**
"We didn't just meet the requirements—we implemented all three stretch goals for extra credit: 3D perspective effects, a dealer burn card animation, and interactive hover peek functionality. Let's show you what we built."

**[TRANSITION: Switch to live demo]**

---

## 🎮 LIVE DEMO (4 minutes)

### **CARTER:**
"Let me walk you through the experience. When users first visit, they land on this introduction page..."

**[Navigate to index.html]**

"Notice the smooth fade-in animation. Everything here is CSS—the card animations you see are pure @keyframes."

**[Click 'Enter Casino' button]**

"And now we enter the main blackjack table."

### **ADNAN:**
"Right away, you'll notice several animations happening simultaneously. Let me point out the key features:"

**[Point to screen elements as you describe them]**

1. **"See the dealer shoe on the left? The deck is continuously shuffling with a subtle rotation and scale animation."**

2. **"Watch this burn card sliding off the deck—this is one of our stretch goals. It's on an infinite loop, smoothly translating and fading out."**

3. **"Now observe the card dealing sequence. Cards deal automatically from the shoe to the dealer first, then to each of the three player positions."**

### **CARTER:**
"The timing here was critical. Each card has a staggered delay—0.3 seconds between each deal—to create that natural, sequential dealing rhythm you'd see in a real casino."

**[Hover over player cards]**

"Now let me show you the hover peek feature—another stretch goal. When I hover over a player's cards, they lift and tilt in 3D space. This uses multiple transforms: translateY to lift, rotateY for the tilt, and we maintain the 3D perspective throughout."

### **ADNAN:**
**[Hover over chips in chip bank]**

"The chips are interactive too. Hovering creates a scale-up effect with an animated glowing shadow. These are all CSS transitions with proper timing functions."

### **CARTER:**
**[Click theme switcher buttons]**

"We also implemented theme customization using CSS variables. Watch as I switch from Classic Green to Royal Blue... and now Ruby Red. The entire color scheme changes instantly—the felt, the table border, even the chip colors—all driven by CSS custom properties."

### **ADNAN:**
**[Resize browser window or show responsive view]**

"And of course, it's fully responsive. On tablets and mobile devices, the layout adapts—cards scale down, the deck repositions, and navigation elements stack vertically for better usability."

---

## 💻 CODE HIGHLIGHTS (5 minutes)

### **CARTER:**
"Now let's dive into the technical implementation. I want to show you five key techniques we used."

**[Open styles.css or show code slides]**

**1. CSS Variables for Theming:**

"We defined custom properties at the root level:"

```css
:root {
    --felt-color: #0d5e2a;
    --chip-red: #dc143c;
    --table-border: #8b6914;
}
```

"Then throughout our stylesheet, we reference these variables. When users click a theme button, we simply update these root variables with inline styles, and the entire page re-renders with new colors. No JavaScript manipulation needed."

### **ADNAN:**

**2. 3D Perspective Implementation:**

"For the 3D effects, we used a two-part approach. First, we set perspective on the container:"

```css
.table-container {
    perspective: 1000px;
}
```

"Then on individual cards, we preserved the 3D space and applied rotations:"

```css
.card {
    transform-style: preserve-3d;
    transform: rotateY(-5deg) rotateX(2deg);
}
```

"This creates that realistic depth where cards appear to exist in 3D space, not just flat on the screen."

### **CARTER:**

**3. Keyframe Animation Sequences:**

"The card dealing animations were the most complex. Here's an example for Player 1's first card:"

```css
@keyframes dealToPlayer1Card1 {
    0% {
        left: 15%;
        top: 45%;
        opacity: 0;
    }
    50% {
        opacity: 1;
    }
    100% {
        left: 20%;
        top: 70%;
        transform: rotateZ(2deg);
    }
}
```

"We created 15+ unique animations—each card has its own path from the dealer shoe to its final position."

### **ADNAN:**

**4. Hover Effect Techniques:**

"For the card hover peek, we combined multiple transforms:"

```css
.player-cards .card:hover {
    transform: translateY(-30px) rotateY(-10deg) rotateX(5deg) rotateZ(-2deg);
    transition: all 0.3s ease-out;
    cursor: pointer;
    z-index: 10;
}
```

"The key here is the smooth transition—0.3 seconds feels instant to users but smooth enough to be visually appealing. We also adjusted z-index so hovered cards appear above others."

### **CARTER:**

**5. Responsive Design Strategies:**

"We used a mobile-first approach with three breakpoints:"

```css
@media (max-width: 1200px) { /* Tablet adjustments */ }
@media (max-width: 768px) { /* Mobile landscape */ }
@media (max-width: 480px) { /* Mobile portrait */ }
```

"At each breakpoint, we adjust card sizes, reposition the deck, and modify layouts. For example, on mobile, cards scale from 100px width down to 60px, and the three-player layout becomes more vertical."

---

## 🚧 TECHNICAL CHALLENGES (2 minutes)

### **ADNAN:**
"Of course, this project wasn't without its challenges. Let me share what we encountered during testing."

**Challenge 1: Timing the Card Deal Animations**

"Initially, all cards dealt too quickly—it looked chaotic. We had to carefully tune the animation durations and stagger delays. Each card has a 1.5-second animation with delays increasing by 0.3 seconds. Getting this rhythm right took multiple iterations."

### **CARTER:**

**Challenge 2: Achieving True 3D Effects**

"CSS 3D transforms are powerful, but they have limitations. We wanted cards to look realistic from all angles. The solution was combining perspective at the container level with transform-style: preserve-3d on children, plus careful tuning of rotateX, rotateY, and rotateZ values."

### **ADNAN:**

**Challenge 3: Cross-Browser Compatibility**

"Different browsers handle animations slightly differently. Safari, in particular, needed special attention with -webkit prefixes for some transforms. We tested on Chrome, Firefox, Safari, and Edge to ensure consistency."

### **CARTER:**

**Challenge 4: Performance Optimization**

"Animating 15+ elements simultaneously can strain browser rendering. We optimized by using transform and opacity properties—which are GPU-accelerated—instead of animating position properties like top and left excessively. We also implemented prefers-reduced-motion media queries for accessibility."

---

## 🎯 CONCLUSION (2 minutes)

### **ADNAN:**
"So, what did we achieve? Let's recap:"

- ✅ **All core requirements:** Transforms, transitions, animations, responsive design
- ✅ **All three stretch goals:** 3D perspective, burn card, hover peek
- ✅ **Accessibility features:** Reduced motion support, semantic HTML
- ✅ **Professional polish:** Three theme options, smooth UX, clean code

### **CARTER:**
"We used the Kanban methodology for project management—daily check-ins, visual task boards, and continuous delivery. This kept us organized and on track."

### **ADNAN:**
"From a testing perspective, I verified functionality across four major browsers and four device sizes. We found and fixed issues with mobile card sizing, tablet deck positioning, and theme variable scoping—all documented in our README."

### **CARTER:**
"What did we learn? Advanced CSS is incredibly powerful. You can create rich, interactive experiences without a single line of JavaScript. We mastered keyframe animations, 3D transforms, CSS variables, and responsive design patterns that we'll use in future projects."

### **ADNAN:**
"We also learned valuable collaboration skills—clear role division, continuous testing, and effective communication made this project successful."

### **CARTER:**
"If we were to take this further, we could add:"
- Sound effects for card shuffling and chip clicks
- JavaScript for actual gameplay logic and scoring
- Multiplayer functionality
- More card games like Poker or Baccarat

### **ADNAN:**
"But for now, we're proud of what we've built with just HTML and CSS."

### **CARTER:**
"Thank you for your time. We're happy to answer any questions!"

---

## 🎤 Q&A PREPARATION

### **Potential Questions & Suggested Responses:**

**Q: "How long did this project take?"**
- **EITHER:** "About [X] days of active development, plus [Y] days of testing and refinement. The animation timing alone took several iterations to get right."

**Q: "What was the hardest part?"**
- **CARTER:** "Definitely the staggered card dealing animations. Creating 15+ unique keyframe animations and timing them perfectly was complex."
- **ADNAN:** "From a testing perspective, ensuring consistent behavior across browsers, especially Safari's rendering quirks."

**Q: "Why no JavaScript?"**
- **CARTER:** "The project requirements specified HTML/CSS only, which was actually a great constraint. It forced us to deeply understand what CSS can do and pushed us to creative solutions."

**Q: "How did you implement the theme switching without JavaScript?"**
- **CARTER:** "We use CSS custom properties defined at :root. The theme switcher links have onclick inline styles that update those variables. It's technically HTML's onclick attribute, not JavaScript files."

**Q: "Is this actually playable?"**
- **ADNAN:** "Not yet—it's purely visual. To make it a real game, we'd need JavaScript for game logic, user input handling, and state management. But this demonstrates the presentation layer that could wrap around that logic."

**Q: "Did you use any CSS frameworks?"**
- **CARTER:** "No, this is completely vanilla CSS—no Bootstrap, no Tailwind, no libraries. Everything you see we wrote from scratch."

**Q: "How did you handle accessibility?"**
- **ADNAN:** "We implemented prefers-reduced-motion media queries to reduce or eliminate animations for users with motion sensitivity. We also ensured proper color contrast and semantic HTML structure."

**Q: "What would you do differently?"**
- **CARTER:** "Maybe start with a design mockup first. We did some trial and error with positioning. A clear visual plan would've saved time."
- **ADNAN:** "I'd implement automated testing earlier. Manual testing across browsers was time-consuming."

---

## 📋 DEMO CHECKLIST

**Before Presentation:**
- [ ] Test all links work
- [ ] Verify animations play smoothly
- [ ] Check browser zoom level (100% recommended)
- [ ] Close unnecessary browser tabs
- [ ] Have backup browser ready
- [ ] Test audio/video connection
- [ ] Have code examples ready to show
- [ ] Practice timing (aim for 12-13 minutes to leave time for Q&A)

**During Demo:**
- [ ] Speak clearly and at a moderate pace
- [ ] Face the audience, not just the screen
- [ ] Point to specific elements when describing them
- [ ] Pause briefly after showing each feature
- [ ] Make eye contact with instructor/audience
- [ ] Show enthusiasm—you built something cool!

**Transitions:**
- **Carter starts:** Introduction and project overview
- **Adnan joins:** Team intro and challenge statement
- **Carter leads:** Initial demo walkthrough
- **Adnan takes over:** Feature demonstration
- **Carter shows:** Theme switching and responsiveness
- **Both alternate:** Code highlights (5 sections split)
- **Adnan leads:** Challenges faced
- **Carter contributes:** Technical solutions
- **Both together:** Conclusion and summary
- **Either handles:** Q&A based on question topic

---

## 💡 PRESENTATION TIPS

**For Carter:**
- You're the technical lead, so dive deep on code architecture
- Explain the "why" behind decisions, not just the "what"
- Use analogies to explain complex concepts (e.g., "CSS variables are like themes in a game")
- Show confidence in your code—you built this!

**For Adnan:**
- You're the quality expert, so emphasize testing and UX
- Point out issues you found and how they were fixed
- Speak to the user experience and polish
- Your perspective balances Carter's technical depth

**For Both:**
- Make eye contact with each other during transitions
- Support each other's points ("Exactly, and to add to that...")
- Keep energy up—enthusiasm is contagious
- If you make a mistake, just keep going
- Practice the handoffs between speakers
- Time yourselves during practice runs

---

**Good luck! You've built something impressive—now show it off with confidence! 🎰♠️♥️♣️♦️**


