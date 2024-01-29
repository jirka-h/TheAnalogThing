# Bouncing Ball

The [FIRST STEPS](../THAT_First_Steps.pdf) describes in chapter 9.9 a Bouncing Ball System. 

I have focused only on height simulation. The critical part is the bouncing itself when the ball hits the ground. 

The system is modeled by this equation:

#### Free fall with drag at y > -1
y"(t) = -g - d * y'(t)

#### Bouncing action - the ball is bellow floor at y < -1
y"(t) = -g - d * y'(t) + c * (-y(t) - 1) for y<-1, meaning that ball is under the floor

*  y(t) is the vertical displacement (at start y = 1, floor is at y = -1, the ball goes bellow y = -1 when it bounces of)
*  y'(t) is the velocity (positive when the ball goes up, negative when it goes down)
*  y"(t) is the acceleration
*  d is the drag. The drag force is `-d * y'`, and it's directed against the velocity.  When the object falls, `y'<0` and the drag force is positive (up). When the ball rises `y'>0`, and the drag force is negative (down).
*  c is the spring coefficient for bouncing off the ground. (The force from the floor is directed up and equals  `c * (-y - 1)`. For example, for y = -1.1, we will get bouncing force `c * 0.1` )

## Bouncing action
`c * (-y - 1) for y<-1` is implemented via 10V Zener diode. -1 unit value is represented by voltage of -10V. This is inverted, so when voltage drops below -1, voltage at inverter output is over 10V, and Zener diode becomes conductive. The current flows to the SJ (Summing Junction) pin of the integrator, so it directly charges the capacitor in inverter. However, this works as intended only when the velocity before impact is the same as the velocity after the impact. On my THAT computer, this is different. The current through the Zener diode is asymmetrical, leading to exit velocity being higher than impact velocity. This breaks the model. 

I have attempted to use a comparator instead, with the following inputs:
*  A: y
*  B: +1
*  A+B>0: GND
*  A+B<0: 1

This creates a square wave, but because of comparator hysteresis, exit velocity is still higher than impact velocity. Finally, I partially mitigated the problem by connecting all four diodes from THAT board after the Zener diode. This makes the current lower, increasing charging time from 160 to 210 microseconds, but the disproportion between exit and impact velocity was lower. 
