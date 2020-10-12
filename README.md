# Flywheel-Tuner
RoboRIO program for tuning a flywheel using REV Robotics sparkmax NEO motor(s)

A small WPILib project to quickly tune your REV Robotics NEO powered flywheel.

If you're using a Cross The Road Electronics (CTRE) motor you should use the CTRE Phoenix Tuner.

I highly recommend reading [this excellent artticle](https://trickingrockstothink.com/blog_posts/2019/10/19/tuning_pid.html) on how to tune PIDF for a flywheel. Follow the example in the sidebar to tune an imaginary flywheel.

## Tuning

![Example Tuning Output](https://raw.githubusercontent.com/FRC-Sonic-Squirrels/Flywheel-Tuner/master/TuningExample.png)

Start by importing the shuffleboard config (`shuffleboard_flywheel_tuner.json`) so that the output looks like the above image.

1. Set the CAN id to match the motor you are tuning.
2. Set the mode to Variable or Fixed
3. Start tuning. First, try to get the RPM close just changing the kF value and leave kP, kD, and kI zero. You want the kF value alone to get the RPM to just above the target setpoint. Tune with a setpoint close or a little over to your anticipated target RPM. Alternatively tune with an RPM that corrisponds to roughly 75% of max trottle.
4. Adjust the kP value to shorten the time it takes to reach the setpoint. Keep increasing it until, the RPM starts to overshoot and oscillate the setpoint, then back it off.
5. You probably won't need to adjust kI and the iZone. Only if the rpm falls short of the setpoint and it cannot be fixed using kF and kP.
6. You probably won't need to adjust kD either. Only if after tuning everything else that the system is still overreacting.

## Tuning Modes

There are two modes: *Fixed* and *Variable. 

In Fixed mode, use the Xbox controller A, B, Y, X, and right bumper buttons to toggle between RPM setpoints. The right bumber is zero RPM, A is 1000 RPM, B 2000 RPM, Y 3000 RPM, and X 4000 RPM.

In Variable mode, the left stick controls the setpoint RPM. 

## References

* <https://trickingrockstothink.com/blog_posts/2019/10/19/tuning_pid.html> Flywheel Tuning PIDF tuning theory explained (*Start Here*)
* <https://www.revrobotics.com/sparkmax-users-manual/#section-3-4> REV Robotics closed loop tuning instructions
* <https://phoenix-documentation.readthedocs.io/en/latest/ch16_ClosedLoop.html> CTRE closed loop tuning instructions
* <https://howdybots.org/wp-content/uploads/2019/12/Dont_Break_Your_Bot_Whitepaper-V1.pdf>  Howdybots Don't Break Your Bot

## Original REV Robotics Example Code

<https://github.com/REVrobotics/SPARK-MAX-Examples/tree/master/Java/Velocity%20Closed%20Loop%20Control>
