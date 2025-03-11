# Shepherd's Dog

I've had this game concept in mind for years. While I've built several prototypes, getting the sheep flocking behavior right proved challenging. Now, with LLMs showing impressive programming capabilities, I'm curious to see what game they can create when given the same prompt (see below).

Every model had 1 shot at this task. I would tell them to continue if they ran out of tokens and combine the results in one index.html.

[Discussion on Hacker News](https://news.ycombinator.com/item?id=43298945)

## Leaderboard

| Model      | Score                           | Demo                                                                              | Notes                                                                           |
| ---------- | ------------------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| Claude 3.7 | [24/28](./claude-3.7/README.md) | [Demo](https://vnglst.github.io/when-ai-fails/shepards-dog/claude-3.7/index.html) | Really impressive demo, missing some obstacle dynamics. Doesn't work on Safari. |
| o3-mini    | [16/28](./o3-mini/README.md)    | [Demo](https://vnglst.github.io/when-ai-fails/shepards-dog/o3-mini/index.html)    | Misses a lot of features, but I love the flocking & the gameplay.               |
| o1 Pro     |                                 | [Demo](https://vnglst.github.io/when-ai-fails/shepards-dog/o1-pro/index.html)     | Pretty similar to o3-mini                                                       |
| Mistral    | [12/28](./mistral/README.md)    | [Demo](https://vnglst.github.io/when-ai-fails/shepards-dog/mistral/index.html)    | Herding is not properly implemented.                                            |
| GPT-4o     | [4/28](./gpt-4o/README.md)      | [Demo](https://vnglst.github.io/when-ai-fails/shepards-dog/gpt-4o/index.html)     | Limited set of features. Model wouldn't continue.                               |
| Gemini Pro |                                 | [Demo](https://vnglst.github.io/when-ai-fails/shepards-dog/gemini-pro/index.html) | Difficult as sheep don't stay in the pen.                                       |
| Deepseek   | [0/28](./deepseek/README.md)    | [Demo](https://vnglst.github.io/when-ai-fails/shepards-dog/deepseek/index.html)   | JavaScript is not valid.                                                        |
| Cursor     |                                 | [Demo](https://vnglst.github.io/when-ai-fails/shepards-dog/cursor/index.html)     | Super impressive, but not sure if this counts as "one-shot"                     |

## Prompt

```markdown
Create a game called _Shepherd's Dog_ where the player controls a dog to herd sheep into a pen. The core gameplay mechanic and what makes this game stand out is the realistic flocking behavior of the sheep - they should move as a cohesive group, follow each other, and react naturally to the dog and obstacles. The player moves the dog using mouse or touch controls and herds the sheep into a pen. The player can bark by clicking/tapping on the screen to make the sheep move faster. To complete each level, the player must herd at least 80% of the sheep (e.g., 40 out of 50 sheep) into the pen before nightfall. The difficulty increases as the game progresses through more obstacles between the starting position of the sheep and the pen.

## Flocking Behavior Requirements

- Sheep should demonstrate authentic flocking behavior based on principles like separation, alignment, and cohesion
- Sheep should react realistically to the dog's presence (moving away while staying in a group)
- The flock should navigate around obstacles while maintaining group dynamics
- Individual sheep should occasionally stray but generally try to rejoin the flock
- When frightened, the flock should scatter in believable patterns

## Technical constraints

- The game should be build in a single index.html file
- The game should be build using HTML, CSS and JavaScript
- It's okay to use external libraries when this is needed
- You will generate your own assets using basic shapes, but they should be recognizable (e.g., triangles for sheep, circles for the dog)
- The game should be playable on both desktop and mobile devices

## Features

- Players can control the dog using mouse or touch controls
- The dog barks when the player clicks or taps on the screen, making the sheep move faster
- The sheep show natural, realistic flocking behavior as the primary gameplay element
- The game increases in difficulty with more obstacles between the pen and the starting position of the sheep herd
- Obstacles can be static or dynamic (e.g., moving obstacles)
- Example obstacles include rock, trees, fences, rivers, roads (with cars), etc.
- Additionally, later in the game, wolves can appear. They don't attack until nightfall, but they scare sheep and can cause the herd to completely disperse
- The player must prevent wolves from scaring the sheep to succeed
- It should have at least 10 levels
- Include a start screen, a game over screen, and a win screen
- Have a timer that counts down to nightfall
- Have a score that increases with each sheep herded into the pen
- Include an option to restart the game after a game over
- Include an option to go to the next level after a win
- Include an option to go back to the start screen after a win or game over
- Game progress should be stored between sessions (using local storage)

Make sure the game is fun to play and is visually appealing, even with simple shapes. The realistic flocking behavior should be the standout feature that makes the game engaging and distinctive.
```
