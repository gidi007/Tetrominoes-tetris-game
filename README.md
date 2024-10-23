# 🎮 Simple Tetris Implementation

A lightweight, browser-based Tetris implementation focusing on core game mechanics. Built with vanilla JavaScript and HTML5 Canvas.

## 🚀 Features

- Pure JavaScript implementation
- HTML5 Canvas rendering
- Efficient piece rotation system
- Classic Tetris gameplay mechanics
- Performance-optimized rendering
- Keyboard controls

## 🎯 Core Game Components

### Tetromino Implementation

The game uses an innovative bit-based representation for tetrominoes. Each piece is represented as a 4x4 grid using 16-bit integers:

```javascript
const TETROMINOES = {
  i: { blocks: [0x0F00, 0x2222, 0x00F0, 0x4444], color: 'cyan'   },
  j: { blocks: [0x44C0, 0x8E00, 0x6440, 0x0E20], color: 'blue'   },
  l: { blocks: [0x4460, 0x0E80, 0xC440, 0x2E00], color: 'orange' },
  o: { blocks: [0xCC00, 0xCC00, 0xCC00, 0xCC00], color: 'yellow' },
  s: { blocks: [0x06C0, 0x8C40, 0x6C00, 0x4620], color: 'green'  },
  t: { blocks: [0x0E40, 0x4C40, 0x4E00, 0x4640], color: 'purple' },
  z: { blocks: [0x0C60, 0x4C80, 0xC600, 0x2640], color: 'red'    }
};
```

### 🎲 Piece Randomization

The game implements a "bag" system for piece selection:
- Maintains a bag of 4 instances of each piece
- Randomly draws pieces until the bag is empty
- Ensures fair piece distribution
- Prevents long sequences of the same piece

### 🎮 Controls

```
← → : Move piece left/right
↑   : Rotate piece
↓   : Soft drop
ESC : Quit game
SPACE: Start new game
```

## 🔧 Technical Implementation

### Game Loop

The game uses `requestAnimationFrame` for smooth animation:

```javascript
function gameLoop() {
    const now = timestamp();
    update((now - last) / 1000.0);
    draw();
    last = now;
    requestAnimationFrame(gameLoop);
}
```

### Rendering Optimization

Implements an intelligent invalidation system:
- Only redraws changed components
- Tracks four distinct areas:
  - Game court
  - Score display
  - Row count
  - Next piece preview
- Uses canvas translation for crisp rendering

### Core Game Constants

```javascript
const GAME_SETTINGS = {
    COURT_WIDTH: 10,    // Width in blocks
    COURT_HEIGHT: 20,   // Height in blocks
    PREVIEW_SIZE: 5,    // Size of next piece preview
    STARTING_SPEED: 0.6 // Initial drop speed (seconds)
};
```

## 🔄 Game Flow

1. Player starts game (Space)
2. Game initializes with:
   - Empty court
   - Random current piece
   - Random next piece
   - Score = 0
   - Rows = 0
3. Each frame:
   - Process player input
   - Update piece positions
   - Check for completed lines
   - Update score
   - Render changes

## 🎯 Scoring System

- 10 points per piece drop
- Additional points for completed lines
- Speed increases with completed rows

## 🛠️ Future Improvements

- [ ] Menu system
- [ ] Level progression
- [ ] High score tracking
- [ ] Animations and effects
- [ ] Sound effects and music
- [ ] Touch screen support
- [ ] Multiplayer capabilities
- [ ] AI opponent

## 🔍 Technical Notes

- Collision detection uses efficient bit operations
- Piece rotation handles edge cases automatically
- Rendering optimized for performance
- Canvas used for smooth graphics
- Modular code structure for easy expansion

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---
Gideon Bawa (fullstack dev)

Built with ❤️ for the love of classic gaming