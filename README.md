# Snake Game

A classic Snake game built with vanilla JavaScript, featuring obstacle rocks, background music, and sound effects.

## Features

- **Classic Snake Gameplay**: Control the snake using Arrow Keys or WASD
- **Screen Wrapping**: Snake wraps around the edges of the screen
- **Obstacle Rocks**: Random rocks spawn on the map - hitting them ends the game
- **Progressive Difficulty**: Speed increases as you eat more food
- **Background Music**: FNAF 8-bit remix plays during gameplay
- **Sound Effects**: Munch sound plays when eating food
- **High Score Tracking**: Scores are saved to localStorage
- **Mobile Support**: Touch/swipe controls for mobile devices
- **Responsive Design**: Works on various screen sizes

## Controls

- **Arrow Keys** or **WASD** - Move the snake
- **Space** - Start game / Restart after game over
- **Touch/Swipe** - Mobile controls

## Technologies Used

- **HTML5 Canvas** - Game rendering
- **CSS3** - Styling with retro arcade aesthetic
- **Vanilla JavaScript** - Game logic
- **Web Audio API** - Background music and sound effects
- **localStorage** - High score persistence
- **Vercel** - Deployment and hosting
- **GitHub** - Version control

## Deployment

The game is deployed on Vercel and accessible at:
https://snake-game-amber-three.vercel.app

## How to Play

1. Open the game in a browser
2. Press Space or click to start
3. Use arrow keys or WASD to control the snake
4. Eat the red food to grow and score points
5. Avoid hitting the rocks and your own tail
6. Speed increases as you eat more food

## Project Structure

```
├── index.html          # Main game file
├── music/              # Audio files
│   ├── Cartoon bite SFX.mp3
│   └── Five Nights at Freddy's Song (The Living Tombstone) 8-bit remix.mp3
├── vercel.json         # Vercel configuration
├── package.json        # Node.js dependencies
└── README.md           # This file
```

## Development

To run locally, simply open `index.html` in a web browser.

For development with live reload, you can use any local server:
```bash
python3 -m http.server 8080
# or
npx serve
```

## Credits

- Background Music: "Five Nights at Freddy's Song (The Living Tombstone) 8-bit remix"
- Sound Effect: "Cartoon bite SFX"
