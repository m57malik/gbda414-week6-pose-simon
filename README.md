# Pose Simon Says — GBDA 414 Week 6

Individual activity by Moosa Malik, adapted from the supplied Week 6 workshop with OpenAI Codex coding support.

## Play

Allow camera access and wait for MoveNet to load. Keep your shoulders and wrists in view. Follow the requested action only if the prompt starts with **Simon says**. Otherwise, keep your hands down. Lower your hands between rounds. Left and right refer to your anatomical left and right.

The active file is `sketch.js`. All workshop checkpoints remain in the folder for reference; `index.html` loads exactly one sketch.

## Changes

- Started from the instructor's `full-sketch.js`.
- Confirmation: **NICE READ. YOU GOT IT.**
- Rejection: **ROUND MISSED. TRY AGAIN.**
- Added `simonSays` to every prompt and alternate prefixed/unprefixed prompts in a fixed sequence.
- Added `evaluateRound(simonSays, detected)`, which returns true when the two Booleans match.
- Retained the timed WAITING, PROMPTING and RESULT states and the action-detection latch.
- Fixed the supplied page's reference to a missing `bonus-sketch.js`.
- Explicitly select MoveNet and WebGL to avoid the old library's WebGPU startup error in current Chrome.
- Wrapped longer prompts and added game instructions.

| Simon says | Action detected | Result |
| --- | --- | --- |
| Yes | Yes | Correct |
| Yes | No | Incorrect |
| No | Yes | Incorrect |
| No | No | Correct |

## Run locally

Serve this folder using VS Code Live Server or another local HTTP server, then open the localhost address. Internet access is required for p5.js, ml5.js and the model. Camera access requires localhost or HTTPS.

## Validation and limits

Automated checks passed for the four rule cases, action memory across a prompt, result retention, next-round reset, prompt alternation, raised-wrist geometry and stale-pose rejection. The browser preview loads the model and draws the game. Physical webcam and private-window tests must also be performed before submission.

The system estimates keypoints, not intention. Low confidence, poor light, occluded wrists or a stale/missing pose can prevent an action from being recognized. In an unprefixed round, an undetected attempted gesture can be scored as no action. The feedback describes model evidence, not deliberate obedience or refusal.

## Source files

`full-sketch.js` and `step1-webcam.js` through `step4-check.js` are the supplied workshop checkpoints. p5.js 1.9.4 and ml5.js 1.0.1 are loaded from their original CDN URLs in `index.html`.
