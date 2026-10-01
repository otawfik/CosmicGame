
# 🪐 Cosmic Explorer

### [🚀 CLICK HERE TO PLAY THE GAME](https://otawfik.github.io/CosmicGame/)

**Cosmic Explorer** is an interactive educational arcade game where you explore the solar system. Click on a planet to launch a unique mini-game based on that planet's actual scientific conditions (gravity, atmosphere, wind speed, etc.).

![Solar System](https://img.shields.io/badge/Status-Playable-brightgreen) ![Tech](https://img.shields.io/badge/Built%20With-React%20%7C%20Canvas-blue)

## 🎮 The Missions

| Planet | Mission | Mechanic |
| :--- | :--- | :--- |
| **Mercury** | Solar Flare Survival | Bullet-hell dodger |
| **Venus** | Acid Ascension | Reverse-lander thrust game |
| **Earth** | Orbital Defense | Radial defense (Pong-style) |
| **Mars** | Red Rover Drift | Top-down driving physics |
| **Jupiter** | Gravity Well | Orbital mechanics simulator |
| **Saturn** | Ring Racer | Vertical high-speed scroller |
| **Uranus** | Atmosphere Harvester | Catch & Avoid |
| **Neptune** | Diamond Rain | Wind resistance survival |

## 🧮 Built on Linear Algebra

The game world is the vector space R². Every position, velocity, and direction is a vector in R², and every rotation is an explicit 2x2 rotation matrix

    R(θ) = | cos θ  −sin θ |
           | sin θ   cos θ |

All of it lives in the `LA` linear algebra core at the top of `index.html`: vector construction, addition, subtraction, scalar multiplication, dot products, Euclidean norms, normalization, and rotation matrices with both matrix-vector and matrix-matrix products.

Where it shows up in the games:

- **Mercury**: projectile velocity = R(aim)·(speed, 0), the rotation matrix applied to the x basis vector. Movement is the vector update p += v·dt via scalar multiplication.
- **Earth**: the pointer direction becomes a vector, and debris spawn positions and inward velocities are R(a)·(300, 0) and R(a)·(−100, 0). The shield blocks debris when the dot product of the two unit direction vectors exceeds cos(0.5), which is the old angle comparison rewritten as pure linear algebra.
- **Mars**: the rover's forward vector = R(heading)·(150, 0). Steering composes rotations as a matrix-matrix product, R_new = R(turn·dt)·R(heading), then reads the new heading back out.
- **Jupiter**: orbital position = center + R(θ)·(radius, 0), vector addition of the rotated radius vector onto the planet center.
- Even the menu's CSS orbit animations are matrix transforms under the hood.

No game engine. Just math.

## 🛠️ How to Run Locally

If you want to run the code on your own machine:

1. Clone this repository.
2. Open `index.html` (or `standalone.html`) using a local server.
   - **VS Code:** Right-click -> "Open with Live Server".
   - **Python:** Run `python3 -m http.server` in the folder.
3. The game runs 100% offline with no API keys required.

## 🎨 Artist's Statement
This project bridges the gap between abstract planetary data and interactive experience. By translating physical constants—like Jupiter's gravity or Neptune's wind velocity—into gameplay variables, Cosmic Explorer allows players to *feel* the hostile environments of our celestial neighbors.
