---
title: "Building a Tic Tac Toe Game with AI: Learn How to Create an Intelligent Player That Never Loses!"
datePublished: Mon Apr 24 2023 09:30:39 GMT+0000 (Coordinated Universal Time)
cuid: clgun1afe05vk72nv0xdl20l5
slug: building-a-tic-tac-toe-game-with-ai-learn-how-to-create-an-intelligent-player-that-never-loses
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1682169437386/c47064ed-99da-4ecb-9920-9eed08a13ad5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1682169483701/b197955a-55a1-44ad-a125-0a9284bce687.png
tags: ai, robots, wemakedevs, mayankaggarwal, mayank

---

# Introduction:

Tic Tac Toe is a classic game that can be played between two players. However, it's also possible to build an AI controlled Tic Tac Toe game that can play against a human player. In this blog post, we will learn how to build an AI controlled Tic Tac Toe game using Python and Pygame library. We will be using the minimax algorithm to create the AI.

## Technologies Used:

To create this game, we will be using the following technologies:

* Python as the programming language
    
* Pygame library, which is a set of Python modules designed for writing video games.
    

## Steps to Build the Game:

We will be building the AI controlled Tic Tac Toe game in the following steps:

1. Setting up the Game Window
    
2. Drawing the Game Board
    
3. Handling User Input
    
4. Creating the AI using the minimax algorithm
    
5. Making the AI Move
    
6. Running the Game
    

### Step 1: Setting up the Game Window

The first step is to set up the game window. We will be using Pygame to create the game window. Here's the code for setting up the game window:

```python
import pygame

pygame.init()

WINDOW_SIZE = (600, 600)
screen = pygame.display.set_mode(WINDOW_SIZE)
pygame.display.set_caption("Tic Tac Toe")
```

In the above code, we import the Pygame library and initialize it. We also set the size of the game window to 600x600 pixels and set the caption of the game window to "Tic Tac Toe".

### Step 2: Drawing the Game Board

Next, we need to draw the game board. Here's the code for drawing the game board:

```python
def draw_board():
    for row in range(3):
        for col in range(3):
            pygame.draw.rect(screen, (255, 255, 255), (col * 200, row * 200, 200, 200), 2)
```

In the above code, we use Pygame to draw a 3x3 grid on the game window. We loop through all the cells of the grid and draw a rectangle for each cell.

### Step 3: Handling User Input

Next, we need to handle user input. Here's the code for handling user input:

```python
def handle_input():
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
        elif event.type == pygame.MOUSEBUTTONDOWN:
            row = event.pos[1] // 200
            col = event.pos[0] // 200
            make_move(row, col)
```

In the above code, we use Pygame to handle mouse clicks on the game window. When the user clicks on a cell of the game board, we calculate the row and column of the cell and call the make\_move() function to make the move.

### Step 4: Creating the AI using the minimax algorithm

To create the AI, we will be using the minimax algorithm. The minimax algorithm is a decision-making algorithm that is used in game theory to find the optimal move for a player, assuming that the other player is also playing optimally.

Here's the code for the minimax algorithm:

```python
def minimax(board, depth, maximizing_player):
    if check_winner(board) == "X":
        return -1
    elif check_winner(board) == "O":
        return 1
    elif check_draw(board):
        return 0

    if maximizing_player:
        max_eval = float("-inf")
        for row in range(3):
            for col in range(3):
                if board[row][col] is None:
                    board[row][col] = "O"
                    eval = minimax(board, depth + 1, False)
                    board[row][col] = None
                    max_eval = max(max_eval, eval)
        return max_eval
    else:
        min_eval = float("inf")
        for row in range(3):
            for col in range(3):
                if board[row][col] is None:
                    board[row][col] = "X"
                    eval = minimax(board, depth + 1, True)
                    board[row][col] = None
                    min_eval = min(min_eval, eval)
        return min_eval
```

In the above code, we use recursion to simulate all possible moves that can be made by the AI and the human player. We evaluate each move by assigning a score to it. If the AI wins, it gets a score of 1, and if the human player wins, it gets a score of -1. If the game is a draw, the score is 0. We assume that the AI is the maximizing player and the human player is the minimizing player.

### Step 5: Making the AI Move

Now that we have the AI algorithm, we need to make the AI move. Here's the code for making the AI move:

