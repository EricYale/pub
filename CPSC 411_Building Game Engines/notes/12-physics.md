# Physics

**Types of bodies**
- Rigidbody: non-deformable
- Softbody: deformable (less performant)

**Jobs of a physics engine**
1. Integration: initial movement of bodies (velocity, acceleration, forces)
2. Detection: detects collisions between bodies
3. Resolution: sorts out the result of the collisions—after a collision, no two bodies should be intersecting

## Integration
Integration is pretty simple:
```c
velocity += acceleration * deltaTime;
position += velocity * deltaTime;
```
## Collision Detection
- Sphere-Sphere: check if the distance is less than the sum of the radii
- Axis-Alogned Bounding Box: check if one non-rotated rectangle intersects with another
- Oriented Bounding Box: check if two rotated rectangles intersect
- Convex hull: check if two convex polygons intersect (making a convex hull is a good enough approximation to make computation cheaper)
- Concave polygons: unfortunately we have to check intersection with every segment

**Optimizations**
- Broad-Phasing collision: "spatially partition" the world and only check collisions for objects that are near to each other
    - We can use a quad tree for this
- Sweep and prune: you can do a sweep along the x axis, sorting objects by position along that axis; keep a list of objects that are within the current x value

## Resolution
- Constraint-based: solve iteratively (frame-by-frame)
    - Problem: we have to determine which objects to resolve first
- Impulse-based: intersecting objects bounce off one another a set amount
- Tile-based: based on "feel" (e.g. coyote time); used for platformers
