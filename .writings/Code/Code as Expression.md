The Fundamental Theorem of Readability -
Code should be written to minimize the time it would take for someone else to understand it.

# Naming
Pack information into the names. 
- Choose specific words. Avoid ambiguous descriptions.
- Concrete names instead of abstract ones. 
- Attach extra info by suffixing or prefixing.
- Name length should be proporitional to the scope (lifetime).
- Tighten the meaning. No mis-interpretations allowed.
Personal Additions
- Find a metaphor to your problem and name accordingly.

*Note: A token lifetime is measured by the number of lines it appears at.*

# Aesthetics
- It is easier to work with code that is aesthetically pleasing.
- Use linebreaks to expand the code vertically when the line are too long.
Personal Additions
- Opeators and operands must layed down with a one space separation.
- Expressions within parenthesis (), breakets [] must have a leading and ending space.
- Expressions within curly braces {} must be on a new line.
- Expression within chevrons <> must fit tight.
- If possible code chainble methods and use them as follows,
```TypeScript
object
	.methodA()
	.methodB()
	...
```
- Use line grouping. Grouping principles can vary, but the result is that, the code will be organized into themed segments. #design_principles 
- Increase the symmetry of your code. #design_principles It could be superficial symmetry (of naming) or deep symmetry (of functionality).
# Comments
*The purpose of commenting is to help the reader know as much as the writer did.*

- Don’t comment on facts that can be derived quickly from the code itself.
- Don’t comment bad names; fix them instead.

- Record your thoughts; if that is not the heart of commenting.
- Comment the flaws in your code; the chances of it hitting a limit are always real.
- Comment your constants; there is a always a story behind it.

- Put yourself in reader's shoes.
- Anticipate likely questions; answer them.
- Advertise likely pitfalls; there is always that clueless person.

- Big picture comments. Expose the role of this piece of code in the whole code structure.

At-the-end-of-day (ATEOD) directive: A few well-chosen sentences are better than nothing at all.

*Comments should have a high information:space ratio.*

- Use inline comments for arguments in function calls.
- Use words that are indicative of patterns (information-dense words) instead of describing the whole pattern.