title = 'Labs'

# Labs

## General

The labs make up a significant portion of both your prog and final grades.  You must complete each one (even for zero credit) to pass the course.  A disciplined approach to design, implementation, and testing are key to your success!  Wiring and coding the entire lab and then trying to figure out why it doesn't work (they almost never do) can be incredibly painful and time-consuming.  Our experience shows that students who get behind on the labs need to catch up immediately, else the burden of uncompleted labs builds to inescapable levels.

## Lab Notebooks

Lab notebooks are heavily emphasized in this course and constitute a large portion of lab grades.  The lab notebook is maintained as a journal of your lab experience and should allow you, or any knowledgeable engineer, to recreate your project.  For this course, your notebook should contain at least the following (as applicable to the particular lab):

- Descriptive title
- Objectives or purpose
- Prelab
- Preliminary design
- Software flow chart / algorithms
- Hardware schematic
- Well-formatted code (only include key code snippets...code files should be included in code folder)
- Debugging
- Testing methodology / results
- Observations and Conclusions
- Documentation

The actual format is flexible, so don't be afraid to add something later.  All lab reports must stand up to the **"hit by a bus"** standard.  Should you die, another engineer must be able to continue your work without trouble.

You are expected to keep your lab notebooks current as you work on a lab.  You will lose substantial points if sections of the lab notebook which should be part of your documentation before the demonstration (such as prelab, approach, flowcharts, testing, debugging, etc.) are entered afterwards.  Your conclusion section, lessons learned, and your final formatted code are not required before your demo.


### Electronic Lab Notebooks

In this class, we will use an electronic lab notebook.  We'll be using the version control software **git** and your code must be hosted on [Bitbucket](http://bitbucket.org).  Here is the directory structure that must be used if you have more than one code file or more than one image file to be uploaded for a single lab:

- /LabX
    - /code
        - Include all source code here
    - /images
        - Include all images you use in your notebook here
    - notebook.md (or README.md)
        - Lab notes not included in your git commit history

**ECE 382 Lab Notebook Example** - [https://github.com/jfalkinburg/ECE_382_Lab_Ex](https://github.com/jfalkinburg/ECE_382_Lab_Ex)

Your commit history will be used as verification that you've been keeping your lab notebook up to date as you progress.  You should commit early and often.

You'll still need to hand in your grading sheet so I will know your achieved functionality and can record grades and feedback for you.

## Coding Standards

### General

You are expected to use the same structured programming techniques that you were taught in CS110.

You must comment your code where appropriate.  This doesn't mean commenting every line you write - that's distracting and unproductive.  Comments should be used to convey the general purpose of a block of code or explain a section that may be unclear.  You can assume the reader is a knowledgeable engineer.

Use meaningful, readable variable names - variable1 or var1 or loop1 or L1 are unacceptable.

**Don't repeat yourself!**  If you find yourself using the same code over and over, you should abstract it into a subroutine or function.

### Code Headers

For each coding file submitted in your lab notebook, ensure you have a header that includes your name, the date, the assignment, a brief purpose of the code, and documentation for that specific file.

For each subroutine you use, include a header just above the subroutine's location.  Ensure the author, function, inputs, outputs, and destroyed registers for that subroutine are included in the subroutine header.

### Assembly

For constants, you must use `.equ` statements and assign them a meaningful, readable name.

Labels should be used in place of memory addresses and assigned a meaningful, reable name.

You should organize your code in such a way that it's easily readable.  While not required, a good structure would be:

- Headers
- Constants
- Variables
- Main program
- Subroutines
- Interrupt service routines
- Interrupts vectors

Other guidance:

- Comments
    - Assume the reader is a competent assembly language programmer
    - Comment above blocks of code to convey **purpose**
    - Only comment individual lines when purpose is unclear
- Labels
    - Descriptive!
        - loop or loop1 or l1 or blah - not acceptable!
    - Used for all memory location, jumps, etc. 
- Constants
    - Use `.equ` syntax for all constants!
    - Don't want to see magic numbers!
- Instruction Choice
    - Use the instruction that makes your code readable!
        - `JHS` rather than `JC`
        - `INCD` rather than `ADD #2`
    - Well-written code requires few comments
- Spacing
    - Align your code to make it readable
    - Put whitespace between logical blocks of code

### C

[Check out the C style guide.](c_style_guide.html)
