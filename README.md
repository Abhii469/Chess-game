**Introduction

A **Chess Game** is a two-player strategy board game played on an 8x8 grid, where each player starts with 16 pieces: one King, one Queen, two Rooks, two Knights, two Bishops, and eight Pawns. The objective is to checkmate the opponent's King. In this project, you will develop a simple yet functional chess game using Java, implementing the essential rules and game logic.

Java is an ideal language for building a console or graphical chess game due to its rich set of libraries, object-oriented features, and portability. The game can be built with a text-based interface or enhanced with a GUI (Graphical User Interface) for better user experience.

### Key Features:
1. **Board Representation**: An 8x8 grid to represent the chessboard.
2. **Piece Movement**: Each piece (Pawn, Knight, Bishop, etc.) has specific movement rules. The game needs to handle these movements and capture.
3. **Game Rules**: Implementing basic rules like castling, en passant, and pawn promotion.
4. **Turn-Based Gameplay**: Alternating turns between two players.
5. **Check and Checkmate Detection**: Detecting when a player's king is in check and when the game ends in checkmate.
6. **Player Input**: Players can move pieces by specifying the source and destination squares.

---

### Working of the Chess Game Project in Java

The game can be divided into several components for easier management and understanding:

1. **Classes & Objects**:
   - **ChessBoard**: A class representing the chessboard. It will contain a 2D array of squares and the methods to set up the board and print it.
   - **Piece**: An abstract class representing a chess piece. It will have subclasses for each specific piece (Pawn, Knight, etc.). Each piece will have methods for validating its moves.
   - **Player**: A class that represents a player, which stores the player's name and color (black or white).
   - **MoveValidator**: A utility class to check whether a move is legal according to the rules of chess.
   - **Game**: The main class that handles game flow, turn alternation, and win conditions (checkmate, stalemate).

2. **Board Setup**:
   - The chessboard is an 8x8 grid where each piece is placed in its initial position. This can be done using a 2D array (e.g., `Piece[][] board`).
   
   ```java
   public class ChessBoard {
       private Piece[][] board;

       public ChessBoard() {
           board = new Piece[8][8];
           // Set up pieces in the initial positions
           setupBoard();
       }

       private void setupBoard() {
           // Add pieces to the board
           board[0][0] = new Rook(0, 0, "black");
           board[0][1] = new Knight(0, 1, "black");
           // Set other pieces similarly
       }
   }
   ```

3. **Piece Movement**:
   - Each piece will have specific rules for how it can move across the board. The movement logic will be implemented in each piece's class (for example, `Knight`, `Bishop`).
   
   ```java
   public class Knight extends Piece {
       @Override
       public boolean isValidMove(int startX, int startY, int endX, int endY) {
           int dx = Math.abs(endX - startX);
           int dy = Math.abs(endY - startY);
           return (dx == 2 && dy == 1) || (dx == 1 && dy == 2);
       }
   }
   ```

4. **Game Loop**:
   - The main game loop alternates turns between the players. Each player selects a piece to move and specifies the destination. After each move, the game checks for conditions like check, checkmate, or stalemate.
   
   ```java
   public class Game {
       private ChessBoard board;
       private Player player1;
       private Player player2;
       private boolean whiteTurn;

       public Game() {
           board = new ChessBoard();
           player1 = new Player("Player 1", "white");
           player2 = new Player("Player 2", "black");
           whiteTurn = true;
       }

       public void startGame() {
           while (true) {
               printBoard();
               Player currentPlayer = whiteTurn ? player1 : player2;
               System.out.println(currentPlayer.getName() + "'s turn");
               
               // Prompt for and handle move
               // validate move
               // Check for check/checkmate
               
               whiteTurn = !whiteTurn; // Alternate turns
           }
       }
   }
   ```

5. **Move Validation**:
   - Implement a method to check if the move is valid. For instance, for a pawn's move, check if the move is one square forward (or two squares on the first move) and ensure that captures are made diagonally.
   - Also, ensure that the move does not put the player's own king in check.

6. **Endgame Detection**:
   - The game needs to detect check and checkmate conditions. If a player's king is in check and they cannot make a legal move, the game ends in checkmate. If no pieces can be moved and no check exists, it's a stalemate.

7. **Player Input**:
   - The game could take input in the form of coordinates (e.g., "e2 to e4") or using a GUI interface. For console-based input, you'd use `Scanner` to take in coordinates for the move and then process the move.

8. **Game Loop**:
   - The game continues in a loop until one of the players wins (checkmate), or it ends in a draw (stalemate).

---

### Conclusion

The chess game project in Java helps to practice object-oriented principles by breaking down the complex game into manageable classes, such as pieces, board, and players. It also teaches about handling game logic, movement rules, and alternate turns. The project can be extended with features like a GUI, AI opponent, and more sophisticated move validation.





# Java Chess Game Project

## Overview
A Java-based chess game for two players, featuring a graphical user interface and enforcing standard chess rules.

## Initial Game State:

![Board Layout](./img/figure1.png)

## Features
- **Graphical User Interface:** A simple and intuitive GUI for user interaction.
- **Board Initialization:** The chessboard initializes with pieces in the standard starting positions.
- **Piece Movement:** Players can move pieces by clicking on the board's squares.
- **Game Status:** The application includes a status bar to indicate which player's turn it is and to display messages like "Check" or "Checkmate".
- **Reset Functionality:** A reset button allows players to start a new game at any point.

## Getting Started
### Prerequisites
- Java Runtime Environment (JRE) or Java Development Kit (JDK)

### Running the Application

1. Compile the ChessBoard.java file:
    ```bash
    javac ChessBoard.java
    ```

2. Run the compiled class:
    ```bash
    java ChessBoard
    ```

## Gameplay Guide

- **Selecting Pieces:** Click on a piece to see possible moves highlighted.
- **Making Moves:** Click on a highlighted square to move the selected piece.
- **Check/Checkmate Detection:** The game automatically detects and announces check and checkmate scenarios.
- **Turn Notification:** Each player's turn is clearly indicated.

## Behind the Scenes
- **Board Representation:** An 8x8 grid of buttons represents the chessboard.
![Initial Game State](./img/figure2.png)
- **Piece Representation:** Each piece is an instance of the Piece class with a type and color.
- **Game Logic:** Custom methods define the rules for piece movement and capture.
- **Endgame Conditions:** The game detects stalemate, check, and checkmate conditions, concluding the game accordingly.

## Extending the Game
- **Customization:** The GUI can be customized with different themes or piece sets.
- **Enhancements:** Additional features like move history, undo/redo, and AI opponents can be added.

*Visit the repository for the complete code and more information.*
