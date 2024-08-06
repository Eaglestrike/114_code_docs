# .h and .cpp files

C++ has header (.h) and source code files (.cpp), which serve to make build time quicker and to make the code cleaner to write and for others to read and use.

### Header files
**A header file serves as a skeleton of the source code**. It
defines/declares data structures like classes, although it should not implement any of the things it defines (though it can).
### cpp files
**A source file implements the methods the header file defines**. This is where all the logic and inner workings of the class is done.

For example if you look at Robot.h, the class Robot is declared to have methods like RobotInit which are defined but not implemented. Although the methods in Robot.cpp are currently empty, this is where the code would be written.



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
