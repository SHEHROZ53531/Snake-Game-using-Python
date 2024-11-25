# Snake-Game-using-Python
I have developed a snake game using Python programming.
--------->   Creating a window for Snake game  <----------

1. window = Tk() window.title("Snake game") #Title of the Window window.resizable(False, False) #Window not be resizeable
2. score = 0 direction = 'down'
3. label = Label(window, text="Score:{}".format(score), font=('consolas', 40) ) #Creating a lablel font or score label.pack()
4. canvas = Canvas(window, bg=BACKGROUND_COLOR , height=GAME_HEIGHT, width=GAME_WIDTH) #Creating a canavas or backgroung color , height , widht that we intiliaze earlier canvas.pack() #We should have our game Board

---------->   To update a window or simpliy place a game board in center  <----------------

1. window.update()   # to update
2. window_width = window.winfo_width() window_height = window.winfo_height()
3. screen_windth = window.winfo_screenwidth() screen_height = window.winfo_screenheight()


---------->   we need to see how much we adjust window  <----------------

1. x = int((screen_windth/2) - (window_width/2)) y = int((screen_height/2) - (window_height/2))
2. #to set the geometry of window window.geometry(f"{window_width}x{window_height}+{x}+{y}")
3. #we need some controls for our snake window.bind('<Left>' , lambda event: change_direction('left')) window.bind('<Right>' , lambda event: change_direction('right')) window.bind('<Up>' , lambda event: change_direction('up')) window.bind('<Down>' , lambda event: change_direction('down'))
4. snake = Snake() #Object of snake food = Food() #Object of food next_turn(snake, food) #calling the next turn function
5. window.mainloop() ( Explain this entire code in details)


---------->   Game Settings  <----------------

 The game settings are defined at the top of the code:

GAME_WIDTH: The width of the game window, set to 1200 pixels.
GAME_HEIGHT: The height of the game window, set to 668 pixels.
SPEED: The speed of the game, set to 100. A lower value makes the game faster.
SPACE_SIZE: The size of each square in the game, set to 30 pixels.
BODY_PARTS: The number of body parts of the snake at the beginning of the game, set to 3.
SNAKE_COLOR: The color of the snake, set to blue (#0000FF).
FOOD_COLOR: The color of the food, set to yellow (#FFFF00).
BACKGROUND_COLOR: The background color of the game, set to black (#000000).

----------> Classes  <----------------

----->Snake Class

The Snake class represents the snake in the game.

__init__: Initializes the snake with a specified number of body parts.
body_size: The number of body parts of the snake.
coordinates: A list of coordinates representing the snake's body parts.
squares: A list of canvas rectangles representing the snake's body parts.
In the __init__ method, the snake is initialized with BODY_PARTS number of body parts, and each body part is represented by a coordinate [0, 0] (top-left corner of the game board). A square is created for each body part using canvas.create_rectangle, and the square is added to the squares list.

----->Food Class

The Food class represents the food in the game.

__init__: Initializes the food with a random position on the game board.
coordinates: A list of coordinates representing the food's position.
In the __init__ method, the food is initialized with a random position on the game board by generating a random x and y coordinate within the game board boundaries. The food is represented by an oval shape created using canvas.create_oval, and the oval is added to the canvas with a tag "food".


---------->   Functions    <----------------

------>next_turn Function
The next_turn function updates the game state and moves the snake to the next position.

snake: The snake object.
food: The food object.
The function does the following:

Updates the snake's coordinates and squares based on the current direction.
Checks if the snake has eaten the food and updates the score accordingly.
Checks for collisions with the game board boundaries or the snake's own body.
Calls the game_over function if a collision is detected

------>change_direction Function
The change_direction function changes the direction of the snake.

new_direction: The new direction of the snake (up, down, left, or right).
The function updates the direction variable accordingly, but only if the new direction is not opposite to the current direction (e.g., if the snake is moving up, it cannot suddenly move down).

------>check_collisions Function
The check_collisions function checks if the snake has collided with the game board boundaries or its own body.

snake: The snake object.
The function returns True if a collision is detected, False otherwise.

----->game_over Function
The game_over function is called when the game is over.

The function does the following:

Deletes all objects on the canvas.
Creates a "GAME OVER" text on the canvas.

---------->   Main code    <----------------

The main code creates a window for the game and sets up the game board.

Creates a Tk window with a title and sets it to not be resizable.
Creates a Label to display the score.
Creates a Canvas to render the game board.
Sets up the window geometry to center the game board on the screen.
Binds keyboard events to change the direction of the snake.
Creates a Snake and Food object and calls the next_turn function to start the game.
Enters the main event loop with window.mainloop().


---------->   Game loop     <----------------

The game loop is implemented using the next_turn function, which is called repeatedly using window.after with a delay of SPEED milliseconds. The function updates the game state, moves the snake, and checks for collisions. If a collision is detected, the game_over function is called.
