## 🕳️Building and Deploying Code

To build or deploy, press the ![logo](images/image5.png) in the top right corner and search for “build” or “deploy”

**Building** the project simply compiles it. Since there’s nothing in
the project at this point, it should succeed and show you a message like
this:

```{image} media/image16.png 
:width:6.5in
:height:0.72222in
```

**Deploying** is a little more complicated and loads the code onto the
robot. It does this via ethernet, so your computer has to be connected
to the radio on the robot like this:

INSERT PIC

If the robot isn’t connected, the deploy will give you an error message
like this:

```{image} media/image13.png 
:width:6.5in
:height:1.70833in
```

Keep in mind deploying builds before it deploys the code to the robot,
and will not work if your code does not build.

If the deploy works, it’ll open a RioLog that shows you all the error
messages and warnings and prints the code is outputting as it runs. It
looks something like this:

INSERT PIC

I would recommend setting up keyboard shortcuts for building and
deploying (you can ask me if you’re confused on how to). I personally
use cmd+shift+d for deploy and cmd+shift+b for build.