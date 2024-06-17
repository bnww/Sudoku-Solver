# Sudoku solver

A sodoku solver algorithm. The code is in `sudoku.ipynb` along with a description of the implementation. Sudokus of varying difficulties are stored in the `data` folder.

I decided to design this algorithm as a constraint satisfaction problem, as this mirrors the way that humans think about sudokus, inputting values according to the constraints and then updating our knowledge of the problem to decide what square to look at changing next.

Because of this, I followed a similar class-based structure to the constraint satisfaction solution for the 8 queens problem. I used a dictionary in order to keep track of the unknown square grid references given as a string, and their corresponding possible values. The possible values were found by looping through the rows, columns and 3x3 grids in turn, removing the values from a list of values 1-9.

For the search algorithm itself, I implemented a function which picks the next square based on which unresolved square has the fewest number of possible options, thus increasing efficiency by increasing the odds of choosing the correct solution for a square. I then followed the steps set out in the 8 queens exercise to implement a depth first search. This has the advantage over a breadth first search because it can be faster to discover invalid sudokus, as if all possible values for a certain square lead to invalid states, you know that the board itself is invalid (or a previous action invalidated it).

I was working on an implementation which tracked the possible values for every single square on the board, rather than just the unresolved squares, in the aim to better find invalid sudoku configurations. Unfortunately, when I tried to implement this I had to update many of the functions and constraints and it caused bugs which I did not have the time to fix. Thus, there are some rare exceptions where my algorithm will fill in a puzzle despite the puzzle not having solutions.