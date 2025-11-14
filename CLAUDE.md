# CLAUDE.md

Guidance for Claude Code (claude.ai/code) working in this repository.

## Project Overview

`the-truth-lan` is a online board game app, powered by Flask. It contains the following modules: 

1. The game engine: `game.py` defines a class `Game` as the engine that runs the game. 
2. The backend: `app.py` defines the backend of the game.
3. The frontend: `templates/index.html` defines the frontend page, with styles in `static/style.css` and scripts in `static/script.js`. 

## Game Engine: `game.py`

The game engine works on maintaining and updating the game states, where a state is a subclass of `State`, which supports the following methods: 

1. initialization : which takes a value (any type) to initialize the state.
2. get : get the value
3. set : set the value
4. update : takes a delta (any type) to update current value  

There are several predefined subclasses of `State`: 

- `BooleanState` : a state of boolean value, and the update takes a delta of boolean value, and calculate the (not xor) of the current value and the delta value. 
- `IntState` : a state of integer value, and the update takes a delta of int value. 
- `FloatState`: a state of float value, and the update takes a delta of float value.
- `ListState`: a state takes value from a list, and the update takes a delta of integer value as a shift.
- `StringState`: a state of string value, and the update has no effect.

The game engine maitains 3 categories of game state: 

1. Global state:   