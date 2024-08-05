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
