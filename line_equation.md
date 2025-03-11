# $y=mx+b$
The standard line equation is $y=mx+b$. $m$ in this equation is the slope, or $rise/run$. $b$ is the y-intercept. Note that if we put $(run, rise)$ in a vector, that would give us the vector that is tangential to the line. 

## Calculating $y=mx+b$
To find $y=mx+b$ for a line made up of points $one$ and $two$, we first calculate the slope (by finding rise over run) and then figure out the value of $b$ (which is the y-intercept). 

Here is an example. Consider the line made up of the points $(0, 1)$ and $(1, 2)$.  We find $run$ by subtracting the $y$ components of the points and we find $run$ by subtracting the $x$ components of the points. This gives us $rise=2-1=1$ and $run=1-0=1$. $m$ is calculate by taking $rise/run$, which gives us $m=1/1$ or $m=1$. We now know that $y=1\cdot x+b$. To find b, we plug in one point for $x$ and $y$ and then do some algebra. If we plug in the first point, $(0, 1)$ for $x$ and $y$, our equation becomes $1=1\cdot 0 + b$. This simplifies to $1=0+b$ or $b=1$. With $b$, we now know the formula for the line: $y=1\cdot x+1$.

## Problem with $y=mx+b$
$y=mx+b$ is problematic because it cannot represent vertical lines, something used extensively in games. When a line is vertical, the value for $run$ is 0. $rise/0$ is undefined, meaning we can't represent vertical lines. The solution is to find a new equation that can handle lines of all angles, specifically including vertical lines.


# $Ax+By+C=0$
An equation that can handle vertical lines is $Ax+By+C=0$. We can derive this from $y=mx+b$ as follows:
- Rewriting $y=mx+b$ using $rise/run$, it becomes $y=rise/run\cdot x + b$.
- Multiplying both sides by $run$, we get $run\cdot y = rise\cdot x + run\cdot b$. 
- Moving $y$ to the other side, we get $rise\cdot x - run\cdot y + run\cdot b=0$. 
- Let's introduce some constants. If $A$ is $rise$, $B$ is $-run$ and $C$ is $run\cdot b$, then we get $Ax+By+C=0$. This is the standard equation for lines used in games.

In this form, $(A, B)$ is a vector that is orthogonal (or perpendicular) to the line in question. $C$ represents the closest distance from the line to the origin.Notice that this form can represent vertical lines since we don't store the slope as a quotient ($rise/run$), but as two numbers, A and B. If a line is vertical, $B$ is 0, but that doesn't prevent us from representing the line.

## Calculating $Ax+By+C=0$
To calculate $Ax+By+C=0$, we follow very similar steps to calculating $y=mx+b$. We first find $rise$ and $run$ to find $A$ and $B$, we plug in a point, and we use algebra to find $C$.

Here is an example. Consider a line made up of the points $(0, 1)$ and $(1, 2)$. We find We find $run$ by subtracting the $y$ components of the points and we find $run$ by subtracting the $x$ components of the points. This gives us $rise=2-1=1$ and $run=1-0=1$. $A$ is the same is $rise$ and $B$ is $-run$. Thus, in this example, $A=1$ and $B=-1$. At this point the equation of our line is $1\cdot x + -1\cdot y + C = 0$. Next, we then plug in a point. Again we will use $(0, 1)$. This gives us $1\cdot 0+-1\cdot 1 + C=0$. Simplifying, we get $-1+C=0$ or $-1=-C$ or $C=1$. Putting this in our equation, the equation of the line is $1\cdot x + -1\cdot y + 1=0$. Some algebra will show that this equation is the same as the one found with $y=mx+b$, $y=1\dot x + 1$.

## Dot product simplification
We can simplify this process, and make it easier when we are programming, by using a dot product. The dot product of two vectors $i$ and $j$ is written as $i\cdot j$. The dot product is calculated is $i_x\cdot j_x+i_y\cdot j_y$.  Notice that the beginning of our line equation is $A\cdot x+B\cdot y$. This is the same as the dot product of the vectors $(A,B)$ and $(x,y)$. We can therefore rewrite the line equation as $(A,B)\cdot (x,y)+C=0$. Rewriting this, we get $C=-(A,B)\cdot (x,y)$. Since we already know that $A=rise$ and $B=-run$, we can rewrite this as $C=-(rise, -run)\cdot (x,y)$. Since $(x,)$ can be found by taking either point that define our line, we can calculate $A$, $B$, and $C$ as follows:

```javascript
let A = two_y-one_y
let B = -(two_x-one_x)
let C = -(dot(A, B, one_x, one_y))
```

