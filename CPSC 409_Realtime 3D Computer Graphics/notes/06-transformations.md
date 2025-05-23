# Transformations
- Transformations are encoded as matrices

## Affine Transformations
- Affine transformations are transformations that preserve points, straight lines, and planes
- We need an extra row/column because we need to represent translations (remember that the origin always stays the same in normal linear transformations)
    - So for 3D points, we'll have a 4D matrix

### Common Affine Transformations

#### Scaling
$$
\begin{bmatrix}
    s_x & 0 & 0 & 0 \\
    0 & s_y & 0 & 0 \\
    0 & 0 & s_z & 0 \\
    0 & 0 & 0 & 1
\end{bmatrix}
$$

#### Shearing
$$
\begin{bmatrix}
    1 & s_{xy} & s_{xz} & 0 \\
    0 & 1 & s_{yz} & 0 \\
    0 & 0 & 1 & 0 \\
    0 & 0 & 0 & 1
\end{bmatrix}
$$

#### Rotation

Ex. Rotation around the Z axis
$$
\begin{bmatrix}
    \cos \theta & -\sin \theta & 0 & 0 \\
    \sin \theta & \cos \theta & 0 & 0 \\
    0 & 0 & 1 & 0 \\
    0 & 0 & 0 & 1
\end{bmatrix}
$$

- A `1` appears in whichever axis you are rotating about
- Be careful of gimbal locking

#### Reflection

$$
\begin{bmatrix}
    1 & 0 & 0 & 0 \\
    0 & -1 & 0 & 0 \\
    0 & 0 & 1 & 0 \\
    0 & 0 & 0 & 1
\end{bmatrix}
$$

#### Translation

$$
\begin{bmatrix}
    1 & 0 & 0 & t_x \\
    0 & 1 & 0 & t_y \\
    0 & 0 & 1 & t_z \\
    0 & 0 & 0 & 1
\end{bmatrix}
$$

- The _w_ (last) coordinate is set to `1` for points, and `0` for vectors
    - Such that vector + point = point

## World Space vs Local Space
- Local space is the positions of the points, relative to their model
- World space is the absolute positions of the points
