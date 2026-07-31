*This project was developed by amkhelif as part of the 42 School curriculum.*

The goal of cub3D is to create a 3D game from a 2D map using the Raycasting algorithm.

1. Raycasting
For a 1920-pixel screen, 1920 rays are cast from the player. Each ray moves forward until it hits a wall. The distance is then calculated: the farther the wall, the smaller it is drawn.

2. DDA
This is the algorithm that moves the ray efficiently. Instead of moving little by little, it visionally jumps the ray from cell to cell on the grid until it encounters a wall (`1`).

Step 1: Parsing
- **File:** Verifying the `.cub` extension.
- **Textures:** Reading the file and verifying the existence of `.xpm` images.
- **Colors:** Color validation (digits only, between 0 and 255).
- **Map:** Ensuring it is completely enclosed by walls and that there is only one player (whose position is saved).

Step 2: Initialization
If the map is valid, the game engine is prepared. The player is placed in the center of their cell (+0.5) and their direction (`dir_x`/`dir_y`) as well as their camera plan (`plane_x`/`plane_y`) are initialized.

Step 3: 3D Engine
The MLX loops infinitely on the `draw_map` function. For each generated frame:
- The direction of the 1920 rays is calculated.
- DDA advances each ray to the wall.
- The found distance is used to calculate the wall height to be drawn on the screen.

Step 4: Movements and Collisions
*(Files: move.c, player_move.c, player_move_utils.c)*
- **Movements:** Calculated by multiplying the direction or the camera by a speed value.
- **Collisions:** Before moving, the next step is simulated. If the next cell is a wall (`1`), a space, or `\t`, the player is blocked.
- **Rotation:** The arrow keys rotate the camera using a mathematical rotation matrix.

Instructions
**Execution:** ./cub3D map/valid_01.cub

Resources
- Lodev Tutorial
- MiniLibX Documentation
- Artificial Intelligence (for translating this README into English and helping understand the Lodev tutorial)