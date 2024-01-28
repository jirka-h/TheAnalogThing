# Bouncing Ball

The [FIRST STEPS](../THAT_First_Steps.pdf) describes in chapter 9.9 a Bouncing Ball System. 

I have focused only on height simulation. The critical part is the bouncing itself when the ball hits the ground. 

The system is modelled by this equation:

#### Free fall with drag at y > -1
y"(t) = -g - d * y'(t)

#### Bouncing action - ball is bellow floor at y < -1
y"(t) = -g - d * y'(t) + c * (-y(t) - 1) for y(t) < -1 bouncing action

*  y(t) is the vertical displacement (at start y = 1, floor is at y = -1, the ball goes bellow y = -1 when it bounces of)
*  y'(t) is the velocity (positive when the ball goes up, negative when it goes down)
*  y"(t) is the acceleration
*  d is the drag. Drag force is - d * y' and it's directed against the velocity.  When object falls, y'<0 and drag force is positive (up). When ball rises, y'>0 and drag force is negative (down).
*  c is the spring coefficient for bouncing of the ground. (Force from floor is directed up and equvals  c * (-y - 1). For example, for y = -1.1, we will get c * 0.1 )

