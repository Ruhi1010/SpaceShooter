# 🚀 SKY DOMINATION - Modern Air Combat

A modern arcade-style 2D air combat game built using **Pygame**. The player controls a fighter jet to shoot enemies, avoid collisions, and survive as long as possible while progressing through increasing difficulty levels.

---

## 📦 Features

- **Modern Visuals**: Neon and modern-style color palette.
- **Custom Aircraft Designs**: Player and enemy planes are rendered with realistic details.
- **Particle Effects**: Engine exhausts, bullet trails, explosions.
- **Game HUD**: Score, level, health bar, enemy counter.
- **Animated Main Menu** and **Game Over screen**.

---

## 🛠️ Modules and Classes

### `Star`
Simulates background stars for parallax scrolling effect.

- `x`, `y`: Position
- `speed`: Movement speed
- `brightness`, `size`: Appearance
- `update()`: Moves star left; respawns on the right if off-screen
- `draw(screen)`: Renders star as a glowing dot

---

### `Particle`
Handles short-lived particles for visual effects (explosions, exhausts, etc.).

- `x`, `y`: Position
- `vx`, `vy`: Velocity
- `color`, `size`: Appearance
- `life`: Particle lifetime counter
- `update()`: Updates position and shrinks size over time
- `draw(screen)`: Draws fading particle

---

### `Player`
Represents the player's jet aircraft.

- `x`, `y`: Position
- `speed`: Movement speed
- `bullets`: Active bullets fired
- `engine_particles`: Engine exhaust trail
- `update()`: Handles movement, shooting, and updates bullets/particles
- `draw(screen)`: Renders the aircraft and all its parts (body, cockpit, wings, etc.)
- `get_rect()`: Returns collision rectangle for hit detection

---

### `Enemy`
Represents enemy aircraft.

- `x`, `y`: Position
- `speed`: Horizontal movement
- `engine_particles`: Exhaust trail
- `color`: Randomized neon color
- `health`: Placeholder (not used extensively)
- `update()`: Moves left, emits particles
- `draw(screen)`: Draws enemy shape
- `get_rect()`: Returns collision rectangle

---

### `Bullet`
Projectile fired by player.

- `x`, `y`: Position
- `speed`: Velocity
- `color`, `width`, `height`: Appearance
- `update()`: Moves bullet forward
- `draw(screen)`: Renders glowing bullet
- `get_rect()`: Returns hitbox

---

## 🎮 `Game` Class

Main game controller and loop manager.

### Attributes

- `screen`: Pygame display surface
- `clock`: For framerate control
- `player`: Player object
- `enemies`: List of enemy objects
- `particles`: Explosion effects
- `stars`: Starfield background
- `score`, `level`: Game progress stats
- `enemy_spawn_timer`: For controlling spawn rate
- `game_over`, `game_started`: Flags for state management
- `menu_selection`: Main menu index

---

### Key Methods

#### `draw_menu()`
- Animated background and glowing title
- Navigation between `START MISSION` and `QUIT`
- Control instructions

#### `spawn_enemy()`
- Adds new `Enemy` objects at random vertical positions
- Spawn rate increases with level

#### `create_explosion(x, y, color)`
- Generates a burst of particles at a given location

#### `handle_collisions()`
- Checks for:
  - Bullet-to-enemy collisions (score gain, explosion)
  - Player-to-enemy collisions (health loss, game over)

#### `draw_hud()`
- Displays:
  - Score (💰)
  - Level (⚡)
  - Health bar (❤️)
  - Enemy count (🎯)
- Includes gradient effect and neon-styled borders

#### `draw_game_over()`
- Semi-transparent overlay with stats:
  - Final Score
  - Level Reached
  - Enemies Defeated
- Options to restart or quit

#### `reset_game()`
- Resets all gameplay values to initial state

#### `run()`
- Main game loop:
  - Processes user input
  - Updates game state
  - Renders screen
  - Handles transitions between menu, gameplay, and game over

---

## 🕹️ Controls

- `Arrow Keys`: Move aircraft
- `Spacebar`: Shoot double bullets
- `R`: Restart (on game over)
- `Q`: Quit (on game over or menu)

---

## 📊 Game Progression

- Score increases by **100** per enemy destroyed
- Level increases every **1000 points**
- Spawn rate increases with level (max spawn speed: 30 frames)

---

## 🧠 Collision Logic

```python
bullet.get_rect().colliderect(enemy.get_rect())
enemy.get_rect().colliderect(player.get_rect())
```
___
