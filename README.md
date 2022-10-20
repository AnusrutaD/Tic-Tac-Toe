# Design Tic-Tac-Toe

## What is Tic-Tac-Toe?

TicTacToe is a 2 player game played on a 3 x 3 board. Each player is allotted a symbol (one X and one O). Initially, the board is empty. Alternatively, each player takes a turn and puts their symbol at any empty slot. The first player to get their symbol over a complete row OR a complete column OR a diagonal wins.

You can play the game within Google Search by just searching for “tictactoe”!

![TicTacToe](https://www.tuitec.com/wp-content/uploads/2016/08/morpion-640x411.jpg)


## Overview
## Clarifications 
## Overview
## Entities
1. Game
2. Board - N X M
3. Cell
4. Player - 2 Players 
   1. Human Player 
   2. Bot Player
      1. DifficultyLevel
5. Symbol - O, X
## Class Diagram
## Implementation
* Create a CLI or API

## Requirements
* Current Scope
  * Size of the board
  * 2 Player or many?
* Future Scope
  * Can there be multiple ways to win the game
* Behavior
  * Can a player play with a Bot?
  * How does a player win?
  * Who starts the game?

## Design
### Use case Diagram
```puml
@startuml
left to right direction
actor HumanPlayer
actor BotPlayer
rectangle game{
  HumanPlayer -- (Register)
  HumanPlayer -- (Start Game)
  HumanPlayer -- (Make Move)
  BotPlayer -- (Make Move)
  (Make Move) >. (Check Winner) : include
}
@enduml
```

```mermaid
classDiagram
    class Game{
        -Board board
        -HumanPlayer humanPlayer
        -BotPlayer botPlayer
        +Register(HumanPlayer) HumanPlayer
        +startGame(HumanPlayer, BotPlayer, int row, int column) Board
        +makeMove(int playerId, int x, int y) Board
        +checkWinner(Board, HumanPlayer, BotPlayer) int
    }
    class Board{
        -int row
        -int column
        -Cell[][] cells
        +createBoard(row, column) Board
    }
    class Cell{
        -int x
        -int y
        -Symbol symbol
    }
    class Symbol{
        -char O/X 
    }
    class HumanPlayer{
        -String name
        -String email
        -byte[] photo
        -Symbol symbol
        +Play(Board) cell
    }
    class BotPlayer{
        -int id
        -Level level
        -Symbol symbol
        +Play() void
    }
    class Level{
        -int level
    }
    Game "1" --* "1" Board
    Board "1" --* "m" Cell
    Game "1" --* "1" HumanPlayer
    Game "1" --* "1" BotPlayer
    Cell "1" --* "1" Symbol
    HumanPlayer "1" --* "1" Symbol
    BotPlayer "1" --* "1" Symbol
    BotPlayer "1" --* "1" Level
```

## Common Contract - Player Abstract class
- Common Behaviour - `play()`
- common Attribute - `symbol`

## Tight coupling
- HumanPlayer
- BotPlayer
- Player[] players

## OCP and SRP violation in play method

## Huge memory consumption
