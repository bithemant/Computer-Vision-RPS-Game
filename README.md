# Computer Vision Rock Paper Scissors

Play Rock Paper Scissors against the computer using hand gestures detected from your webcam — no keyboard input needed during a round.

## What it does

The game opens your webcam, tracks your hand with MediaPipe, and reads your Rock, Paper or Scissors gesture. Press `s` to start a round: a 3-second countdown runs, then you have 1 second to show your move. The computer picks a move at random, the winner is decided, and the score updates on a live dashboard drawn on the video feed.

## Features

- Real-time hand tracking from the webcam (1280×720)
- Handedness-aware gesture recognition — works with your left or right hand
- Gesture classification from MediaPipe hand landmarks (finger and thumb positions)
- 30-frame vote buffer: the move shown most often during the 1-second capture window wins, so a single flickering frame can't decide the round
- 3-second countdown before each round
- Live on-screen dashboard with round number, scores, current moves, last result and who is leading
- Random computer opponent

## Tech stack

- Python
- OpenCV (`cv2`) — webcam capture and on-screen display
- MediaPipe — hand landmark detection and tracking

## How to run

You need Python 3 and a webcam. There is no `requirements.txt` in this repo, so install the two dependencies first:

```bash
pip install opencv-python mediapipe
```

Then run the game:

```bash
python stonepapergame.py
```

Controls:

- `s` — start a round
- `q` — quit

Show your hand clearly to the camera during the "Show your move!" window. Keep your hand steady and well lit for the best detection.

## Project structure

```
Computer-Vision-RPS-Game/
├── stonepapergame.py                          # The whole game: hand tracking, gesture classification, rounds, dashboard
├── Readme.txt                                 # Short overview of the project
└── Stone_Paper_Scissor_Project_Overview_.docx # Project overview document
```
