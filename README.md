# Solo Red Game

## Introduction
Welcome to **Solo Red**, a solitaire variation of the Red7 card game! The challenge is simple yet strategic: maintain a winning palette under constantly changing rules dictated by the color of the top card on the canvas. As the game progresses, you’ll need to carefully play your cards to your palette or the canvas to stay ahead.

This project was developed over three assignments, creating a fully playable, text-based Solitaire Red experience with multiple game modes.

---

## Game Overview

### **Cards**
The game uses a custom deck of 35 cards, each defined by:
- **Color:** Red (R), Orange (O), Blue (B), Indigo (I), Violet (V)
- **Number:** An integer between 1 and 7

Cards are represented as two-character codes:
- Example: `R3` (Red 3), `B1` (Blue 1), `V7` (Violet 7)

### **Game Structures**
- **Deck:** The draw pile of cards.
- **Palettes:** Collections of face-up cards manipulated by players. The number of palettes is chosen at the start.
- **Canvas:** A single face-up card that determines the current rule for winning.
- **Hand:** A private set of cards used to play to palettes or the canvas.

---

## Starting the Game

When you run the game from the command line, all setup steps are performed automatically by the model. This includes:

1. **Creating palettes:** One card from the deck is automatically placed face-up on each palette.
2. **Initializing the canvas:** The canvas is set to Red initially, establishing the first rule without using a card from the deck.
3. **Filling your hand:** Cards are automatically drawn from the deck until your hand reaches the specified maximum size, or the deck runs out of cards.

You do not need to manually perform these steps; simply start the game (as described in the "Running the Game" section) and the model handles all of this for you.

---

## Winning Rules
The color on the canvas determines the current winning condition:

- **Red:** The palette with the highest card wins (ranked first by number, then by color: R > O > B > I > V).
- **Orange:** The palette with the most cards of the same number wins.
- **Blue:** The palette with the most differently colored cards wins.
- **Indigo:** The palette with the longest run of consecutive numbers (e.g., 4-5-6) wins.
- **Violet:** The palette with the most cards valued below 4 wins.

If there’s a tie, it’s resolved using Red-rule logic (highest card).

---

## Gameplay

### **Your Turn**
On your turn, you must:
1. Either:
    - Play one card from your hand onto a losing palette, **or**
    - Play one card to the canvas (changing the rule), then play another card onto a losing palette.
2. After making a palette win, draw cards from the deck until your hand is full (or the deck is empty).

**Important:** If you cannot make a losing palette win by the end of your turn, you lose.

---

## Ending the Game
The game ends when:
- **You lose:** You cannot make a losing palette win.
- **You win:** Your hand and deck are empty, but you’re currently winning.

---

## Variants
In the **Advanced Variant**:
- After playing to a palette, you draw only **one card** (if available).
- If you play a card to the canvas with a number greater than the size of the winning palette, you draw **two cards** after playing to a palette.

---

## Running the Game
1. Compile all the code.
2. Run the `SoloRed` class with one of these commands:
    - `basic` — Starts Basic Solo Red with default settings (4 palettes, hand size 7).
    - `basic 4 7` — Explicitly sets 4 palettes and hand size 7.
    - `advanced 8` — Starts Advanced Solo Red with 8 palettes and default hand size.
    - `advanced 7 8` — Sets 7 palettes and hand size 8.

### **Controls**
- **Play to a palette:** `palette <palette-index> <hand-index>`
- **Play to the canvas:** `canvas <hand-index>`
- **Quit:** Type `q` or `Q`.

---

## Testing

Comprehensive tests are provided. Tests for both the basic and advanced models ensure correctness and adherence to specifications.

You can run these tests using **JUnit** in your IDE or from the command line.

---

## Implementation Notes
- **Packages:**
    - `cs3500.solored.model.hw02:` Basic model (`SoloRedGameModel`) and card representation.
    - `cs3500.solored.view.hw02:` Text-based view (`SoloRedGameTextView`).
    - `cs3500.solored.controller:` Controller (`SoloRedTextController`).
    - `cs3500.solored.model.hw04:` Advanced model (`AdvancedSoloRedGameModel`).

- **Key Interfaces:**
    - `RedGameModel:` Defines the game’s behavior.
    - `RedGameController:` Handles game logic.
    - `RedGameView:` Manages game state display.

- **Factory Class:** The `RedGameCreator` factory class helps create the Basic or Advanced version of the game.

---

## Conclusion
Solo Red combines strategy and adaptability under dynamic rules, challenging players to think critically and stay ahead. With MVC architecture and support for both basic and advanced modes, the project demonstrates well-structured, extensible code.

Enjoy the game and happy strategizing!
