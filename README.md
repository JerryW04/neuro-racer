# Neuro Racer

Neural-network cars learn to drive through evolution — no driving logic is ever programmed.
Draw your own track and watch them figure it out.

**Play it:** https://jerryw04.github.io/neuro-racer

## How it works

Each of the 36 cars is controlled by a tiny multilayer perceptron (6 → 7 → 2): five
raycast distance sensors plus current speed go in, steering and throttle come out.
A genetic algorithm evolves the population — fitness is progress along the track's
checkpoints, the top performers are kept (elitism), and the rest of each generation
is bred via uniform crossover and Gaussian mutation. Crashing off the road, or
loitering without progress, ends a car's run.

Tracks are rasterized into a pixel mask, which powers both collision detection and
the sensor raycasts — which is what makes **arbitrary hand-drawn tracks** work: draw
any shape in one stroke (end near your start point to create a lap-able loop) and the
cars immediately begin learning it. Brains persist across track changes, so you can
test whether what they learned on one circuit transfers to another.

Extras: live fitness chart per generation, sensor visualization on the current best
car, and a ×5 fast-forward for impatient evolution.

## Tech

- Vanilla JavaScript + HTML5 Canvas — no libraries, no build step, no server
- Hand-rolled neural network (forward pass on flat Float32Arrays)
- Genetic algorithm: elitism, uniform crossover, Gaussian mutation
- Pixel-mask collision & raycasting for arbitrary user-drawn geometry

## Run locally

Open `index.html` in a browser.

## Deploy on GitHub Pages

1. Create a public repo named `neuro-racer`
2. Add `index.html` and this `README.md`, commit, push
3. **Settings → Pages → Deploy from a branch → main / (root)**
4. Live at `https://<username>.github.io/neuro-racer`
