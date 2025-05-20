 from random import randint

board = [] #empty list

for x in range(4):
    board.append(["O"] * 4) #Add "O" to board

def print_board(board):
    for row in board:
        print (" ".join(row)) #Defines conjunction between O's

print ("Let's play Battleship!")
print_board(board)

def random_row(board):
    return randint(0, len(board) - 1)

def random_col(board):
    return randint(0, len(board[0]) - 1)

ship_row = random_row(board)
ship_col = random_col(board)

for turn in range(10): #Defines number of turns
    guess_row = int(input("Guess Row:"))-1
    guess_col = int(input("Guess Col:"))-1

    if guess_row == ship_row and guess_col == ship_col:
        print ("Congratulations! You sunk my battleship!")
        break
    else:
        if (guess_row < 0 or guess_row > 4) or (guess_col < 0 or guess_col > 4):
            print ("Oops, that's not even in the ocean.")
        elif(board[guess_row][guess_col] == "X"):
            print ("You guessed that one already.")
        else: 
            print ("You missed my battleship!")
            board[guess_row][guess_col] = "X"
    
    print ("Turn", turn + 1)
    print_board(board)
    if turn == 4: #defines number of turns to guess
        print ("Game Over")
        print ("The row where the ship used to be is: ", ship_row) #to know ship's ccords
        print ("The rocolumn where the ship used to be is: ", ship_col)
