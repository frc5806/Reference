# Style Guide

Below is the general style guide for programming on FRC team 5806.  As we are one collaborative team, our code must mesh as if it were written by one person.  For this reason (and some others), it is crucial that all programmers follow the guidelines below.  

## Naming

Classes names are begin with a capital letter. There are no spaces or underlines between words, and each successive word begins with a capital letter (e.g. `NeuralNetwork`). Variables and functions begin with a lower case letter, there are no spaces or underlines between words, and each word after the first begins with a capital letter. Constants are an exeption to this rule. Constants are fully capitalized, and there are underscores between words.

An example of proper naming:

```java
public class ExampleClass {
	public final float EXAMPLE_CONSTANT = 3.14159;
	private double exampleMemberVariable;
	public void exampleMethod(int exampleVariable) {}
}
```

##General Syntax Rules

The following rules apply to most languages.

#### Rule #1: Curly brace placement

The following is right:

```java
if (5 == 5) {
	/// do stuff
}
```

The following is acceptable for short, single-line blocks:
```java
if (5 == 5) myVarable += 5;
```

The following is wrong:

```java
if (5 == 5)
{
	/// do stuff
}
```

Get over it.

#### Rule #2: Tabs, not spaces

Heading says it all

## Version Control

#### Rule #1: Commit contents

Imagine you've been working on the drive code and the autonomous code, and want to commit your changes.  These are __separate__ commits.

#### Rule #2: Commit Messages

`asdf` is a bad name for a commit.  We've all done it before, but we don't do it here.  The title should be at least two words, and if that's not totally self explanatory you should probably put in a description.

#### Rule #3: Branching and Pushing

If you and another team member are working on a piece of code in two separate directions, you each need a branch.  If you're working on it in the same direction, a branch probably isn't necessary (but be wary of merge conflicts).  In cases of robot code, never push untested/unworking code to the main branch, as somebody probably *will end up running it*.

## Documentation and Comments

Code is rarely ever truly "self documenting."  This is just something we tell ourselves at night to help us sleep.  Thus, every class should have a comment describing it immediately beforehand.  In Java, this should be directly on top of the class declaration:

```java
/* Describes a cat-tank hybrid.
 *
 * CatTank objects should only be
 * created when absolutely necessary.
 */
public class CatTank {
	// Describes the number of
	// bullets in the CatTank
	private int bullets;

	// Constructs a CatTank
	public CatTank(int bullets) {

	}
}
```

As you can see in this example, not only is the class documented but also the constructor, the methods, and the variables.

If you'd like to make a comment that isn't documentation, such as a note to a teammate or a clarification on something messy, three slashes should be used rather than two (or in Python, two hashes instead of one). This helps distinguish documentation for somebody just browsing the code, and makes the file easier to parse for automatic documentation generators such as doxygen and cldoc.  Additionally, comments should have a space between the forward slashes and the comment message.
