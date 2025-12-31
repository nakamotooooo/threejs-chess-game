# 3D Chess Game

A beautiful, fully interactive 3D chess game built with Three.js, featuring realistic piece models, smooth animations, and an AI opponent.

![3D Chess Game](https://img.shields.io/badge/Three.js-r128-blue) ![Chess.js](https://img.shields.io/badge/Chess.js-0.10.3-green) ![Status](https://img.shields.io/badge/Status-Playable-success)

## Features

### 🎮 Gameplay
- **Full Chess Rules**: Complete implementation of standard chess rules including castling, en passant, and pawn promotion
- **AI Opponent**: Play against a computer that makes strategic moves and prioritizes captures
- **Turn-Based Play**: Clear turn indicators with "White's Turn" / "Black's Turn" / "Check!" / "Checkmate!" status
- **Legal Move Highlighting**: Click any piece to see all legal moves highlighted in cyan
- **Capture Detection**: Captured pieces are displayed on side trays for both players

### 🎨 Visual Design
- **3D Chess Pieces**: High-quality GLTF models for all piece types (Pawn, Rook, Knight, Bishop, Queen, King)
- **Realistic Board**: Wooden texture materials with light and dark squares
- **Professional Lighting**: Ambient lighting combined with shadow-casting spotlight
- **Smooth Shadows**: Soft PCF shadows for realistic depth
- **Elegant UI**: Classic wood-themed interface with gradient status display

### 🛠️ Technical Features
- **OrbitControls**: Rotate, zoom, and pan the camera to view from any angle
- **Interactive Raycasting**: Precise click detection on pieces, squares, and highlights
- **Debug Mode**: Real-time GUI controls to adjust piece scale and elevation
- **Responsive Design**: Automatically adjusts to window resizing
- **Asset Loading**: Graceful fallback if models fail to load

## How to Play

### Basic Controls
1. **Select a Piece**: Click on any white piece during your turn
2. **View Legal Moves**: Valid destination squares will be highlighted in cyan
3. **Make a Move**: Click on any highlighted square to move there
4. **Capture**: Click on opponent pieces if they're in valid move range
5. **Camera**: Left-click drag to rotate, right-click drag to pan, scroll to zoom

### Game Flow
- White always moves first
- After each move, the AI (playing as Black) will automatically respond
- The game detects check, checkmate, and draw conditions
- Use the "Reset Game" button to start a new match

## Installation & Setup

### Prerequisites
The game requires the following assets in an `assets/` folder:
- `pawn.glb`
- `rook.glb`
- `knight.glb`
- `bishop.glb`
- `queen.glb`
- `king.glb`

### Running the Game
1. Place all `.glb` model files in the `assets/` directory
2. Open `index.html` in a modern web browser (Chrome, Firefox, Safari, Edge)
3. Wait for models to load (loading screen will disappear when ready)
4. Start playing!

**Note**: Due to CORS restrictions, you may need to run a local web server:
```bash
# Python 3
python -m http.server 8000

# Node.js
npx http-server

# Then open http://localhost:8000
```

## Debug Mode

The game includes a DAT.GUI panel for real-time adjustments:

### Controls
- **Size (Scale)**: Adjust piece size from 0.01 to 3.0 (default: 0.05)
- **Elevation (Y)**: Adjust piece height from -1.0 to 1.0 (default: 0.26)

These controls are useful for:
- Fine-tuning visual appearance
- Adapting to different model sizes
- Experimenting with board aesthetics

## Technical Architecture

### Core Technologies
- **Three.js (r128)**: 3D rendering engine
- **Chess.js (0.10.3)**: Chess game logic and rules validation
- **OrbitControls**: Camera manipulation
- **GLTFLoader**: 3D model loading
- **DAT.GUI**: Debug interface

### Key Components

#### Scene Setup
```javascript
- Scene with dark background
- Perspective camera (45° FOV)
- WebGL renderer with shadows
- Ambient + spotlight lighting
```

#### Board Representation
- 8×8 grid of squares (2×2 units each)
- Alternating light/dark wood materials
- Border frame for aesthetic appeal
- Side trays for captured pieces

#### Interaction System
- Raycasting for click detection
- Multi-level object traversal for GLTF models
- Highlight system for legal moves
- Turn-based input validation

## Configuration

### Adjustable Settings
```javascript
const debugSettings = {
    pieceScale: 0.05,      // Default piece size
    pieceElevation: 0.26,  // Height above board
    knightRotation: 90     // Knight facing angle
};
```

### Board Dimensions
```javascript
const SQUARE_SIZE = 2;           // Size of each square
const OFFSET = -3.5 * SQUARE_SIZE; // Board centering
```

## Game Logic

### Move Validation
- All moves validated through Chess.js library
- Automatic check/checkmate detection
- Pawn promotion (automatically promotes to Queen)
- Special moves (castling, en passant) fully supported

### AI Strategy
- Random move selection from legal moves
- Prioritizes captures when available
- 500ms thinking delay for realistic feel

## Browser Compatibility

**Tested and Working:**
- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

**Requirements:**
- WebGL support
- ES6 JavaScript support
- Modern browser with shadow mapping

## Performance

- **Target**: 60 FPS
- **Shadow Quality**: 2048×2048 shadow maps
- **Anti-aliasing**: Enabled
- **Optimization**: Efficient model instancing and material reuse

## Troubleshooting

### Models Not Loading
- Check that all `.glb` files are in the `assets/` folder
- Verify file names match exactly (case-sensitive)
- Run from a web server, not `file://` protocol
- Check browser console for specific errors

### Pieces Not Clickable
- Open browser console (F12) to see click detection logs
- Ensure pieces have loaded completely
- Try adjusting camera angle if pieces are obstructed
- Verify it's White's turn (only White pieces are clickable initially)

### Performance Issues
- Reduce shadow quality in code (lower `shadow.mapSize`)
- Disable anti-aliasing in renderer settings
- Close unnecessary browser tabs
- Update graphics drivers

## Future Enhancements

Potential features for future versions:
- [ ] Multiplayer mode (local or online)
- [ ] Difficulty levels for AI
- [ ] Move history and undo functionality
- [ ] Timer/clock for timed games
- [ ] Opening book for AI
- [ ] Save/load game state
- [ ] Alternative board themes
- [ ] Sound effects for moves
- [ ] Animated piece movements
- [ ] Advanced AI using minimax algorithm

## Credits

### Libraries
- [Three.js](https://threejs.org/) - 3D graphics library
- [Chess.js](https://github.com/jhlywa/chess.js) - Chess logic
- [DAT.GUI](https://github.com/dataarts/dat.gui) - Debug interface

### Models
3D chess piece models should be obtained from appropriate sources with proper licensing.

## License

This project is open source and available for educational purposes.

## Contributing

Contributions are welcome! Areas for improvement:
- Enhanced AI algorithms
- Additional visual themes
- Performance optimizations
- Mobile touch support
- Accessibility features

---

**Enjoy the game!** ♔♕♖♗♘♙

For issues or questions, please check the browser console for debug information.