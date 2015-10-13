title = 'C Programming - Writing Clean Code.  Revision Control.'

# Lesson 22 Notes

## Readings
- [Revision Control](https://en.wikipedia.org/wiki/Revision_control)
- [ppt](Lsn22.pptx)

## Assignment

## Lesson Outline
- Admin
- Review
- Writing Clean Code
- Revision Control

## Admin

- Prog grades are in - CAMIS should be (mostly) up to date

## Mixing C and assembly

Our compiler follows a certain convention while calling an assembly function from C that involves passing parameters.  
- First input: r12
- Second input: r13
- Third input: r14
- Fourth input: r15
- Fifth and beyond: the stack
- returned value: r12

## Lab 4

The basic idea of this lab is using C to call your assembly drawBox subroutine.  This lab should be fun!  Feel free to see what sorts of crazy ideas you can implement in your games.  


## Review

- Review pong code
- Review moving average code

## Writing Clean Code

### Meaningful Names

**[Bad Code](badCode.html)**

- Use intention-revealing names ("self-documenting")
    - `int d, temp; // elapsed time in days, a temporary variable`
    - `int elapsedTimeInDays, daysSinceModification;`
- Make meaningful distinctions
    - `void copyChars(char* a1, char* a2)`
    - `void copyChars(char* source, char* destination)`
- Use pronounceable names
    - `DtaRcrd`
    - `DataRecord`
- Use searchable names
    - `MAX`
    - `MAX_STUDENTS`
- Functions: use verbs!
    - `forward()`
    - `moveForward()`
- Don't be cute
    - `holyHandGrenade()`
    - `deleteItem()`
- Pick one word per concept
    - Bad: `fetch(), retrieve(), get()`

### Functions

- Small - ideally less than 10 lines long
- Do one thing
- Use descriptive names
- Parameters: rarely need more than two or three
- Side effects - function should only do what you say it does
- Do not use static or global variables
- Only depend on local variables / parameters
- Don't repeat yourself - write a function instead of copy / paste
- Only one entry / exit point
- Indent correctly!

*[Let's fix my code!](pong_c.html)*

- Create `updateBallIfHitWall` function
- Create separate `didHitTop`, `didHitBottom`, `didHitLeft`, `didHitRight` functions

### Comments

- Comment on "big picture" items
    - Head of each file
    - Definition of each function
    - Beginning of each major block of code
- As you move deeper in the hierarchy, the comments are more specific
- Try writing functions / meaningful names
    - `if ((employeeFlags & HOURLY_FLAGS) && (employeeAge > 65)) ...`
    - `if (isEligibleForFullBenefits(employee)) ...`
- TODO comments
    - `// TODO: Make this into a function`
    - `// TODO: Write new header file to group these functions`
- Bad comments
    - Restating your code (`a = 1; // Setting a to 1`)
    - Commented-Out code
    - Too much information
    - Don't comment bad code - rewrite it.

- Add comments to functions

## Revision Control

- Database that keeps track of multiple versions of your code
- Revision Control Terms
    - *Repository* - database where your versions are stored
    - *Commit* - submit the changes to files since last commit
    - *Revert* - go back in time to a previous version
- **Not a substitute for backing up your data!**
- Commit very frequently
    - Usually after you get a small part working (e.g. simple function)
    - It only stores the *difference* between versions (i.e. commits don't take up much disk space)
- Most common revision control tools
    - Concurrent Versions System (CVS) - older, but still popular
    - Subversion (SVN) - designed as a replacement for CVS
    - Git - hugely popular for individual / team software development
        - Required for this class
        - Created by Linus Torvalds for use with the Linux Kernel after Bitkeeper withdrew free use of the product
        - Wrote the initial version in two weeks, used for kernel development within 2 months

### The Shell

"A shell is software that provided an interface for users of an operating system to access the services of a kernel." - Wikipedia

Basically, a shell gives you direct access to your computer.

To use git, we'll be using a shell - Git Bash.  Bash is an acronym for Bourne Again Shell - it is probably the most common shell in existence.

Here are some common shell commands that will prove useful:

- `ls`
    - Lists contents of a directory
- `cd`
    - Change directory
- `pwd`
    - Display the present working directory (directory you're currently in)
- `cat`
    - Concatenate, but practically used for displaying the contents of a file
- `vi` or `vim`
    - Sweet text editor that your instructor uses

*[Demo these commands, get them to open shell and practice them]*

**If you want to learn more, [a tutorial is available on the datasheets page.](/382/datasheets)**


### Common Git Commands

- `git config --global user.name "First Last"`
    - Stores your name as a property to be used for each commit
- `git config --global user.email first.last@usafa.edu`
    - Stores your email as a property to be used for each commit
- `git init`
    - Creates a git repository in the current directory
- `git add <filename>`
    - Adds the file `<filename>` to the git repository
- `git commit -a -m "This is what I changed."`
    - Commits all changes to files you have added and stores a message that describes those changes
- `git log`
    - Shows you a complete history of commits within the repository
- `git status`
    - Show you the status of the repo this directory is in

### [Github](http://www.github.com)

[Github](http://www.github.com) is the most popular open source code repository site in the world.  It's a web-based hosting service for projects that use Git.  It is required for this class.

A sampling of real-world projects hosted there:

- [Linux](https://github.com/torvalds/linux)
    - The world's greatest operating system!
- [jQuery](https://github.com/jquery/jquery)
    - Popular javascript library for front-end web development
- [node,js](https://github.com/joyent/node)
    - Popular framework for serverside javascript

Github is a great place to get access to the source code for some of the world's most popular open source projects.  It's a great way to keep track of programmers whose work you're interested in.  It's also a great way to get involved in the coding community, maybe work on an open source project or release some code of your own.