```python
def make_ai_move():
    best_move = None
    best_score = float("-inf")
    for row in range(3):
        for col in range(3):
            if board[row][col] is None:
                board[row][col] = "O"
                score = minimax(board, 0, False)
                board[row][col] = None
                if score > best_score:
                    best_score = score
                    best_move = (row, col)
    row, col = best_move
    board[row][col] = "O"
```

In the above code, we loop through all possible moves and evaluate each move using the minimax algorithm. We then select the move with the highest score and make the AI move.

### Step 6: Running the Game

Finally, we need to run the game. Here is the complete code for the game:

```python
import pygame

pygame.init()

WINDOW_SIZE = (600, 600)
screen = pygame.display.set_mode(WINDOW_SIZE)
pygame.display.set_caption("Tic Tac Toe")

board = [[None, None, None],
         [None, None, None],
         [None, None, None]]

def draw_board():
    for row in range(3):
        for col in range(3):
            pygame.draw.rect(screen, (255, 255, 255), (col * 200, row * 200, 200, 200), 2)

def handle_input():
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
        elif event.type == pygame.MOUSEBUTTONDOWN:
            row = event.pos[1] // 200
            col = event.pos[0] // 200
            make_move(row, col)

def check_winner(board):
    for row in range(3):
        if board[row][0] == board[row][1] == board[row][2] and board[row][0] is not None:
            return board[row][0]
    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] and board[0][col] is not None:
            return board[0][col]
    if board[0][0] == board[1][1] == board[2][2] and board[0][0] is not None:
        return board[0][0]
    if board[0][2] == board[1][1] == board[2][0] and board[0][2] is not None:
        return board[0][2]
    if all([all(row) for row in board]):
        return "DRAW"
    return None

def make_move(row, col):
    if board[row][col] is not None:
        return
    board[row][col] = "X"
    winner = check_winner(board)
    if winner is not None:
        print(winner)
        pygame.quit()
        sys.exit()
    make_ai_move()
    winner = check_winner(board)
    if winner is not None:
        print(winner)
        pygame.quit()
        sys.exit()

def minimax(board, depth, is_maximizing):
    winner = check_winner(board)
    if winner is not None:
        if winner == "X":
            return -1
        elif winner == "O":
            return 1
        else:
            return 0
    if is_maximizing:
        max_eval = float("-inf")
        for row in range(3):
            for col in range(3):
                if board[row][col] is None:
                    board[row][col] = "O"
                    eval = minimax(board, depth + 1, False)
                    board[row][col] = None
                    max_eval = max(max_eval, eval)
        return max_eval
    else:
        min_eval = float("inf")
        for row in range(3):
            for col in range(3):
                if board[row][col] is None:
                    board[row][col] = "X"
                    eval = minimax(board, depth + 1, True)
                    board[row][col] = None
                    min_eval = min(min_eval, eval)
        return min_eval

def make_ai_move():
    best_move = None
    best_score = float("-inf")
    for row in range(3):
        for col in range(3):
            if board[row][col] is None:
                board[row][col] = "O"
                score = minimax(board, 0, False)
                board[row][col] = None
                if score > best_score:
                    best_score = score
                    best_move = (row, col)
    row, col = best_move
    board[row][col] = "O"

while True:
    draw_board()
    handle_input()
    pygame.display.update()
```

  
In the make\_move function, we first make the human player's move and then check if there is a winner. If there is a winner, we print the winner and exit the game. We then make the AI move and check if there is a winner again. If there is a winner, we print the winner and exit the game. Finally, we create a game loop that draws the board, handles user input, and updates the display. This loop runs indefinitely until the game is exited by the user.

### Conclusion

In this tutorial, we have created a Tic Tac Toe game with an AI opponent that uses the Minimax algorithm to make its moves. We used the Pygame library to create the game window and draw the game board.

We first created a function to draw the board on the game window, and then we handled user input to allow the human player to make their moves. We then created the `check_winner` function to check if there is a winner after every move.

Next, we created the `minimax` function to calculate the score of each possible move for the AI opponent. The `minimax` function uses recursion to simulate every possible move and calculates the score using the Minimax algorithm.

Finally, we created the `make_ai_move` function to make the AI move based on the score calculated by the `minimax` function. We then added the `make_move` function to make the human player move and check for a winner, and we updated the `make_ai_move` function to check for a winner after making the AI move.

