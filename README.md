# Midpoint Ellipse Drawing Algorithm

The Midpoint Ellipse Algorithm is a raster graphics algorithm used to draw an ellipse efficiently using incremental calculations and symmetry, avoiding floating-point operations inside the main drawing loops.

Input: semi-major axis rx, semi-minor axis ry, and ellipse center (xc, yc).

Algorithm:
1. Read values of rx, ry, and the center coordinates (xc, yc). Initialize the starting point of the ellipse centered at the origin as (x0, y0) = (0, ry). Set x = 0 and y = ry.

2. Compute the initial decision parameter for Region 1 as:
   p1 = ry² − (rx² × ry) + (1/4 × rx²)

3. Region 1 (slope > −1): At each x position, if p1 < 0, select the next point as (x + 1, y) and update the decision parameter using:
   p1 = p1 + 2·ry²·x + ry²
   Otherwise, select the next point as (x + 1, y − 1) and update:
   p1 = p1 + 2·ry²·x − 2·rx²·y + ry²
   Continue this process until 2·ry²·x ≥ 2·rx²·y.

4. The last point obtained in Region 1 becomes the starting point for Region 2. Compute the initial decision parameter for Region 2 as:
   p2 = ry²(x + 0.5)² + rx²(y − 1)² − rx²·ry²

5. Region 2 (slope ≤ −1): At each y position, if p2 > 0, select the next point as (x, y − 1) and update:
   p2 = p2 − 2·rx²·y + rx²
   Otherwise, select the next point as (x + 1, y − 1) and update:
   p2 = p2 + 2·ry²·x − 2·rx²·y + rx²
   Continue until y = 0.

6. For every calculated point (x, y), determine the symmetric points in the remaining three quadrants:
   (x, y), (−x, y), (x, −y), (−x, −y).

7. Translate each point from the origin to the actual ellipse center using:
   X = x + xc, Y = y + yc
   Plot the pixel at (X, Y).

Output: A complete ellipse drawn using midpoint calculations with symmetry and incremental updates.

