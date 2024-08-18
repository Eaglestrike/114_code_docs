# ⚪114’s Git Workflow

1.  **Work in branches** NOT in main

We keep the latest working version of code in the main branch of the
repository. If someone is working on a subsystem or an improvement, they
create a separate branch and work there. This way we always have an
easily accessible branch of working code. In general we try to keep the
main branch clean.

2.  Create **pull requests for code reviews** OR to merge into main if your branch is tested and approved by the code lead

It’s only after that branch has been tested on the robot and approved by
the code lead do they create a pull request, asking to be merged to
main. Pull requests can also be used for code reviews. A good example of
this is [<u>this old
PR.</u>](https://github.com/Eaglestrike/2024-RobotCode/pull/2)

3.  New branches for every conceptual change

To avoid merge conflicts, create new branches for every conceptual
change to the robot. For example if you’re working on a subsystem like an intake and
suddenly find a way to improve the controller class, you’d have to open
a new branch called controller-class-improvement or something