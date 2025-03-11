# Circle/Line Segment Collisions

In order to calculate if a circle and a line segment are in collision, we have to find the point on the line segment that is closest to the circle. Once we have that distance, we can compare it to the radius of the circle. If it is smaller than the radius, they are in collision. If not, they are not in collision.

To calculate the point on a line segment that is closest to a circle, we start by find the point on an infinite line that is closest to the circle. We then "clamp" that point onto the line segment to get the closest point on the line segment.

## Point on Infinite Line

The steps to finding the closest point on an infinite line and a circle are as follows:
- Find the tangent of the line
- Calculate the distance on the line to the closest point to the circle
- Calculate the coordinate on the line that is closest to the circle

### Tangent of the Line

To find the point on a line that is closest to a circle, we start by finding the tangent. We start with the line equation $Ax+By+C=0$, remembering that $A$ is $rise$ and $B$ is $-run$. The tangent is therefore $(-B, A)$. However, we always normalize vectors when they are tangents, so we will actually use $|(-B, A)|$.

### Distance to the Nearest Point

We can find the distance to the nearest point by taking the dot product between the tangent and the difference between a point on the line and the center of the circle. If the choose point $two$ on the line and the center of the circle is at $circle$, then the equation for the difference is $(center_x-two_x, center_y-two_y)$. The dot product therefore $tangent\cdot difference$ or $(-B, A)\cdot (center_x-two_x, center_y-two_y)$. This is the distance between $two$ and the closest point on the line to the circle, which we will call $distance$.

### Coordinate on the line that is closest.

We can find the coordinate on the infinite line that is closest to the circle by moving in the direction of the tangent the distance defined in the previous equation. We do this by scaling the tangent by $distance$ and adding it to $two$. Mathematically, this is $two+distance\cdot tangent$. This is the closest point on the infinite line.

## Clamping the Point on the Infinite Line

The closest point on the infinite line is not what we want, we want the closest point on the line segment. To find the closest point on the line segment, we determine if the point is on the line segment. If it is, we are done. If not, we determine which side of the line segment it is one. If it is closer to $one$, we clamp the value to $one$ and if it is closer to $two, we clamp it to $two$.

To see if the nearest point  is between $one$ and $two$, we first find the distance between one of the points and the nearest point. We then then see if that distance is less than the length of the line. If it is, then the nearest point is between the points. Otherwise we clamp it.

To do this, we first find the difference between $two$ and the nearest point. We then find the length of that difference. If the length is less than the length of the line, we are done. If the length is greater than the length of the line, we clamp to $one$. If the length is negative, we clamp to $two$.

## Example

Consider a line segment between points $(0,0)$ and $(50, 50)$. Consider also a circle at $(35, 15)$ with a radius of 10. Does this circle intersect the line segment? (You can see a graph of this problem here: https://www.geogebra.org/calculator/jtpwps8s).

- We start by finding the equation of the line. The equation is $Ax+By+C=0$ where $A$ is 1, $B$ is -1, and $C$ is 0.
- We then find the tangent, which is $(1, 1)$. Normalizing, we get $(1/\sqrt(2) ,1/\sqrt(2))$.
- We find the difference between $center$ and point $two$. $difference=center-two=(35-50, 15-50)=(-15, -35)$.
- We use the dot product to find the distance on the infinite line between $two$ and the nearest point.  $distance=dot(tangent, difference)=dot((1/\sqrt(2), 1/\sqrt(2)), (-15, -35))=1/\sqrt(2)\cdot -15 + 1/\sqrt(2)\cdot -35=(-15-35)/\sqrt(2)\approx -35.5$.
- We find the coordinate of the nearest point by adding scaling the tangent by the distance. We add this to $two$ to find the nearest point. $nearest=two+tangent\cdot distance=(50, 50)+(1/\sqrt(2),1/\sqrt(2)\cdot -35.5)=(50-35.5/\sqrt(2), 50-35.5/\sqrt(2))=(50-25.1, 50-25.1)\approx (25,25)$

Thus the nearest point on the infinite line is at $(25,25)$.

Next we need to clamp this point as follows:
- We find the difference between $two$ and the nearest point. $difference=two-nearest=(50, 50)-(25,25)=(25,25)$.
- We then find the length of this difference. $||(25, 25)||=35.3$
- We then find the length of the line segment. $||two-one||=||(50-0, 50-0)||= 70.7$
- Since $35.5<70.7$, we know the nearest point is on the line segment. If the length had been greater than 70.7, we would have clamped to $one$. If the length was negative, we would have clamped to $two$.

Now that we know the closest point on the line segment, we can calculate the distance between the circle and the nearest point. If the distance is less than the radius of the circle, we are in collision. Otherwise, we are not in collision.

- The difference between the nearest point and the circle center is $nearest-center=(25-35, 25-15)=(-10, 10)$.
- The length of this difference is $||(-10,10)=14.1$.

Since the radius of the circle is 10, and 14.1 is greater than 10, we know the circle and the line segment are not in collision.


