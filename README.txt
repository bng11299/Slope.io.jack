Pseudo-3D Slope Game - inspired by Slope.io game

For the actual game, go to https://slopeio.org/

In this game, the player controls a ball rolling down a 3-lane road toward a vanishing point. Obstacles approach from the horizon and must be avoided by switching lanes or jumping. The score increases each time an obstacle is successfully passed.

Controls(COOKED):
left arrow: left
right arrow: right
space: jump (not in original game)


File Descriptions
Main.jack
Creates a SlopeGame instance, runs it, and disposes it when the game ends.
SlopeGame.jack
Main game loop. Each frame it reads keyboard input, updates all objects, checks for collisions, and redraws the screen. Also manages score, game state (playing / game over), and obstacle respawning.
Ball.jack
The ball. Tracks which of the 3 lanes you're in and slides its screen x position toward the target lane each frame. With a jump, the ball rises then falls back to the road over several frames.
Obstacle.jack
A single obstacle. Stores a lane (0, 1, or 2) and a depth value z. Each frame z decreases, moving the obstacle toward the player. Screen position and rendered size are both derived from z, so obstacles appear small at the horizon and large up close. When z goes negative the obstacle has passed the player — a passed flag is set for exactly one frame so SlopeGame can respawn it at a new lane and depth.
Road.jack
Draws the pseudo-3D road each frame. Renders the two outer road edges, two lane dividers, a bottom edge, and a horizon line — all converging at the vanishing point at the top centre of the screen. No animation; the 3D effect comes entirely from the obstacles and ball changing size and position as their depth changes.


"3D" function:
Initially, I tried to utilize the same logic as the Hackenstein game on the nand2tetris website, but it won't work since their game is technically step based, and new screens are created/reused each time. 
In this implementation, the road lines converge. All the road edges and lane dividers are drawn as straight lines meeting at the horizon line. This is a trick I learned from my second grade art class.
As obstacles approach the player, it gets drawn lower on the screen and becomes larger. By the time it reaches the player it is a large rectangle at the bottom of the screen. The countdown happens every frame, so it should go towards you without any framedrops(pray).

*Not updated as of April 16 2026. Will make README changes by April 19 2026

Workflow Plan:
Last week(spring break): scaffolding and most of the code(got "3d" working)
This week and next week: Projects 9 and 10, will NOT look at this to avoid a headache
After until end of semester: bugfixes, optimization, etc(you can only do one run at a time right now lol)

Notes: all the controls are COOKED(i think) but if you get it to work, spam tf out of space as SOON as you spawn.