We then created the game loop to draw the board, handle user input, and update the display until the game is exited by the user.

Overall, this tutorial demonstrates how to create a simple game with an AI opponent using the Minimax algorithm. However, there are several ways to improve the game, such as adding difficulty levels, improving the AI algorithm, and creating a more user-friendly interface.

## Full Code

```python
import pygame
import sys

# Initialize Pygame
pygame.init()

# Set window size and caption
WINDOW_SIZE = (300, 300)
WINDOW_CAPTION = "Tic Tac Toe with AI"
screen = pygame.display.set_mode(WINDOW_SIZE)
pygame.display.set_caption(WINDOW_CAPTION)

# Set up game variables
board = [[None, None, None], [None, None, None], [None, None, None]]
player = "X"

# Define colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)

# Set up font
FONT_SIZE = 50
font = pygame.font.SysFont(None, FONT_SIZE)

def draw_board():
    # Draw grid lines
    pygame.draw.line(screen, BLACK, (100, 0), (100, 300), 2)
    pygame.draw.line(screen, BLACK, (200, 0), (200, 300), 2)
    pygame.draw.line(screen, BLACK, (0, 100), (300, 100), 2)
    pygame.draw.line(screen, BLACK, (0, 200), (300, 200), 2)

    # Draw X's and O's
    for row in range(3):
        for col in range(3):
            if board[row][col] == "X":
                x_pos = col * 100 + 50
                y_pos = row * 100 + 50
                x = font.render("X", True, BLACK)
                x_rect = x.get_rect(center=(x_pos, y_pos))
                screen.blit(x, x_rect)
            elif board[row][col] == "O":
                x_pos = col * 100 + 50
                y_pos = row * 100 + 50
                o = font.render("O", True, BLACK)
                o_rect = o.get_rect(center=(x_pos, y_pos))
                screen.blit(o, o_rect)

def handle_input():
    global player
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
        elif event.type == pygame.MOUSEBUTTONDOWN:
            x, y = pygame.mouse.get_pos()
            row = y // 100
            col = x // 100
            make_move(row, col)

def check_winner(board):
    for row in range(3):
        if board[row][0] == board[row][1] == board[row][2] and board[row][0] is not None:
            return board[row][0]
    for col in range(3):
        if board[0][col] == board[1][col] == board[2][col] and board[0][col] is not None:
            return board[0][col]
    if board[0][0] == board[1][1] == board[2][2] and board[0][0] is not None:
        return board[0][0]
    if board[0][2] == board[1][1] == board[2][0] and board[0][2] is not None:
        return board[0][2]
    if all([all(row) for row in board]):
        return "DRAW"
    return None

def make_move(row, col):
    global board, player
    board[row][col] = player
    if check_winner(board):
        winner = check_winner(board)
        print(f"{winner} wins!")
        reset_game()
    elif check_draw(board):
        print("It's a draw!")
        reset_game()
    else:
        player = "X" if player == "O" else "O"
def get_best_move(board):
    best_move = None
    best_score = -float("inf")
    for row in range(3):
        for col in range(3):
            if board[row][col] is None:
                board[row][col] = "O"
                score = minimax(board, False)
                board[row][col] = None
                if score > best_score:
                    best_score = score
                    best_move = (row, col)
    return best_move

def minimax(board, is_maximizing):
    winner = check_winner(board)
    if winner == "O":
        return 1
    elif winner == "X":
        return -1
    elif winner == "DRAW":
        return 0

    if is_maximizing:
        best_score = -float("inf")
        for row in range(3):
            for col in range(3):
                if board[row][col] is None:
                    board[row][col] = "O"
                    score = minimax(board, False)
                    board[row][col] = None
                    best_score = max(score, best_score)
        return best_score
    else:
        best_score = float("inf")
        for row in range(3):
            for col in range(3):
                if board[row][col] is None:
                    board[row][col] = "X"
                    score = minimax(board, True)
                    board[row][col] = None
                    best_score = min(score, best_score)
        return best_score

def main():
    global player
    while True:
        draw_board()
        handle_input()
        if player == "O":
            row, col = get_best_move(board)
            make_move(row, col)
        pygame.display.update()

if __name__ == "__main__":
    main()
```

> Make Sure to follow me on [**hashnode**](https://blog.mayankaggarwal.live/).
> 
> Having any Querry? [**Ask me**](https://mayankaggarwal.live/).