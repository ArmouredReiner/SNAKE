# Snake Game - Specification Document

## 1. Project Overview

- **Project Name**: Snake Game
- **Type**: Browser-based arcade game (HTML5 Canvas)
- **Core Functionality**: Classic snake game with automatic movement, directional control, food collection, and game over detection
- **Target Users**: Casual gamers on desktop and mobile devices

---

## 2. Visual & Rendering Specification

### Scene Setup
- **Canvas**: 2D HTML5 Canvas
- **Grid Size**: 20x20 cells (responsive sizing based on viewport)
- **Background**: Dark charcoal (#1a1a2e) with subtle grid lines (#16213e)
- **Border**: Neon glow effect around play area

### Color Palette
| Element | Color | Hex |
|---------|-------|-----|
| Background | Dark Navy | #1a1a2e |
| Grid Lines | Deep Blue | #16213e |
| Snake Head | Bright Lime | #00ff88 |
| Snake Body | Green Gradient | #00cc6a → #00994d |
| Food | Vibrant Red | #ff4757 |
| Score Text | White | #ffffff |
| UI Accent | Cyan | #00d4ff |
| Game Over | Red | #ff6b6b |

### Typography
- **Primary Font**: "Press Start 2P" (Google Fonts - retro arcade style)
- **Fallback**: monospace
- **Score Size**: 16px
- **Title Size**: 24px
- **Button Text**: 14px

### Visual Effects
- Snake head has slight glow/bloom effect
- Food pulses with subtle scale animation
- Game over screen fades in
- Smooth snake movement interpolation
- CRT scanline overlay effect (subtle)

---

## 3. Game Mechanics Specification

### Snake Behavior
- **Initial Length**: 3 segments
- **Initial Position**: Center of grid
- **Initial Direction**: Right
- **Movement**: Automatic, continuous in current direction
- **Growth**: +1 segment per food eaten
- **Collision with self**: Game Over

### Controls
- **Arrow Keys**: Up, Down, Left, Right
- **WASD Keys**: W (up), A (left), S (down), D (right)
- **Touch/Swipe**: Mobile swipe detection
- **Reverse Prevention**: Cannot reverse directly (e.g., moving right cannot instantly go left)

### Food Mechanics
- **Spawn**: Random empty grid cell
- **Appearance**: Red square with pulsing animation
- **Respawn**: Immediately after eating, in new random location

### Screen Wrap
- Snake exiting one edge appears on opposite edge
- Works for all 4 directions

### Scoring
- **Points per food**: 10 points
- **Display**: Top center of screen

### Speed/Difficulty
- **Initial Speed**: 150ms per move
- **Speed Increase**: -5ms per food eaten (minimum 50ms)
- **Formula**: `Math.max(50, 150 - (score / 10) * 5)`

---

## 4. Game States

### 1. Start Screen
- Title: "SNAKE" in large retro font
- Subtitle: "Press SPACE or Tap to Play"
- Animated snake demo (optional)
- High score display (if localStorage available)

### 2. Playing State
- Snake moves automatically
- Controls enabled
- Score updates in real-time
- Speed increases with score

### 3. Game Over State
- "GAME OVER" text displayed
- Final score shown
- "RESTART" button (clickable)
- "Press SPACE to Restart" text
- High score update (if applicable)

---

## 5. UI Components

### Score Display
- Position: Top center
- Format: "SCORE: XXX"
- Updates immediately on food collection

### Start Screen Overlay
- Semi-transparent dark background
- Centered title and instructions
- Animated prompt to start

### Game Over Overlay
- Semi-transparent dark background
- "GAME OVER" heading
- Final score
- Restart button
- High score (if applicable)

### Restart Button
- Styled as arcade button
- Hover effect with glow
- Click/tap to restart

---

## 6. Responsive Design

### Desktop
- Canvas: 400x400px minimum, scales up to 600x600px
- Keyboard controls primary
- Mouse hover effects on buttons

### Mobile
- Canvas: Full width with padding
- Touch swipe controls
- Larger touch targets for buttons
- Prevent default touch scrolling

---

## 7. Audio (Optional - Implementation Ready)
- Eat food sound
- Game over sound
- Background music loop (toggleable)
- Volume control (if implemented)

---

## 8. Technical Implementation

### File Structure
Single HTML file with embedded CSS and JavaScript for portability.

### Key Functions
```
- initGame()         // Initialize/reset game state
- gameLoop()         // Main game loop using setInterval
- update()           // Update snake position, check collisions
- render()           // Draw game state to canvas
- handleInput()      // Process keyboard/touch input
- spawnFood()        // Place food in random empty cell
- checkCollision()   // Check wall/self collision
- wrapPosition()     // Handle screen wrap
- gameOver()         // Handle game over state
- restart()          // Reset and start new game
```

### Data Structures
```javascript
snake = {
  segments: [{x, y}, ...],  // Array of {x, y} positions
  direction: {x, y},        // Current direction vector
  nextDirection: {x, y}     // Queued direction change
}

food = {x, y}               // Current food position

gameState = {
  status: 'start' | 'playing' | 'gameover',
  score: 0,
  highScore: 0,
  speed: 150
}
```

---

## 9. Acceptance Criteria

1. Snake moves automatically in current direction
2. Arrow keys and WASD change snake direction
3. Cannot reverse directly into yourself
4. Snake wraps around screen edges
5. Eating food: score increases, snake grows, new food spawns
6. Game ends when snake hits its own body
7. Game Over screen displays with restart option
8. Speed increases as score increases
9. Start screen shown on initial load
10. Responsive layout works on desktop and mobile
11. Retro arcade visual style applied
12. Clean, commented code

---

## 10. Browser Compatibility

- Modern browsers (Chrome, Firefox, Safari, Edge)
- HTML5 Canvas support required
- localStorage for high score persistence
- Touch events for mobile support
