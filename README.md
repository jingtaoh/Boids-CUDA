# Boids

Flocking simulation using CUDA based on Reynolds Boids Algorithm, along with two levels of optimiation: uniform grid and uniform grid with semi-coherent memory access. 
- Tested on: Windows 10, Intel(R) Xeon(R) CPU E5-2667 v3 @ 3.20GHz, NVIDIA Quadro P5000

## Implementation

### Naive Boids Simulation

In the Boids flocking simulation, particles representing birds or fish (boids) move around the simulation space according to three rules:

1. cohesion - boids move towards the perceived center of mass of their neighbors
```
function rule1(Boid boid)

    Vector perceived_center

    foreach Boid b:
        if b != boid and distance(b, boid) < rule1Distance then
            perceived_center += b.position
        endif
    end

    perceived_center /= number_of_neighbors

    return (perceived_center - boid.position) * rule1Scale
end
```
2. separation - boids avoid getting too close to their neighbors
```
function rule1(Boid boid)

    Vector perceived_center

    foreach Boid b:
        if b != boid and distance(b, boid) < rule1Distance then
            perceived_center += b.position
        endif
    end

    perceived_center /= number_of_neighbors

    return (perceived_center - boid.position) * rule1Scale
end
```
3. alignment - boids generally try to move with the same direction and speed as their neighbors
```
function rule3(Boid boid)

    Vector perceived_velocity

    foreach Boid b
        if b != boid and distance(b, boid) < rule3Distance then
            perceived_velocity += b.velocity
        endif
    end

    perceived_velocity /= number_of_neighbors

    return perceived_velocity * rule3Scale
end
```

### Uniform Grid

### Semi-Coherent Uniform Grid

## Performance Analysis

## Renferences
