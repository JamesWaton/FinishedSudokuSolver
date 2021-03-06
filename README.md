This Project is one to test my mathematical skills and how I am able to implement them into an automated sudoku solver. This works through trial and error in the way that if an error occurred then it will go back a step and try again. It will continually do this until it gets the correct answer even if it means going all the way back to the start. This Sudoku Solver Project was one that was set as one of five projects that was part of the Quality Assurance Projects Certificate in Free Code Camp. Another part of this project was to see if I could work with unit tests and functional tests. You can find my original project on my repl.it https://repl.it/@JamesWatson7/boilerplate-project-sudoku-solver-1 as this is where i originally made the project. This also contains the Unit and Functional tests unlike this  one i have uploaded to GitHub.


Creating a sudoku solver 

I was tasked with this project as part of doing the Quality Assurance Certificate on the Free Code Camp Course as one of the final projects. When starting the project the HTML template had already been made so all I had to do was pull it from the git repository. The task of the project was to solve the sudoku puzzle through creating a mathematical algorithm so when you press the solve button it will automatically solve the puzzle. While having 13 tasks to make sure that you do the projects properly while also helping as a guide. So the most challenging part of these challenges was the mathematical side as it took a long time thinking of the right algorithms and the approach to take rather than previous projects that took longer finding the right libraries and other technologies and how to implement them into my code.


The challenges to complete are as what follows:

You should provide your own project, not the example URL.
You can POST /api/solve with form data containing puzzles which will be a string containing a combination of numbers (1-9) and periods . to represent empty spaces. The returned object will contain a solution property with the solved puzzle.
If the object submitted to /api/solve is missing a puzzle, the returned value will be { error: 'Required field missing' }.
If the puzzle submitted to /api/solve contains values which are not numbers or periods, the returned value will be { error: 'Invalid characters in puzzle' }.
If the puzzle submitted to /api/solve is greater or less than 81 characters, the returned value will be { error: 'Expected puzzle to be 81 characters long' }.
If the puzzle submitted to /api/solve is invalid or cannot be solved, the returned value will be { error: 'Puzzle cannot be solved' }.
You can POST to /api/check an object containing a puzzle, coordinate, and value where the coordinate is the letter A-I indicating the row, followed by a number 1-9 indicating the column, and value is a number from 1-9.
The return value from the POST to /api/check will be an object containing a valid property, which is true if the number may be placed at the provided coordinate and false if the number may not. If false, the returned object will also contain a conflict property which is an array containing the strings "row", "column", and/or "region" depending on which makes the placement invalid.
If the puzzle submitted to /api/check contains values which are not numbers or periods, the returned value will be { error: 'Invalid characters in puzzle' }.
If the puzzle submitted to /api/check is greater or less than 81 characters, the returned value will be { error&#58; 'Expected puzzle to be 81 characters long' }.
If the object submitted to /api/check is missing puzzle, coordinate or value, the returned value will be { error: Required field(s) missing }
If the coordinate submitted to api/check does not point to an existing grid cell, the returned value will be { error: 'Invalid coordinate'}
If the value submitted to /api/check is not a number between 1 and 9, the returned values will be { error: 'Invalid value' }

Before I start talking about how I came to solve some of these solutions you should know that the best way to see my logic is to read through my comments in my code, as there I describe each function a little more in depth. Starting off I had to find how to access the correct squares which was easy enough using the developer tools. Then connect the index of the text area and the grid to match up so when the text area is updated so will the grid through an event listener. 

With challenge 3 is making an error message appear if there is a number or character that is not between 0-1 luckily there is a way for doing this through regex so i was able to be solved in  one line (let validateRegex = /^[0-9.]*$/) then update the error box if it fails. While making the grid I made it so only one digit can be added through a basic function.

Now for solving the puzzle I went for essentially trial and error approach so starting with the fist empty box the computer will add 0 if it passes then go to the next empty box. So when it comes to the empty boxes further along the algorithm will most likely have to restart the whole puzzle with the first empty box as number 1. This is due to it failing all numbers so it will go to the previous empty box going for the next higher number. So when a box fails to pass all the criteria of no matching numbers in a line then it goes back to the previous empty box and tries again with a higher number so on.  Unless it has tried each sequence of the 81 boxes and still failed then it will return an error message letting the user know it is unsolvable. If it passes then return the answer in an array letting the user know the solution.

To go break up the procedure of selecting the right digit for each empty box I wrote three functions: one to check through the column in each row to make sure the value doesn't exist already then, it checks through the row in each column to make sure the value doesn't exist already so opposite to the first one. Next I created one that determines the top row and the left column of the box (3 x 3 grid) to check if it checks through each row and column in the small 3x3 grid and value doesn't already exist then place that number (true).So buy the end it will look at each row or column 3 times before placing it.

For the error tasks are just making an error message which is quite simple as you can just target the errorBox then put inner text in depending on the error. For example if some has put in less than 81 values that would make it not fill up the text box to try make it easier then I have an error message letting the user know 81 characters are expected. This also helps with automatic updating as the text box or grid cant be updated until there are 81 characters.  Finally once there are no errors it is time to return the solved puzzle by converting the solution to a string to put in the text box that then can be printed onto the grid using textBoxChanged(). Finally making the clear button clear all values in the text box and cells in the grid to allow the user to try other sudoku problems. So with that being done I was now finished with all the challenges complete.

From this exercise it has allowed me to practice my problem solving abilities and how they can be implemented into web development even if this wouldn’t be the typical project you would come across. The favourite part of this project was breaking up the problem into multiple different functions to get the final solution and how each different function works so in sync with one another, what is a crucial part of writing perfect code. I would like to acknowledge Ganesh H as his video on youtube for this was a tremendous help you can find his work on his channel under Sudoku Solver - Quality Assurance Projects - freeCodeCamp.


By James Watson

