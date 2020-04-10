## Dynamic Memory Management

**Dynamic arrays** will be used in this program to avoid any non-essential counts and calculations.

A dynamic struct array scoreboard is needed to display/sort the final scores of the user. Initially, the array will be assigned very largely (about a thousand or even more), but it will be altered to the number of lines of text file scoreboard.txt (which would be explained later). 

Dynamic struct array inventory will also be created to save all the objects that the user keeps during the gameplay. Since it is unknown how many items the user will keep, the array is initially sized zero, and later expanded depending on the number of items. The struct will include two string values: an item name and an item description.

## File Input/Output

Two files needed: **autosave.txt**, **scoreboard.txt**

**autosave.txt**

This blank text file is created as soon as the game operates for the first time in a new working space. When a player starts a new game, a line is inputted into the file:

`ID` `UserName` `Checkpoint` `Current Stage`
1. `ID` is a randomly assigned value for each individual user. At the start of the game, a user is required to input a unique 5 digit code. This is used to identify each user in a text file.
2. `UserName` is the name of the protagonist that a user assigns when a game starts. Different users can have the same UserName.
3. `Checkpoint` is a variable that is initially created at the start of the game. Each stage of the game has its own unique ‘checkpoint variable’. This variable indicates which stage player is in and can continue at the same stage when the game is rebooted before the game is finished. The user can resume the game from where it ended before closing the game.
4. `Current Stage` is the in-game name of the stage. Since the user doesn’t know what checkpoint value represents which stage, they wouldn’t understand what stage they were in only with the checkpoint. The name of the stage will notify the user easily.

The game will have an option to resume it. If the user wants to resume the game, the user can input the ID and continue the game. In case the user cannot remember the ID, there is an option to see all of the content in autosave.txt and input the ID shown (file output).

**scoreboard.txt**
The file is created after the game is completed for the first time in the working directory. When the user ends the game, a line is inputted in a file:

`UserName` `Score` `Achievement`

1. `UserName` is the name of the protagonist that a user assigns when a game starts. Different users can have the same UserName.
2. `Score` is a point based on the time taken for the user to end the game (details of the score will be written later). The user can display all previous records sorted in order from highest score to lowest score.
3. `Achievement` is displayed in %(percentage). This is based on not only the progress of the game but also the items that a person picks and important sub-plot materials as well. 
The final scores of the player will be displayed (file output) if the user wants to. Scores will be displayed in highest to lowest score order.

## Program codes in multiple files

The main function (main.cpp) will include the checkpoint system and function headers only.

File for text(text.h)
 - `playertext.cpp`: this function will include all the dialogues from the player itself.
 - `aliennote.cpp`: this function will include all the notes given to the player.
 - `encryption.cpp`: this function encrypts the note to another form (alien words) before the message is found.
 
File for save(save.h)
 - `autosave.cpp`: updates the checkpoint variable at autosave.txt.
 - `achievement.cpp`: updates the achievement % when a user interacts with a certain item or progresses the game.

First Round (roundone.h)
 - `locate.cpp`: locates the true key and fake keys in different containers.
 - `clue.cpp`: gives clues to find the key (Specific content of the notes will be updated later. This part might consist several functions).
 
Second Round (roundtwo.h)
 - `boardscript.cpp`: randomly loads one of the pre-made boards (total 5 or more)
 - `display.cpp`: outputs the current board
 - `changeboard.cpp`: changes the status of the board depending on user input
 - `refresh.cpp`: refresh the board in case the user failed the puzzle
 - `shoot.cpp`: shoot a bullet to the front if the user requested. The bullet breaks the block.
 
Third Round (roundthr.h)
 - `tubeassign.cpp`: randomly assign the location of the tubes
 - `display.cpp`: outputs the current board (it can possibly be the same function as second round’s display.cpp)
 - `humanmove.cpp`: the person will move to a certain direction depending on the user’s input.
 - `alienmove.cpp`: the alien will move from side to side unless the human is too close; it will follow the human then.

Each function will take one `.cpp` file. There will be 5 or 6 `.h` files that hold the function files. A `makefile` will be created to simply compile the files after the alteration.
