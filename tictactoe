from __future__ import print_function
#from IPython.display import clear_output
import random

# Displays the board. It is a 3x3 input that corresponds to
# the standard number bad on a full keyboard
# 7 8 9
# 4 5 6
# 1 2 3

def display_board(board):
	#clear_output()
	print('   |   |')
	print(' ' + board[7] + ' | ' + board[8] + ' | ' + board[9])
	print('   |   |')
	print('-----------')
	print('   |   |')
	print(' ' + board[4] + ' | ' + board[5] + ' | ' + board[6])
	print('   |   |')
	print('-----------')
	print('   |   |')
	print(' ' + board[1] + ' | ' + board[2] + ' | ' + board[3])
	print('   |   |')
	print('')

# Takes in player input and assigns the marker as 'X' or 'O'

def player_input():
	while True:
		xo = input("Input 'X' or 'O': ")
		if (xo == 'X') or (xo == 'O'):
			return xo
		else:
			continue


# Take in the board, a marker, and the position and assigns it to a board

def place_marker(board, marker, position):
	if (position > 9) or (position < 1):
		print("Invalid position")
		return
	else:
		if ((marker == "X") or (marker == "O")):
			board[position] = marker
		else:
			print("Invalid Marker")
			return
	

# Takes a board and a marker(X or O) and sees if the marker has won

def win_check(board, mark):
	if board[1] == mark:
		if board[2] == mark:
			if board[3] == mark:
				return True
		if board[4] == mark:
			if board[7] == mark:
				return True
		if board[5] == mark:
			if board[9] == mark:
				return True
	if board[2] == mark:
		if board[5] == mark:
			if board[8] == mark:
				return True
	if board[3] == mark:
		if board[6] == mark:
			if board[9] == mark:
				return True
		if board[5] == mark:
			if board[7] == mark:
				return True
	if board[7] == mark:
		if board[8] == mark:
			if board[9] == mark:
				return True
	if board[4] == mark:
		if board[5] == mark:	
			if board[6] == mark:
				return True
	return False

# Randomly decides which player goes first. Returns a string of which player went first

def choose_first():
	choice = random.randint(1,2)
	if choice == 1:
		return 'Player 1'
	else:
		return 'Player 2'

#  Returns a boolean indicating whether a space on the board is freely available.

def space_check(board, position):

	if board[position] != 'X' and board[position] != 'O':
		return True
	else:
		return False

# Returns true if the board is full and false if otherwise

def full_board_check(board):
	tf = True
	for item in board:
		if (item != 'X') and (item != 'O'):
			tf = False
	if tf == True:
		return True
	elif tf == False:
		return False

# Asks a for a player's next position and checks it its a free position. If it is, it returns the position

def player_choice():
	inp = input('What is your next position?: ')
	return int(inp)

# Asks the player is they want to play again and returns boolean True if they do want to play

def replay():
	imp = input('Do you wanna play again? (Yes or No): ')
	if imp.upper() == 'YES':
		return True
	else:
		return False


#############
# Base game #
#############




# Game Start
print('Welcome to Tic Tac Toe!\n')
# Game initialization. Player 1 and Player 2 choose
# markers and an order is decided.

while True:

	# Initial variables
	board = [" "] * 10
	board[0] = 'X'
	p1marker = None
	p2marker = None
	first = None
	second = None
	curr = None
	select = None

	# Player 1 picks a marker

	print('Player 1, pick a marker.')
	p1marker = player_input()
	print("")

	# Player 2 picks a marker

	print('Player 2, pick the other marker.')

	# Prevents Player 2 from picking the same marker
	while True:
		p2marker = player_input()
		if p2marker == p1marker:
			print("Can't have same marker as Player 1\n")
			p2marker = None
			continue
		else:
			break
	print("")

	# Random selection of the first player to start

	first = choose_first()
	if first == 'Player 1':
		second = 'Player 2'
		curr = p1marker
	elif first == 'Player 2':
		second = 'Player 1'
		curr = p2marker
	print('%s goes first!' % first)
	print("\n")

	# Core gameplay
	while full_board_check(board) == False:
		display_board(board)
		if curr == p1marker:
			print("%s's turn!" % first)
			while True:
				while True:
					select = player_choice()
					if select <= 9 and select >= 1:
						break
					print('Invalid position, please select again')

				if space_check(board, select) == True:
					place_marker(board, p1marker, select)
					curr = p2marker
					break
				else:
					print('That is not a valid space')
					continue
			
		elif curr == p2marker:
			print("%s's turn!" % second)
			while True:
				while True:
					select = player_choice()
					if select <= 9 and select >= 1:
						break
					print('Invalid position, please select again')
				if space_check(board, select) == True:
					place_marker(board, p2marker, select)
					curr = p1marker
					break
				else:
					print('That is not a valid space')
					continue

	display_board(board)
	if (win_check(board, p1marker) == True) and (win_check(board, p2marker) == False):
		print('Player 1 Wins!')
	elif (win_check(board, p1marker) == False) and (win_check(board, p2marker) == True):
		print('Player 2 Wins!')
	elif (win_check(board, p1marker) == True) and (win_check(board, p2marker) == True):
		print('Something is wrong')
	elif (win_check(board, p1marker) == False) and (win_check(board, p2marker) == False):
		print('Draw')

	if replay() == True:
		print("Another game!")
		continue
	else:
		print("Goodbye")
		break
