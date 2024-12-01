This is the final project for University of Virginia School of Data Science's Fall 2024

Monte Carlo Simulator

The Monte Carlo Simulator is a Python package designed to model and analyze random processes using Monte Carlo methods. Named after the famous casino in Monaco, these methods use repeated random sampling to estimate the outcomes of complex systems. This simulator includes three core components—Die, Game, and Analyzer—that work together to mimic and study stochastic behavior. Whether you're exploring probabilities, analyzing patterns, or testing statistical hypotheses, this package offers a robust framework to dive into the fascinating world of randomness and simulations.

## Metadata
- **Author**: Jerry Singh 
- **Course**: DS 5100 | University of Virginia (khb9gd)
- **GitHub repo**: CodeStriker10

##Synopsis

Installing
After downloading this repository, run the code:
pip install .

Importing
Import the montecarlo library with the code:
import montecarlo

When trying to import a specific class within the montecarlo library, run the code:
from montecarlo import insert_class_name
insert_class_name can be Die, Game, or Analyzer.
This project implements a Monte Carlo Simulator with three core classes: Die, Game, and Analyzer. Below are examples demonstrating how each class is used, showcasing their functionality.

##Die Class
The Die class creates a die with customizable faces and weights. You can simulate biased or fair rolls using this class.

python code:
from monte_carlo import Die

#Create a die with three faces
die = Die(["A", "B", "C"])

#Change the weight of a specific face
die.change_weight("A", 5)

# Display the current faces and weights as a dataframe
print(die.show())

# Roll the die 5 times and display the outcomes
rolls = die.roll(5)
print(rolls)

## Game Class
The Game class uses multiple Die objects to simulate a game. It records the results of rolling all dice over a specified number of rounds.

python code:
from monte_carlo import Game, Die

# Create dice with different faces
die1 = Die(["1", "2", "3"])
die2 = Die(["X", "Y", "Z"])

# Initialize a game with a list of dice
game = Game([die1, die2])

# Roll all dice 10 times
game.play(10)

# Display the results in wide format (default)
print(game.show())

# Display the results in narrow format
print(game.show(form="narrow"))

## Analyzer Class
The Analyzer class performs statistical analysis on the results of a Game object, providing insights such as jackpots, combinations, and face frequencies.

python code: 
from monte_carlo import Analyzer, Game, Die

# Create and play a game
die1 = Die(["A", "B"])
die2 = Die(["1", "2"])
game = Game([die1, die2])
game.play(100)

# Analyze the game results
analyzer = Analyzer(game.show())

# Count how many jackpots occurred (all dice rolled the same face)
jackpots = analyzer.jackpot()
print("Number of jackpots:", jackpots)

# Get all combinations of rolled faces and their frequencies
combinations = analyzer.combo()
print(combinations)

# Get counts of each face for every roll
face_counts = analyzer.face_counts()
print(face_counts)

## API
The Monte Carlo Simulator API consists of three main classes: Die, Game, and Analyzer. Each class is designed to work together for modeling, simulating, and analyzing random processes. Below is a detailed breakdown of the classes, their attributes, and methods.

## Die Class
The Die class represents a single die with customizable faces and weights, allowing for both fair and biased simulations.

Attributes:
None

Methods:
__init__(faces)
Initializes a die with unique faces, each assigned a default weight of 1.
Parameters:

faces (list or array): A list of strings or integers representing the die's faces.
Example:
die = Die(["A", "B", "C"])
change_weight(face, new_weight)
Updates the weight of a specified face.
Parameters:

face (str or int): The face whose weight will be updated.
new_weight (float): The new weight to assign.
Raises:
ValueError if the face is invalid or the weight is not positive.
Example:
die.change_weight("A", 5)

roll(num_rolls=1)
Rolls the die a specified number of times.
Parameters:

num_rolls (int): Number of times to roll the die (default is 1).
Returns:
A list of outcomes from the rolls.
Example:
results = die.roll(3)

show()
Displays the current state of the die (faces and weights) as a dataframe.
Returns:

A Pandas DataFrame showing the faces and their respective weights.
Example:
print(die.show())

## Game Class
The Game class simulates a series of rolls using multiple dice of the same type, recording the outcomes for analysis.

Attributes:
None

Methods:
__init__(list_of_die)
Initializes a game with a list of Die objects.
Parameters:

list_of_die (list): A list of Die objects.
Example:
game = Game([die1, die2])

play(rolls)
Simulates rolling all dice for a specified number of rounds.
Parameters:

rolls (int): Number of times to roll each die.
Returns:
None
Example:
game.play(10)

show(form='wide')
Returns the results of the most recent game as a dataframe.
Parameters:

form (str): Format of the output, either "wide" (default) or "narrow".
Raises:
ValueError if an invalid format is specified.
Returns:
A Pandas DataFrame with game results.
Example:
print(game.show(form="wide"))

## Analyzer Class
The Analyzer class analyzes game results, providing statistical insights such as jackpots, face combinations, and frequency counts.

Attributes:
jackpot_count: Total number of jackpots (all dice rolled the same face).
jackpot_dataframe: Dataframe containing rows where jackpots occurred.
combo_frame: Dataframe of all combinations (or permutations) of face values with their frequencies.
face_count: Dataframe showing counts of each face per roll.
die_type: Data type of the die faces.

Methods:
__init__(game_results)
Initializes the Analyzer object with results from a Game object.
Parameters:

game_results (DataFrame): A dataframe of results from the Game class.
Example:
analyzer = Analyzer(game_results)

jackpot()
Identifies and counts the number of jackpots (all dice showing the same face).
Returns:

A dataframe of rows where jackpots occurred.
Example:
jackpots = analyzer.jackpot()

combo(permutation=False)
Calculates the frequency of face combinations or permutations across rolls.
Parameters:

permutation (bool): If True, calculates permutations instead of combinations. Default is False.
Returns:
A dataframe of combinations or permutations with frequencies.
Example:
combinations = analyzer.combo()

face_counts()
Counts the occurrences of each face value per roll.
Returns:

A dataframe showing face counts for each roll.
Example:
face_counts = analyzer.face_counts()

