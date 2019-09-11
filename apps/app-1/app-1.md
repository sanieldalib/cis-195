# App 1: Tic Tac Toe

Discuss this app & get help on [Piazza](https://piazza.com/upenn/fall2019/cis195201/home).
Please leave feedback by creating a GitHub issue or by posting on Piazza.
Remember -- Stack Overflow and Google are encouraged, but DO NOT copy code. Ideas may be discussed with classmates, but don't work together.

This assignment has 2 parts. Part A covers the interface and app structure, and Part B covers the game logic. **You must submit each section to canvas by the due date.**

**Expected Duration:** 1+ hours for Part A, and 2+ hours for Part B.

**Deadlines:**
* Part A: Wednesday, September 11th at **11:59pm**
* Part B: Wednesday, September 18th at **11:59pm**

- - - -

## Objectives
* Make your first app
* Learn about interface builder and swift
* Get familiar with UIViewController, UIButton, UILabel, and UIView

![](/apps/app-1/assets/fig1.png?raw=true)

## Topics

#### UIKit
* UIViewController
* UIButton
* UILabel

#### Swift
* Properties
* Enums
* Optionals
* Functions
* Data structures

#### IB (Interface Builder)
* IBAction
* IBOutlet
* IBOutlet collections
* Element tags

---

# Part A: Tic Tac
## Step 0: Create a new project
* Open Xcode
* Select "new project" from the start screen, or use File > New > Project in the menu bar
* Select "Single View Application"
* Name the project "YOUR-NAME_tic-tac-toe"

## Step 1: Import assets
* Using the file menu on the left, open `Assets.xcassets`.
* Download the image assets from [this link](/apps/app-1/assets/app-1-assets.zip) (click 'download').
* There will be 3 image files for each symbol -- this is to account for different iPhone screen resolutions. [More info](https://developer.apple.com/design/human-interface-guidelines/ios/icons-and-images/image-size-and-resolution/).
* Drag all 9 of the image files into your assets file; this is called an "Asset Catalog".

## Step 2: Build the game board
* Go to the storyboard.
* Drag `UIButton`s into your `view` to construct the game grid, using the screenshots above as a reference.
* Set each button's `title` to be blank, and set the `image` field to "mark-none" (one of the images you just imported).
* Make the size of the buttons consistent.

## Step 3: Hook up the game board
* Go to `ViewController.swift`.
* Make a function to be called when any of the 9 buttons are tapped (hint: use @IBAction). Remember to hook the 9 buttons up to this function.
* When any of the buttons are pressed, this function should *change the image* of the pressed button. For now, randomly change the image to either "mark-x" or "mark-o" (hint1: use Boolean.random(). hint2: use `.setImage` with a state of `.normal`).
* This function should also print out the "button number" (hint: set the `tag` field in IB, and use `sender.tag` in code).
* That's all for now! We'll return to this function when we're implementing the game logic. For now, we're just setting up the interface.

## Step 4: Set up the labels
* Go to the storyboard.
* Drag 4 `UILabel`s into the ViewController -- one for the title, one for each score field, and one as a "game status" label. Give them fake text for now.
* Try to match the look of the labels to what you see in the screenshot by changing the font size, weight, and alignment.

## Step 5: Hook up the labels
* Go to `ViewController.swift`.
* Make an outlet variable for each `UILabel`.
* Connect the outlets from the storyboard.
* Back in `ViewController.swift`, test out the outlets by setting the `text` of each label whenever a button is tapped. This text can be whatever you want -- just demonstrate that a connection has been made.

## Step 6: Add a clear button
* In the storyboard, add a `UIButton` and change its title to "Clear".
* Change the `tint` of the button to your favorite color (just not blue).
* In `ViewController.swift` create a function to be called by the Clear button.
* In this function, we want to set the image of each button back to the image "mark-none" to clear the board. In order to do this, we'll need a reference to each of the 9 buttons... We could create an outlet variable for each button, but that would be messy -- instead, use an [IBOutlet collection](https://stackoverflow.com/questions/24805180/swift-put-multiple-iboutlets-in-an-array).
* At this point, tapping a button should randomly change it to an X or O. Tapping "clear" should set ALL buttons to the NONE state.

## Step 7: Sanity check
At this point your app should be crash free and support the following:
* Tapping a game grid button randomly changes it to a O or X, and updates each label to a different value of your choosing.
* Tapping the clear button sets each game grid button back to the NONE state.
* The buttons and labels should look roughly like they do in the screenshot.
* The app should compile and run in the simulator. It should not crash when any buttons are tapped.

## Submission
Zip your entire project folder. Name the zipped file app1A_Lastname_Firstname and submit it on canvas.

Late submissions will be graded according to the policy described in Recitation 0. Please submit by the deadline!

---
# End of Part A
SUBMIT YOUR WORK TO THIS POINT on Canvas by Wednesday, September 11th at **11:59pm**. Warning: missing this deadline will result in a late grade.
---

# Part B: Toe

What follows will be more open-ended than Part A.

Now that you've created the game’s UI in your storyboard and hooked up your UI to ViewController.swift, it is time to think about the infrastructure required to maintain the game’s state. For example:
* How do you plan to keep track of whose turn it is (Player X or Player O)?
* How many states can a block in a grid have? An example of a state is that “the block is currently occupied by an X”. How do you plan to represent these states given all the data structures you have learned?
Hint: A block should have 3 possible states.
* A grid is made up of 9 blocks. How do we maintain the state of the grid? 
* When, and how do you check if the game has been won (and by whom) or drawn?
* How should we update the interface when the game is won?

## Game logic
* If you think of the game as two players playing on one device, player 1 should tap on an empty block first to produce an X.
* Player 2 would then tap on another empty grid to produce an O. (What should happen if a player taps on an occupied block? Be sure to handle this.)
* The game is completed when:
* * Player X makes a move that results in Player X winning the game.
* * Player O makes a move that results in Player O winning the game.
* * Player X or O occupies the last empty block in the grid, such that neither of them has achieved a winning combination, therefore resulting in a draw.
* A complete game would not allow any more moves from either player for that round.
* Observe in the screenshots that there is a ‘status message’ that displays whose turn it is. At the beginning of the game, this should say "Player 1's Turn". When the game is complete, the label should say "Player _ Wins" in the case of a win, or "Draw" in the case of a draw. The label color should turn to green when a player wins.

## Winning Combinations
Let’s imagine that the blocks of tic-tac-toe grid are numbered as follows:
```
0   1   2
3   4   5
6   7   8
```

Then we can say that a player (X or O) has won, if the user has conquered any one of the following combinations of blocks:
`[0, 1, 2], [3, 4, 5], [6, 7, 8], [0, 3, 6], [1, 4, 7], [2, 5, 8], [2, 4, 6], [0, 4, 8]`

To find a winner, consider checking against these combinations after every move.

## After Each Move
When a user taps on a block in your tic-tac-toe grid, you would want to do the following:
* Update the underlying data structure that maintains the ‘state’ of each block in the grid.
* Update the UI to reflect this change in your data structure
* Check for the grid contains a winning combination.

## Reset Button
Recall (from the screenshots at the beginning of this document) that the app contains a ‘Reset’ button to reset the state of the tic-tac-toe game. This feature is useful for when the players want to restart a game, or start a new one. Implementing this feature would entail:

* Resetting the tic-tac-toe grid. 
* Hint: Given that the X’s and O’s on the grid are represented by custom images, what value must you set these images to, such that they are in an ‘blank’ or ‘unset’ or ‘none’ state?)
* Hint: Resetting the blocks of the tic-tac-toe grid would require having object references to them in code (a.k.a. IBOutlets). Use the IBOutletCollection you created in Part A.
* Resetting the ‘status message’ to say “Player 1's Turn” and be black (not green!)
* Resetting a game board should not reset the scoreboard!

## Update the Scoreboard
Recall (from the screenshots) that the game contains a scoreboard that maintains the scores for Player 1 (X) and Player 2 (O). This feature allows the players to compare their ‘number of victories’ across multiple games. You should create properties to maintain the scores, and update these properties and the UI when a player wins.

Hint: Can you use *property observers* to make your code more elegant?

## Submission
Zip your entire project folder. Name the zipped file app1B_Lastname_Firstname and submit it on canvas.

Late submissions will be graded according to the policy described in Recitation 0. Please submit by the deadline!

---
# End of Part B
SUBMIT YOUR WORK TO THIS POINT on Canvas by Wednesday, September 18th at **11:59pm**. Warning: missing this deadline will result in a late grade.
---
