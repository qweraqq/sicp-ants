# 来源
[https://inst.eecs.berkeley.edu//~cs61a/fa13/proj/ants/ants.html](https://inst.eecs.berkeley.edu//~cs61a/fa13/proj/ants/ants.html)

## Introduction
- In this project, you will create a tower defense game called Ants Vs. SomeBees. 
- As the ant queen, you populate your colony with the bravest ants you can muster. 
- Your ants must protect their queen from the evil bees that invade your territory. 
- Irritate the bees enough by throwing leaves at them, and they will be vanquished. 
- Fail to pester the airborne intruders adequately, and your queen will succumb to the bees' wrath. This game is inspired by PopCap Games' Plants Vs. Zombies ®.
- The Ants Vs SomeBees project highlights the **object-oriented programming paradigm from Section 2.4 of the text**. 

## Core Concepts
- A game of Ants Vs. SomeBees consists of a series of turns. In each turn, new bees may enter the ant colony. Then, new ants are placed. Finally, all insects (ants, then bees) take individual actions: bees sting ants, and ants throw leaves at bees. The game ends either when a bee reaches the ant queen (you lose), or the entire bee flotilla has been vanquished (you win).
- The `Colony`. The colony consists of several places that are chained together. The exit of each Place leads to another Place.
- Placing `Ants`. There are two constraints that limit ant production. Placing an ant uses up some amount of the colony's food, a different amount for each type of ant. Also, only one ant can occupy each Place.
- `Bees`. When it is time to act, a bee either moves to the exit of its current Place if no ant blocks its path, or stings an ant that blocks its path.
- `Ants`. Each type of ant takes a different action and requires a different amount of food to place. The two most basic ant types are the `HarvesterAnt`, which adds one food to the colony during each turn, and the `ThrowerAnt`, which throws a leaf at a bee each turn.

## The Code
- Most concepts in the game have a corresponding class that encapsulates the logic for that concept. For instance, a Place in the colony holds insects and connects to other places. A Bee stings ants and advances through exits.
- The game can be run in two modes: as a text-based game or using a graphical user interface (GUI). The game logic is the same in either case, but the GUI enforces a turn time limit that makes playing the game more exciting. The text-based interface is provided for debugging and development.
- The files are separated according to these two modes. ants.py knows nothing of graphics or turn time limits. All graphical elements are specified in `ants_gui.py` and `graphics.py`. It is possible to complete this project without ever reading the graphics files.

To start a text-based game, run
```bash
python ants.py
```

To start a graphical game, run
```bash
python ants_gui.py
```

- In the starter implementation, you have unlimited food and your ants only throw leaves at bees in their current Place. Try playing a game anyway! You'll need to place a lot of ThrowerAnts (the second type) in order to keep the bees from reaching your queen.

- The game has several options that you will use throughout the project, which you can view with `--help`.
```bash
python [ants.py|ants_gui.py] [OPTIONS]
    Run the Ants vs. SomeBees project.

    -h, --help      Prints this help message
    -t, --ten       Start with ten food
    -f, --full      Loads a full layout and assault plan
    -w, --water     Loads a full layout with water
    -i, --insane    Loads a difficult assault plan
```
- You have also been provided a testing file `ants_grader.py` that runs a series of unit tests for the project. To test your project, you can run
```bash
python ants_grader.py -v
```

This command runs all of the unit tests along with any doctests in `ants.py`. The optional `-v` generates more verbose output. You can also run tests for individual questions:
```bash
python ants_grader.py -q 2
python ants_grader.py -q A5
```
- If you would like to learn more about Python's built-in unit testing framework, read the documentation of the unittest module. Most problems have associated tests. Make sure that the tests for each problem pass before moving on.

