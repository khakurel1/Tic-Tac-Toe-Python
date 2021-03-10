# Tic-Tac-Toe-Pythonn


#let's display on the screeen to let the user know what this program does
print("Hello!!! Here is a Tic Tac Toe for you. Enjoy playing.")

#just to push the next printing code one line down
print()

#makeBoard Function is used to return a list of lists with numbers in them in order to create a tic tac toe board whenever necessary.
def makeBoard():
  'Make a Tic Tac Toe board as a 3x3 list of ints'
  return([[1,2,3],[4,5,6],[7,8,9]])

#displayBoard function is used to create a tic tac toe board on the screen it used board function as an argument.
def displayBoard(board):
  'Display a Tic Tac Toe board'
  for r in range(3):
    for c in range(3):
      if c>0: print("|",end="")
      print(board[r][c],end="")
    print()
    if r<2: print("-----")

#this function returns you the position of a given number. It is later used to get the position of the number entered by the user
def getLoc(n):
  'Given an int between 1 and 9, return the row and column'
  if int(n) == 1:
    return 0,0
  if int(n) == 2:
    return 0,1
  if int(n) ==3:
    return 0,2  # This is 3
  if int(n) == 4:
    return 1,0
  if int(n) == 5:
    return 1,1
  if int(n) ==6:
    return 1,2
  if int(n) == 7:
    return 2,0
  if int(n) == 8:
    return 2,1
  if int(n) ==9:
    return 2,2 

#getMove function is used to ask the specific user ("X" or "O" in this case) to enter the position of the move they want to make. This function works with checkMove function in order to check if the input from the user is legal move.
def getMove(board,player):
  while True:
    b = input("Player  " + str(player) + "  enter a move: ")
    if checkMove(board,b) == True:
      return int(b)
    else:
      continue

  '''
  given a board and a player letter, ask for and  check a legal move
  move must be between 1 and 9
  player should be an "X" or "O"
  Don't return until they input  proper move that is not taken
  '''


#checkMove function is used to check if the user input data is a legal move or not. if it is a legal move and the game runs smoothly, if it is not it akss the user to input again letting them know why it is not a legal move 
def checkMove(board,m):

  '''
  Given a board and a move (1-9), return True is move is in range
  and if that location is available
  '''
  for i in range(len(m)):
      if m[i].isdigit()== False:
        print("Move must be a number!")

    #print("Move must be a number!")
        return False 

      else:
        if int(m)<1 or int(m)>9:
          print("Move must be in range 1-9!")
          return False
        else:
          r,c=getLoc(m)
    #print(r,c)
          if board[r][c]=="X" or board[r][c]=="O":
            print((r,c),"already taken")
          else:
            return True



#this function is used to let the user know which player's turn is next in order to make a move.
def player(i):
  '''
  Given a move number (1-9), return the player
  the player is "X" for even moves, "O" for odd moves
  '''
  if i%2==1:
    return("O")
  else:
    return("X")

#win function checks after every move if a game is won by any of the user. if a user has won the game, it immediately lets them know who has won the game.
def win(board):
  '''
  Check a board for a win, 
  If a win print who won, and return True
  Otherwise return False
  '''
  # Check each row
  for i in range(3):
    if board[i][0]==board[i][1]==board[i][2]:
      print("Wow!",board[i][0], "wins!")
      return True 
      
      break


  # Check each column
  for i in range(3):
    if board[0][i] == board[1][i]== board[2][i]:
      print("Wow!",board[0][i], "wins!")
      return True 
      
      break
    
  
  # Check the diagonals 
  for i in range(1):
    if board[0][0] == board[1][1] ==board[2][2]:
      print("Wow!",board[0][0], "wins!")
      return True 
      
      break
  
    if board[0][2] == board[1][1] == board[2][0]:
      print("Wow!",board[0][2], "wins!")
      return True 
      
      break

  return False

#TTT function contains all the necessary functions from above code allowing a user to be able to enjoy a basic tic tac toe. The game starts with a player "X". 
def TTT():
  '''
  Play Tic Tac Toe
  Start with "x"
  '''
  board=makeBoard()
  displayBoard(board)
  for i in range(9):
    move=getMove(board,player(i))
    r,c=getLoc(move)
    #print(r,c)
    board[r][c]=player(i)
    displayBoard(board)
    if win(board):
      break
    
#calling the main funtion to start the game.
TTT()
