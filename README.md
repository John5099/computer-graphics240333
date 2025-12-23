Algorithm (mid point circle)
1. Input radius r and circle centre (xc
, yc), then set the coordinates for the first point on the
circumference of a circle centred on the origin as:
( x<sub>0</sub> , y<sub>0</sub>) =(0 , r )
2. Calculate the initial value of the decision parameter as:
    p<sub>0</sub>=5/4-r
3. Starting with k = 0 at each position xk, perform the following test. If pk < 0, the next point
along the circle centred on (0, 0) is (xk+1, yk) and:
p<sub>k+1</sub> =p<sub>k</sub>+2x<sub>k+1</sub>+1
Otherwise the next point along the circle is (xk+1, yk-1) and:
p<sub>k+1</sub>=p<sub>k</sub>+2x<sub>k+1</sub>+1-2y<sub>k+1</sub>
4. Determine symmetry points in the other seven octants
5. Move each calculated pixel position (x, y) onto the circular path centred at (xc
, yc) to plot thecoordinate values:
6. Repeat steps 3 to 5 until x >= y
  x=x+x<sub>c</sub>  y=y+y<sub>c</sub>
