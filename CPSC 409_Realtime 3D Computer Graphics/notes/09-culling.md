# Culling

## View Frustum Culling
- On the CPU side, objects that fall outside of the camera View Frustum are not rendered
- You can use various bounding box shapes for view frustum culling; for example, sphere or axis-aligned bounding box (AABB)

## Occlusion Culling
- Completely occluded objects are not rendered
- If any part of the object's bounding box is visible, the object is rendered

## Back-Face Culling
- The front/backs of triangles may not need to be rendered depending on the camera angle
