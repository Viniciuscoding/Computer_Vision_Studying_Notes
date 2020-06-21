# Lesson 15 - Perspective Imaging

NOTE (Homegenous Coordinates): ``` Homogeneous coordinates are invariant under scale ```

NOTE (Perpective Projections): ``` Projection is a matrix multiply using homogeneous coordinates ```

### Project Equations

- Compute intersection with Perspective Projection of ray from (x, y, z) to COP.
- Derived using similar triangles.

### Formula
```(X, Y, Z) -> (-d(X/Z), -d(Y/Z), -d)```
**Note: Distant objects are smaller**

**Homogeneous Coordinates**
- It is not a linear transformation

**Geometric Properties of Projection**
- Points got to points.
- Lines go to lines.
- Polygons go to polygons.

### Vanishing points
```
Parallel lines in the world meet in one point in an image.
Parallel lines converge in one point too in Mathematics.
```

1. Each set of parallel lines meets at a different point.
2. Sets of parallel lines on the same plane lead to collinear vanishing points. This is what we call the horizon in real life.
3. 3 Points Perspective: Different directions correspond to different vanishing points.
- If you have a cube in the air this sets three parallel lines (right face, left face, underneath face).

What determines at what point in the image parallel lines intersect?
A: The direction of the lines have in the world and the orientation of the camera.

**Other Models:** Orthograpphic Model and Weak Perspective.

**Model**       |  **3D Point Position**  |  **2D Image**
Perspective     |             (x, y, z)       (fx/z, fy/z) 
Weak Perspective|             (x, y, z)       (fx/z0, fy/z0)
Orthographic    |             (x, y, z)       (x, y)










