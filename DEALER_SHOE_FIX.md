# Dealer Shoe Fix - Simplified Design

## Problem
- Cards in the dealer shoe were displaying vertically down the page
- When the burn card slid off, it left an empty container
- Multiple stacked cards were causing layout issues

## Solution
**Simplified to a single card display:**
- Removed all individual stacked cards (stack-1 through stack-8)
- Made the `.deck` container itself look like a card back
- Burn card now slides off the deck container directly

## Changes Made

### HTML (blackjack.html)
**Before:**
```html
<div class="deck">
    <div class="card burn-card">
        <div class="card-back"></div>
    </div>
    <div class="card deck-card stack-1"><div class="card-back"></div></div>
    <div class="card deck-card stack-2"><div class="card-back"></div></div>
    <!-- ... 6 more stacked cards ... -->
</div>
```

**After:**
```html
<div class="deck">
    <!-- Burn card that slides off first -->
    <div class="burn-card"></div>
</div>
```

### CSS (styles.css)

**1. Deck container as card back:**
```css
.deck {
    position: relative;
    width: 80px;
    height: 112px;
    margin-bottom: 10px;
    background: linear-gradient(135deg, #1e3a8a 0%, #3b82f6 100%);
    border-radius: 8px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.5);
    animation: deckShuffle 4s ease-in-out 2.5s infinite;
}

/* Card back pattern on deck */
.deck::before {
    content: '';
    position: absolute;
    top: 5px;
    left: 5px;
    right: 5px;
    bottom: 5px;
    border: 2px solid rgba(255, 255, 255, 0.3);
    border-radius: 6px;
}

.deck::after {
    content: '♠ ♥ ♣ ♦';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: rgba(255, 255, 255, 0.4);
    font-size: 1.5rem;
    letter-spacing: 3px;
}
```

**2. Burn card as standalone card:**
```css
.burn-card {
    position: absolute;
    top: 0;
    left: 0;
    width: 80px;
    height: 112px;
    background: linear-gradient(135deg, #1e3a8a 0%, #3b82f6 100%);
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    animation: burnCardSlide 2s ease-out 0.5s forwards;
    z-index: 10;
}

/* Burn card pattern */
.burn-card::before {
    content: '';
    position: absolute;
    top: 5px;
    left: 5px;
    right: 5px;
    bottom: 5px;
    border: 2px solid rgba(255, 255, 255, 0.3);
    border-radius: 6px;
}

.burn-card::after {
    content: '♠ ♥ ♣ ♦';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: rgba(255, 255, 255, 0.4);
    font-size: 1.5rem;
    letter-spacing: 3px;
}
```

**3. Simplified shuffle animation:**
```css
@keyframes deckShuffle {
    0%, 100% {
        transform: rotate(0deg);
    }
    25% {
        transform: rotate(2deg) scale(1.05);
    }
    50% {
        transform: rotate(-2deg) scale(0.95);
    }
    75% {
        transform: rotate(1deg) scale(1.02);
    }
}
```

**4. Removed:**
- `.deck-card` styling
- `.stack-1` through `.stack-8` styling
- Complex deck card transform offsets

## What You'll See Now

**Dealer Shoe (upper right corner):**
1. ✅ Single blue card back with gradient
2. ✅ White border pattern
3. ✅ Suit symbols (♠ ♥ ♣ ♦) in center
4. ✅ "Dealer Shoe" gold label above it
5. ✅ Subtle shuffle animation (slight rotation and scale)

**Burn Card Animation:**
1. ✅ Card slides off from the deck at 0.5s
2. ✅ Arcs away dramatically with rotation
3. ✅ Fades out as it moves
4. ✅ Reveals the dealer shoe underneath

**Timeline:**
- 0.0s: Page loads with dealer shoe visible
- 0.5s: Burn card starts sliding off
- 2.5s: Burn card completes, shoe shuffle animation begins
- 2.8s+: Cards start dealing from the shoe
- 2.5s onward: Dealer shoe continuously shuffles with subtle animation

## Benefits

**Simpler:**
- Less HTML markup
- Cleaner CSS
- Easier to maintain

**Better Performance:**
- Fewer DOM elements
- Less complex animations
- Faster rendering

**Clearer Visual:**
- Single card is easier to understand
- Burn card effect is more visible
- No confusing vertical stack

**Still Feature-Complete:**
- ✅ Dealer shoe visible
- ✅ Burn card animation (stretch goal)
- ✅ Shuffle animation (core feature)
- ✅ Visual source for dealt cards
- ✅ Professional appearance

## Testing

Open `blackjack.html` and verify:
1. [ ] Dealer shoe displays as a single blue card back
2. [ ] Card has white border and suit symbols
3. [ ] Burn card slides off dramatically at 0.5s
4. [ ] After burn card leaves, dealer shoe remains visible
5. [ ] Dealer shoe has subtle shuffle animation (starts at 2.5s)
6. [ ] "Dealer Shoe" label is visible and gold colored
7. [ ] Cards appear to deal from this location

---

**Result: Clean, simple, and professional dealer shoe display!** 🎴

