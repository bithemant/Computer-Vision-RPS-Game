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

## How it works

- **Hand tracking:** MediaPipe Hands follows one hand at a time (detection and tracking confidence 0.6) and draws its landmarks on the mirrored video feed.
- **Reading a gesture:** a finger counts as open when its fingertip sits above its middle joint; the thumb is judged by its sideways position, which flips between left and right hands. Rock is a closed fist, Paper is all five digits open, Scissors is index and middle open with the rest closed — any other pose counts as no gesture.
- **A round:** press `s` and a 3-second countdown runs, then a 1-second "Show your move!" window opens. Every frame in that window votes for the gesture it sees, and the most-voted gesture is your move (a 30-frame buffer, about 1 second at 30 FPS). If no gesture was recognised, the round ends with "No valid move" and no point is given.
- **Scoring:** the computer picks its move at random and the winner follows the usual rules. Scores are shown as You vs Hemant on the dashboard card at the right of the video feed, along with the round number, both moves, the last result and who is leading.

## Tech stack

- Python
- OpenCV (`cv2`) — webcam capture and on-screen display
- MediaPipe — hand landmark detection and tracking

## How to run

You need Python 3 and a webcam. Install the dependencies first:

```bash
pip install -r requirements.txt
```

Then run the game:

```bash
python stonepapergame.py
```

Controls:

- `s` — start a round
- `q` — quit

Show your hand clearly to the camera during the "Show your move!" window. Keep your hand steady and well lit for the best detection.

If the game reports "No valid move", hold the gesture steady and fully inside the frame for the whole 1-second window — a half-seen hand does not register a vote.

## Project structure

```
Computer-Vision-RPS-Game/
├── stonepapergame.py                          # The whole game: hand tracking, gesture classification, rounds, dashboard
├── requirements.txt                            # opencv-python, mediapipe
├── Readme.txt                                 # Short overview of the project
└── Stone_Paper_Scissor_Project_Overview_.docx # Project overview document
```
