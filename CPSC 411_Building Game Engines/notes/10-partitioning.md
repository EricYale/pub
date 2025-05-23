# Partitioning
- Spatial partitioning is used when we need to look up objects within a certain location bounding box, i.e. for collisions, occlusion culling, or audio
- We can use a data structure to make spatial partitioning easier

## Different Data Structures
- Fixed Grid
    - Each cell stores a list of units within its boundaries
    - Checks are only performed on units in the same cell
- Quad Tree
    - Quad trees divide the world (and each sub-division) into four quadrants
    - Regions which are more dense are subdivided further
