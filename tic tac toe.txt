import random
#*********************************FUNKCJE*************************
def display_board(board):
    print('+-------+-------+-------+')
    print('|       |       |       |')
    print('|  ',board[0],'  |  ',board[1],'  |  ',board[2],'  |')
    print('|       |       |       |')
    print('+-------+-------+-------+')
    print('|       |       |       |')
    print('|  ',board[3],'  |  ',board[4],'  |  ',board[5],'  |')
    print('|       |       |       |')
    print('+-------+-------+-------+')
    print('|       |       |       |')
    print('|  ',board[6],'  |  ',board[7],'  |  ',board[8],'  |')
    print('|       |       |       |')
    print('+-------+-------+-------+')
def enter_move(b):
     move = '10'
     while (move.isdigit()==False or int(move) not in board):
         move = input("Enter your move(number): ")
     move = int(move)
     b[b.index(move)] = 'O'
     return b
def computer_move(b):
    numbers=[1,2,3,4,5,6,7,8,9]
    arr=[]
    for item in b:
        if item in numbers:
            arr.append(item)
    rand=random.choice(arr)
    b[b.index(rand)] = 'X'
    return b
def didYouWin(b):
    if b[0]=='O' and b[1]=='O' and b[2]=='O' or b[3] == 'O' and b[4] == 'O' and b[5] == 'O' or b[6] == 'O' and b[7] == 'O' and b[8] == 'O':
        print('YOU WON!')
        return True
    if b[0]=='O' and b[3]=='O' and b[6]=='O' or b[1] == 'O' and b[4] == 'O' and b[7] == 'O' or b[2] == 'O' and b[5] == 'O' and b[8] == 'O':
        print('YOU WON!')
        return True
    if b[0]=='O' and b[4]=='O' and b[8]=='O' or b[2] == 'O' and b[4] == 'O' and b[6] == 'O':
        print('YOU WON!')
        return True
def didComputerWin(b):
    if b[0]=='X' and b[1]=='X' and b[2]=='X' or b[6] == 'X' and b[7] == 'X' and b[8] == 'X':
        print('COMPUTER WON')
        return True
    if b[0]=='X' and b[3]=='X' and b[6]=='X' or b[1] == 'X' and b[4] == 'X' and b[7] == 'X' or b[2] == 'X' and b[5] == 'X' and b[8] == 'X':
        print('COMPUTER WON')
        return True
    if b[0]=='X' and b[4]=='X' and b[8]=='X' or b[2] == 'X' and b[4] == 'X' and b[6] == 'X':
        print('COMPUTER WON')
        return True
def freeFields(b):
    freeFieldsArr=[]
    for item in board:
        if (item!= 'O' and item!='X'):
            freeFieldsArr.append(item)
    return freeFieldsArr
def draw(b):
    if len(freeFields(b))==0:
        print('DRAW!')

#**********************VARIABLES********************
board = [1, 2, 3, 4, 'X', 6, 7, 8, 9]

#************************GAME********************
while(True):
    display_board(board)
    board = enter_move(board)
    if didYouWin(board):
        display_board(board)
        break
    computer_move(board)
    if didComputerWin(board):
        display_board(board)
        break
    draw(board)