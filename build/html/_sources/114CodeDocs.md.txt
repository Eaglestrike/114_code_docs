# Table of contents

[**Table of contents 2**](#table-of-contents)

[**Informal Prerequisites 4**](#informal-prerequisites)

[**The Purpose of Code 5**](#the-purpose-of-code)

[**Getting started 6**](#getting-started)

> [WPILib VScode 6](#wpilib-vscode)
>
> [Installation 6](#installation)
>
> [Making a project 6](#making-a-project)
>
> [.h and .cpp files 8](#h-and-.cpp-files)
>
> [Why separate? 8](#why-separate)
>
> [The Robot Class 8](#the-robot-class)
>
> [Building and Deploying Code 9](#building-and-deploying-code)

[**Coding a motor 11**](#coding-a-motor)

> [Motors + Motor Controllers 11](#motors-motor-controllers)
>
> [Installing Vendor Libraries 12](#installing-vendor-libraries)
>
> [Using Vendor Libraries 12](#using-vendor-libraries)
>
> [TalonFX 12](#phoenix6)
>
> [REVLib 12](#revlib)

[**Motion Control** **13**](#control-theory)

> [Feedback Control 13](#feedback-control)
>
> [Bang-Bang Control 13](#bang-bang-control)
>
> [PID Control 13](#pid-control)
>
> [Tuning tips 16](#tuning-tips)
>
> [Implementation tips 17](#implementation-tips)
>
> [Shortcomings of PID 17](#shortcomings-of-pid)
>
> [Motion Profiles 17](#motion-profiles)
>
> [Trapezoidal motion profile 17](#trapezoidal-motion-profile)
>
> [Feedforward Control 17](#feedforward-control)

[**Coding as a team 19**](#coding-as-a-team)

> [Git and GitHub 19](#git-and-github)
>
> [Git Terms: 19](#git-overview)
>
> [Git Actions: 19](#try-it-yourself)
>
> [114’s Git Workflow 19](#s-git-workflow)
>
> [Team practices 20](#team-practices)
>
> [Style practices: 20](#style-practices)
>
> [Conceptual practices: 20](#conceptual-practices)
>
> [The Mechanism class 21](#the-mechanism-class)
>
> [The Controller class 21](#the-controller-class)
>
> [Shuffleboard Sender 21](#shuffleboard-sender)
>
> [Team Utils: 21](#team-utils)
>
> [Trapezoidal motion profile 21](#trapezoidal-motion-profile-1)
>
> [Timer 21](#timer)
>
> [Logger 21](#logger)
>
> [Poses 21](#poses)
>
> [Feedforward Auto Tuner 21](#feedforward-auto-tuner)

[**Other Resources 22**](#other-resources)

# Informal Prerequisites

Keep in mind that a lot of this can be learned on the go so if you don’t
know everything don’t sweat it. I’ve also provided links to learn these
things with c++ syntax for those of you who know the concepts in other
languages.

- Code knowledge (C++ specific)

  - Basics

    - primitive data types, if statements, variables, switch statements,
      > for loops, while loops

    - [<u>vectors</u>](https://www.geeksforgeeks.org/vector-in-cpp-stl/)/arrays,
      > functions, printing to console (std::cout \<\< “text” \<\<
      > std::endl)

  - Scope

    - [<u>Access
      > specifiers</u>](https://www.w3schools.com/cpp/cpp_access_specifiers.asp#:~:text=public%20%2D%20members%20are%20accessible%20from,be%20accessed%20in%20inherited%20classes.)
      > (public/private/protected)

  - Object oriented programming

    - [<u>Classes</u>](https://www.w3schools.com/cpp/cpp_classes.asp),
      > [<u>inheritance</u>](https://www.geeksforgeeks.org/inheritance-in-c/)
      > (C++ supports [<u>multiple
      > inheritance</u>](https://www.geeksforgeeks.org/multiple-inheritance-in-c/),
      > unlike Java),
      > [<u>constructors</u>](https://learn.microsoft.com/en-us/cpp/cpp/constructors-cpp?view=msvc-170)

    - Encapsulation (creating meaningful classes) and abstraction
      > (keeping internal stuff hidden) are practices we follow but not
      > super important and will improve the more you code

  - Data structures

    - [<u>Namespaces</u>](https://cplusplus.com/doc/oldtutorial/namespaces/),
      > [<u>Enums</u>](https://www.geeksforgeeks.org/enumeration-in-cpp/)

  - Optional stuff that will be useful later

    - [<u>Structs</u>](https://www.w3schools.com/cpp/cpp_structs.asp) if
      > you’re extra. It’s basically the same thing as a class but we
      > use them like little folders for variables. If that’s confusing,
      > ask me and I’ll show you an example.

    - [<u>Virtual
      > functions</u>](https://www.geeksforgeeks.org/virtual-function-cpp/)
      > (basically c++ equivalent of an abstract method in Java)

    - [<u>Pointers vs
      > references</u>](https://www.geeksforgeeks.org/pointers-vs-references-cpp/)
      > (and [<u>passing by
      > reference</u>](https://www.geeksforgeeks.org/cpp-functions-pass-by-reference/))

- A basic understanding of physics

  - Kinematics: know what position, velocity, and acceleration are

    - [<u>Lecture Video</u>](https://youtu.be/198u1x8TBTo)

  - Know that friction exists and always opposes motion

  - Know that gravity exists and acts on an object’s center of mass

- How FRC games work

  - Autonomous, Teleop

- Knowing calculus is helpful but not necessary

Keep in mind anything you don’t know can pretty easily be found online,
especially for syntax stuff and coding concepts.

That being said, these docs are written with the assumption the reader
understands everything mentioned at a very basic level.

# 🟠The Purpose of Code

From the code’s POV, the robot’s composed of **moving parts**: motors
and pneumatics, sensors: cameras, encoders and miscellaneous other
parts, and inputs from the driver. Coding is about utilizing and
integrating all the information given by the sensors and driver input to
make the moving parts move—that is how the robot functions. As such, to
actually make working code on the robot, a coder (you) must understand
how each part functions.

# ⚪Getting started

Understand how we write code that gets on the robot in the simplest
terms, and try deploying some code yourself.

## WPILib VScode

VScode is a code editing software that WPILib has built off of with
robotics and FRC in mind. WPILib VScode is the software we use to write
and edit all our code, manage projects, to build code, deploy code on
the robot, and more.

### Installation

Follow WPILib’s [<u>installation
guide</u>](https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html)
to install it.

It’s a really large file and will take a long time to download, so I’d
recommend **downloading at home**.

I’d also recommend **pinning the application** to a doc or keeping a
shortcut on your desktop. It’s time consuming to dig through all your
files to find the app otherwise.

If you already have the normal version of VSCode downloaded, I’d
recommend renaming the WPILib version to ‘WPILib VSCode \<year\>’ so you
can tell them apart.

## Making a project

Open WPILib VScode and click the
<img src="media/image4.png" style="width:0.42708in;height:0.46875in" />
button in the top right corner.

A navigation bar should pop up. Type in or select Create New Project
like
this:<img src="media/image9.png" style="width:6.5in;height:1.80556in" />

Edit the settings as follows:

<img src="media/image15.png" style="width:6.5in;height:2.22917in" />

Then select the base folder this project will be held in (it’s good
practice to keep all your projects in an isolated folder called
“robotics” or something), and name the project depending on what you’re
doing. When all the settings are correct, click “generate
project”.<img src="media/image1.png" style="width:1.81871in;height:2.77721in" />

After navigating to the project in VSCode, open the explorer

(on the left) with these files:

- src/main/cpp/Robot.cpp

- src/main/include/Robot.h

Don’t worry too much about the other folders and files; they’re just
specific to running robot
code.<img src="media/image7.png" style="width:2.33333in;height:1.73247in" />

Robot.h should look something like this:

<img src="media/image8.png" style="width:2.33333in;height:2.103in" />

And Robot.cpp something like this:

## .h and .cpp files

C++ has header (.h) and source code files (.cpp), which serve to make
build time quicker and to make the code cleaner to write and for others
to read and use.

A header file serves as a skeleton of the source code. It
defines/declares data structures like classes, although it should not
implement any of the things it defines (though it can).

**A source file implements the methods the header file defines**. This
is where all the logic and inner workings of the class is done.

For example if you look at Robot.h, the class Robot is declared to have
methods like RobotInit which are defined but not implemented. Although
the methods in Robot.cpp are currently empty, this is where the code
would be written.

### Why separate?

You can skip this part if you don’t care why (it’s not that important)

By separating the skeleton from the body of the code, it creates an
easily readable view of what a class is capable of doing, which makes
the class easier to understand for other people who want to use your
class. It also makes you more intentional about abstraction and
encapsulation when you’re writing a class.

On the more technical side, classes depend on each other and so when a
class changes something that other classes depend on, the compiler needs
to rebuild the code of every class that uses it to make sure nothing
broke. However, since we separated the implementation from the
definition of the class, the compiler only needs to rebuild dependencies
if the definition of the class changes. This really saves build time
since the majority of changes are made in the source code.

## The Robot Class

The robot class is a special class because each method inherited from
TimedRobot is executed conditionally at runtime without you as a coder
having to call them. This is akin to main() being run when you run a
java or c++ program. You don’t need to worry about how this happens,
just understand what functions are called and when.

Driver Station has a display of the different states the robot can have:
<img src="media/image14.png" style="width:6.5in;height:1.50019in" />

You can enable the robot in different states (TeleOperated, Autonomous,
Practice, and Test) or keep it in the disabled state.

Every state has an Init and Periodic function. As soon as you put the
robot in one of these states, its init function will be called. After
the state is entered, the periodic function for that state will
continuously be called every 20ms while the state is active.

For example, if I enable the robot and TeleOperated is selected on
Driver Station, as soon as I enable TeleopInit() will be called once.
Then every 20ms while the robot remains enabled and in the TeleOperated
state, TeleopPeriodic() will be called.

The RobotInit() and RobotPeriodic() functions are the only functions not
tied to a state. RobotInit is called as soon as the robot is powered on,
and RobotPeriodic is called every 20ms while the robot is on, regardless
of the state.

We don’t use the practice or simulation states, although if you’d like
to you are free to figure out how.

## 🕳️Building and Deploying Code

To build or deploy, press the
<img src="media/image4.png" style="width:0.42708in;height:0.38761in" />
in the top right corner and search for “build” or “deploy”

**Building** the project simply compiles it. Since there’s nothing in
the project at this point, it should succeed and show you a message like
this:

<img src="media/image6.png" style="width:6.5in;height:0.72222in" />

**Deploying** is a little more complicated and loads the code onto the
robot. It does this via ethernet, so your computer has to be connected
to the radio on the robot like this:

INSERT PIC

If the robot isn’t connected, the deploy will give you an error message
like this:

<img src="media/image2.png" style="width:6.5in;height:1.70833in" />

Keep in mind deploying builds before it deploys the code to the robot,
and will not work if your code does not build.

If the deploy works, it’ll open a RioLog that shows you all the error
messages and warnings and prints the code is outputting as it runs. It
looks something like this:

INSERT PIC

I would recommend setting up keyboard shortcuts for building and
deploying (you can ask me if you’re confused on how to). I personally
use cmd+shift+d for deploy and cmd+shift+b for build.

# ⚪Coding a motor

Intro here

## Motors + Motor Controllers

A motor is a device that takes voltage and applies rotational force.
Basically it's a thing that spins.

A motor controller is what regulates the voltage supplied to the motor.
This is what code interacts with to manipulate how the motor moves.

We mainly use motors from CTRE and REV Robotics. Though code only
interacts with the motor controllers, it’s important to know which
controllers correspond to which motors. In order to communicate with the
controllers, code has to use 3rd party libraries (in the rightmost
column) supplied by the motor vendors (leftmost column).

<table>
<colgroup>
<col style="width: 13%" />
<col style="width: 38%" />
<col style="width: 31%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Supplier</th>
<th>Motor(s)</th>
<th>Motor controller</th>
<th>Software library</th>
</tr>
<tr class="odd">
<th rowspan="2"><p>CTRE</p>
<p>(+ vex)</p>
<p>(+ WCP)</p></th>
<th><p>Falcon 500</p>
<p><img src="media/image10.png"
style="width:2.30729in;height:2.07897in" /></p></th>
<th rowspan="2"><p>TalonFX (built on the motor)</p>
<p><img src="media/image11.png"
style="width:1.87716in;height:1.82952in" /></p></th>
<th rowspan="2">Phoenix6</th>
</tr>
<tr class="header">
<th><p>Kraken</p>
<p><img src="media/image13.png"
style="width:2.32675in;height:1.72722in" /></p></th>
</tr>
<tr class="odd">
<th rowspan="2">REV robotics</th>
<th><p>NEO V1.1</p>
<p><img src="media/image12.png"
style="width:2.18265in;height:1.60447in" /></p></th>
<th rowspan="2"><p>SparkMax</p>
<p><img src="media/image3.png"
style="width:1.88021in;height:2.62497in" /></p></th>
<th rowspan="2">REVlib</th>
</tr>
<tr class="header">
<th><p>NEO 550</p>
<p><img src="media/image5.png"
style="width:2.32762in;height:1.54734in" /></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

There are definitely more motors (like mini NEOs and CIMs) and more
controllers (like the TalonSRX) that we might use but they’re used way
less often. If you want to know about those as well, let me know and
I’ll add them.

## 🔴Installing Vendor Libraries

## 🔴Using Vendor Libraries

### 🔴Phoenix6

The TalonFX class

PutVoltage()

GetPosition().ValueAsDouble()

### 🔴REVLib

# Control Theory

Getting the motor to move is cool and all, but not quite useful yet. As
code we need to get the motors to DO something with which requires
control and precision in order to produce reliable and consistent
results. For example using a motor to extend an elevator to reach some
height. And to produce consistent

Anyway this is where we step away from syntax and boring stuff like that
and get into the fun stuff.

## Feedback Control

Feedback control usually is the most intuitive type of control, as it is
what us humans do. We respond to the environment around us and change
our movement accordingly.

The code changes how the robot behaves, which impacts the sensor data,
which then is fed back into the robot code, hence the name “feedback”.

### Bang-Bang Control

The simplest control. **Apply a constant output negative to the sign of
the error.** In other words, if it’s positive/ahead, go backwards and if
it’s negative/behind, go forwards.

One problem with bang-bang control is that since it does not slow down
as it gets to the target, it will consistently overshoot. Once it
overshoots, it will go in the opposite direction and overshoot again,
oscillating and never reaching the target and coming to a stop like we
want it to.

### PID Control

PID consists of 3 parts: the proportional term (p), the integral term
(i), and the derivative term (d), which have corresponding constants kp,
ki, and kd respectively. **The output of the controller or the voltage
is the sum of the 3 terms.**

p = kp \* error

**P** is proportional to the error: **when the mechanism is far away
from its target, it will go fast and as it gets closer to the target it
will go slow**(since the error is smaller). Keep in mind that error has
a sign (positive/negative) so it always moves the mechanism in the
direction of the target.

<img src="media/image24.png" style="width:2.46397in;height:1.38596in" /><img src="media/image24.png" style="width:2.46397in;height:1.38596in" /><img src="media/image24.png" style="width:2.46397in;height:1.38596in" />

When only using the p term, sometimes it is difficult to get to the
setpoint quickly since it’s not slowing down fast enough and its
momentum carries it past the setpoint, overshooting which leads to
oscillation. This is where the d term comes into play.

d= kd \* (change in error)/timePassed

d = kd \* (0 - velocity)

d = - kd \* velocity

**D** is proportional to the derivative of the error. If you haven’t
taken calculus, the derivative of the error is just the rate of change
(or slope) of the error at some point in time. Since error is
essentially position relative to the target (position if the target was
the origin), the rate of change of this ’position’ is the velocity of
the mechanism relative to the target. In simpler terms, D is
proportional to the velocity error. The target velocity usually is 0, so
the error in velocity is 0 - velocity, or just -velocity. **This can
then be seen just as a term to slow down the mechanism (going against
the way it is moving).** This allows us to get to the target quickly
without oscillating.

<img src="media/image24.png" style="width:2.46397in;height:1.38596in" /><img src="media/image24.png" style="width:2.46397in;height:1.38596in" />

i= ki \* totalError

**I** is proportional to the total error, or the integral. Its purpose
is to work against any constant forces such as friction, and to make up
for being constantly off if the p and d terms are too small to move the
mechanism. **This consistent error is called steady-state error**, which
the i term combats by increasing the output over time until it is large
enough to overcome it. Common symptoms of steady state error that
indicate a need for an i term are being consistently off, often stuck,
or heavily resistant.

The constants for each term essentially give different weights to the
p,i,and d terms, scaling their effects. **We don’t want any term doing
too much or too little since they all serve their own unique purpose.**

<img src="media/image21.jpg" style="width:0.71654in;height:0.89129in" /><img src="media/image24.png" style="width:2.46397in;height:1.38596in" /><img src="media/image24.png" style="width:1.88799in;height:1.38596in" /><img src="media/image21.jpg" style="width:0.71654in;height:0.89129in" /><img src="media/image21.jpg" style="width:0.71654in;height:0.89129in" /><img src="media/image24.png" style="width:1.88799in;height:1.38596in" />

#### Tuning tips

A simple tuning process:

1.  Start with kp =0, ki =0, kd = 0

2.  Increase p until it starts oscillating

3.  Increase d until it stops oscillating

4.  Increase i if it’s consistently a little off

5.  Tweak values based on performance

In general but specifically for the last step, knowing how each term is
contributing to the motion of the mechanism is very useful. Since you
know how each term contributes to the motion of the mechanism, you can
respond to the speed and oscillation of the controller and manipulate
the constants to minimize oscillation and maximize speed.

From largest to smallest it should be: kp, kd, ki, although with weird
mechanisms it can change. Always start small and increment with caution,
especially for i.

Mechanisms can also occasionally have no i and/or d terms.

#### Implementation tips

Make sure you are resetting your total error when the target changes.
Otherwise the i term will get super large and break stuff.

#### Shortcomings of PID

PID assumes every position in a mechanism’s range takes the same effort
to be at and to move to. If something like an intake has to resist
gravity at different intensities based on its angle, PID cannot account
for this.

## 🔴Motion Profiles

### 🔴Trapezoidal motion profile

Blaj blah

You should try making your own before using this but we have a
[<u>util</u>](#trapezoidal-motion-profile-1) that implements this
reliably.

## 🔴Feedforward Control

This may look a bit weird since there’s no way to know if the robot’s
doing well (there’s no sensors). But, the core concept here is that the
**code can predict/understand where the robot will be, so it can
confidently set an output that it will somewhat reach the target**.
Although, note, it may not actually be looking into the future (we’ll
get into this later).

# ⚪Coding as a team

Intro blah blah

## Git and GitHub

If you are already familiar with git and GitHub, skip to [<u>the section
about our git workflow</u>](#s-git-workflow).

In order for the whole team to work on a single code project, we have to
use some sort of software to manage multiple people making changes to
one file or set of files. For this, most of the world (our team
included) uses git and GitHub.

git allows people to work on developments while preserving the latest
working version, revision and restoration of version, and easy . It’s
essentially like google drive for code.

### 🟠Requirements

1.  You need to [<u>install git/ check for
    > installation</u>](https://github.com/git-guides/install-git).

2.  [<u>Create a github
    > account</u>](https://github.com/signup?source=header) (do not
    > recommend using your school email)

3.  Set up an ssh key for your account

If you only have one github account, you should [<u>check if you already
have an ssh
key</u>](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys)
on your machine.

If you use multiple github accounts or do not already have an ssh key,
you should [<u>generate an ssh key using
ssh-agent</u>](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

Now once you have an ssh key, you should [<u>add it to your
account</u>](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
and then [<u>verify its
connected</u>](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection).

Managing ssh keys with multiple accounts is pretty complicated so I’m
not going to cover it here but if you’re interested I can show you how
to set it up.

### 🟠Git Overview 

If you’re familiar with git feel free to skip this:

**Repository (Repo):** A storage location for your project files and
their history. It can be local (on your computer) or remote (on a server
like GitHub). You can think of this as the equivalent of a folder. Local
would be a folder of stuff on your desktop, and remote would be
uploading that folder to google drive and then sharing it with others.

**Commit:** A snapshot of your project's changes. Each commit has a
unique ID and contains the changes you made, along with a message
describing those changes. This can be paralleled with version history in
a google doc.

**Branch:** A parallel version of the repository. Branches allow you to
work on different features or fixes separately. The default branch in
most repositories is main or master.

**Pull Request (PR):** A request to merge changes from one branch (often
a fork) into another branch. This is commonly used in collaborative
projects for code reviews before integrating changes.

**HEAD:** A pointer to the current commit or the latest commit in your
checked-out branch.

git clone \[URL\]: Copies an existing repository from a remote server to
your local machine.

git add \[file\]: Adds changes in the specified file to the staging
area. You can also use git add . to add all changes in the current
directory.

git commit -m "message": Records the changes in the staging area with a
descriptive message.

git status: Shows the current state of the working directory and the
staging area, including any changes that have been staged, changes that
haven't been staged, and untracked files.

git pull: Fetches and integrates changes from a remote repository into
your current branch.

git push: Uploads local commits to a remote repository.

git branch: Lists all branches in your repository. Use git branch
\[branch-name\] to create a new branch.

git checkout \[branch-name\]: Switches to the specified branch. Can also
be used to checkout a specific commit or file.

git merge \[branch-name\]: Merges the specified branch into your current
branch.

git fetch: Retrieves updates from a remote repository without merging
them into your local branch.

<s>git rebase: Reapplies commits on top of another base tip. It’s a way
to move or combine a sequence of commits to a new base commit.</s>

git init: Initializes a new Git repository in your current directory.

git diff: Shows the differences between commits, branches, files, etc.

git log: Displays a log of commits. You can use various options to
filter and format the log output.

git stash: Saves your local modifications and reverts the working
directory to match the HEAD commit. This is useful for quickly switching
contexts without committing incomplete changes.

### 🟠Try it yourself

Once you have git installed, try these steps to get an understanding of
how we use git

1.  Pull some repository from [<u>our team’s GitHub
    > account</u>](https://github.com/Eaglestrike), for example [<u>2024
    > robot code</u>](https://github.com/Eaglestrike/2024-RobotCode)

    1.  

2.  Make a new branch

<!-- -->

1.  Checkout that branch

2.  Make a new file or some random change

3.  Stage your changes (git add)

4.  Commit your staged changes

5.  If it’s not the team’s repository, try pushing your changes to the
    > branch

6.  Check github and see if the remote repository is updated and the
    > same as your local one

### ⚪114’s Git Workflow

1.  **Work in branches** NOT in main

We keep the latest working version of code in the main branch of the
repository. If someone is working on a subsystem or an improvement, they
create a separate branch and work there. This way we always have an
easily accessible branch of working code. In general we try to keep the
main branch clean.

2.  Create **pull requests for code reviews** OR to merge into main if
    > your branch is tested and approved by the code lead

It’s only after that branch has been tested on the robot and approved by
the code lead do they create a pull request, asking to be merged to
main. Pull requests can also be used for code reviews. A good example of
this is [<u>this old
PR.</u>](https://github.com/Eaglestrike/2024-RobotCode/pull/2)

3.  1 branch per change

To avoid merge conflicts, create new branches for every conceptual
change to the robot. For example if you’re working on a subsystem and
suddenly find a way to improve the controller class, you’d have to open
a new branch called controller-class-improvement or something.

## Team practices

Stuff we do to keep our code consistently readable, debuggable, and
reusable.

### Style practices:

Generally we try to keep code as clean and easy to read as possible, in
order to make debugging, peer review, and general comprehension easier.
This means we follow some pretty standard practices:

1.  Use m\_*varName* (preferably) or *varName\_* for member variables
    > (i.e. m_ampIntake)

2.  Use camel or snake case (preferably camel) for variable names (i.e.
    > ampIntake)

3.  Class, struct, enum, and function names are capitalized camel case
    > (i.e. AmpIntake)

4.  Constants (and therefore enum values) are all caps snake case (i.e.
    > AMP_INTAKE)

5.  Indent anything in curly brackets or after colons (like private: and
    > the cases of switch statements)

6.  Instantiate variables in the constructor, not the header file
    > (instantiation is different from declaration)

### Conceptual practices:

1.  Abstraction and encapsulation

2.  Meaningful variable and function names

3.  Comment the parts of your code that are hard to understand (do it
    > for yourself trust me)

4.  If time, add a comment explaining what each method does

### The Mechanism class

### The Controller class

### Shuffleboard Sender

### Team Utils:

#### Trapezoidal motion profile

#### Timer

#### Logger

#### Poses

### Feedforward Auto Tuner

Works kinda sometimes

# Other Resources

[<u>WPILib docs</u>](https://docs.wpilib.org/en/stable/index.html)

Has pretty well documented guides to a lot of code concepts and robotics
concepts in general. For example installation guides and even conceptual
stuff like motion profiles.

[<u>WPILib C++
docs</u>](https://github.wpilib.org/allwpilib/docs/release/cpp/index.html)

Documentation of all the classes and namespaces and stuff that WPIlib
offers. We don’t use WPILib’s classes that much, usually we opt to make
our own utility classes because WPILib’s stuff can be sus sometimes and
a little harder to follow/use. They also use really annoying units for
everything instead of just keeping stuff as doubles. But if you’re just
looking for a simple class to handle
[<u>PID</u>](https://github.wpilib.org/allwpilib/docs/release/cpp/classfrc_1_1_p_i_d_controller.html)
or something for you, WPILib’s helpers can be useful.

[<u>The old tech
binder</u>](https://docs.google.com/document/d/111ZI8VX0vLwrTrQJfh3r7tGUT_dupv02ayNkIX2MrQc/edit#heading=h.pvgcrwk7prga)  
Pretty similar to this one,
