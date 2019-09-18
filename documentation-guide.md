# MRAS Application Team Code Documentation Guide

## Documentation: What and Why?

An initial note: This guide is about documenting code, *not* about documenting the software created by that code.  These concepts are related, of course, but are sufficiently distant that it is not sensible to cover them in the same guide.

In order to talk about code documentation, we first need to agree on what code documentation *actually is*.  This question is not quite so simple as it might initially seem; documentation comes in a wide variety of forms (e.g. example projects, usage guides, API docs, comments) and can be located in a wide variety of places (e.g. in-source, github markdown files, hosted webpages).  What's more, some documentation is not even necessarily *material* - the choice of proper variable names and code structure can itself be a form of documentation ("self-documenting code").  The boundaries are fuzzy - concerns of documentation cannot be cleanly separated from other concerns of code architecture/style/implementation, and so documentation best-practices cannot be considered in isolation, either.

For the purposes of this guide, we will take "code documentation" to mean "material and practices meant to *facilitate understanding of software tools.*"  This is a very broad definition, and this guide will, in places, touch on the overlap between documentation and other code design concerns.  Inevitably, much of the content will be about "traditional" forms of software documentation - that is, documents that describe code.  Whenever possible, however, emphasis will be placed on the connection between this sort of documentation and the broader concept of documentation, and care will be taken to link the recommended content and form of the "traditional" documentation to broader concerns of style and coding philosophy.

We also need to concern ourselves with *why* we document code in the first place.  This issue is somewhat less-subtle: we document code because failing to do so (eventually) renders it useless.  When a tool is not documented, the knowledge of its use resides exclusively in the minds of the people currently working on or with it - often, this is little more than a single developer.  Once a person ceases to work with the tool, their knowledge of its is eventually lost, both to others and even themselves (how well do you remember code you wrote two years ago?).  Once working knowledge of the tool is no longer available, it is *almost always* more appealing to make a new tool than to learn the old tool without a guide.  Thus, *undocumented code is [throw-away code](http://www.laputan.org/mud/mud.html#ThrowAwayCode)*.  It is not possible to build a reusable tool without documentation, no matter how elegant.

*Therefore*, the fundamental purpose of documenting code is *to make it easier to reuse the code than it is to rewrite it from scratch.*

## The Fundamental Rule of Documentation

The purpose of documenting code is to make it easy to reuse.  *Incorrect* documentation makes code *harder* to reuse.  Incorrect documentation is *worse* than no documentation.

Documentation is not, as a rule, self-maintaining.  Updating documentation takes time and effort.  The more documentation a project has, the more time and effort must be spent keeping that documentation consistent with changes to the code.

*Therefore*, the fundamental rule of documentation is to *never write more documentation than can be reasonably maintained.*

Violating this rule will not only waste time, but actively hurt your project.  Match the scope of your documentation to the scope of your project - smaller projects naturally require less documentation than larger projects.  *Always* consider how much effort will need to be made to keep a piece of documentation up-to-date before writing that documentation in the first place.

## Documentation as Layers

Good code documentation is pervasive and multileveled.  Often, a software engineer joining a new project will ask "where is the documentation?"  On a robustly-documented project, the answer to this question is: "everywhere."

Understanding of a tool occurs at multiple levels.  At the "highest" level, there are the macro-scale questions about the tool's purpose and higher-order architecture: 

* "What problem does this tool attempt to solve?"
* "When might I want to use this tool?"
* "What are the driving philosophies behind the design of this tool?  How are those driven by the tool's specific problem-space?"
* "What alternative tools should I consider?"

Slightly further down the abstraction-hierarchy, we have broad mechanics-oriented questions:

* "Where do I start after I've decided to use this tool?"
* "What features does this tool actually support?"
* "What does this tool look like when integrated into a typical project?"
* "What are the basic 'parts' of this tool, and how are they organized?"

Continuing downwards, we start to get into mechanical details:

* "How do I customize this tool to do specific tasks?"
* "What language features do I need to know to use this tool?"
* "What are the common mistakes that I can/will make when using this tool?"
* "How is this tool's interface likely to change in the future?"

And then, finally, implementation details:

* "How do the parts of this tool actually work?"
* "How might I modify parts of this tool to do things that I want, but that it does not yet support?"

All of these levels are important, and all of them require documentation.  But the *type* of documentation required by each is not the same; high-level architectural decisions can be explained by technical prose, but low-level implementation details will almost always require either pseudocode or actual source.

Additionally, these levels distinguish themselves by their differential *rates of change*.  Low-level implementations tend to be volatile, while high-level problem-space constraints tend to move relatively slowly.  This naturally leads to [shearing layers](http://www.laputan.org/mud/mud.html#ShearingLayers), as things which change at similar rates end up factored together in code - and, likewise, in documentation.

Just as our actual understanding of a system "cleaves" naturally into layers based on levels-of-abstraction, so too does the ideal structure of project documentation.  So, "where is the documentation?"  It should be woven throughout.  The structure of the documentation should match the structure of our understanding of the system.

*Therefore*, documentation is implemented in a layered fashion.  In particular, code documentation for our software projects should have three layers:

1. **Usage Documentation**:  This includes wide-scope overviews of the tool and its purpose, example projects, code excerpts, and design guides.  This layer is usually the first one to be encountered/read by a new user.
2. **API Documentation**:  This includes rigorous reference material for all of the "surface" parts of the tool (i.e. public-facing API classes and methods).  This layer is usually primary reference for an ordinary user making typical use of the tool.
3. **Source Documentation**:  This includes comments, meaningful naming conventions, and best-practices for code design and readability.  This ensures that advanced users are able investigate, debug, and/or modify the tool when necessary.

It is important to note that this "layering" is not perfect: these layers overlap, and depend on each other.  Usage documentation should refer extensively to API documentation.  API documentation is often source-generated, and so overlaps with best practices for code commenting.  Nevertheless, this provides us with a baseline framework with which we can situate our best-practices.

The standards for each layer will be covered below in reverse-order, as that is the order in which the documentation is naturally developed during the course of code development.

## Source Documentation: Style, Structure, Naming, and Comments

Source documentation is the most basic and fundamental form of code documentation.  *All* projects have source documentation: at base, the code itself can be always considered a piece of documentation.

That said, not all source documentation is created equal.  Some code elegantly explains itself; other code is [deliberately impenetrable](https://www.ioccc.org/).  Code readability (as with many things in code) follow the [principle of least surprise](https://en.wikipedia.org/wiki/Principle_of_least_astonishment) - familiar patterns require less thought, and thus are easier to interpret.

This guide will set standards for the following four aspects of source documentation: **Code Style**, **Code Structure**, **Naming**, and **Comments**.

### Code Style

A uniform code style is *crucial* to code readability.  Consistency in style within a project is *absolutely mandatory,* and consistency across projects is highly desirable.

The foundation of a uniform code style is a coherent set of standards.  Since cross-project consistency is desirable, it is almost always a good idea to *begin with an existing set of standards*, rather than to write one's own.  Accordingly, all MRAS coding styleguides are based on existing standards.  Modifications are permitted, but should be both justified and, if possible, minor.

The following is a list of MRAS Application Team coding styleguides.  NOTE: This list is still under-construction.

* Java: https://github.com/Oblarg/MREStuff/blob/master/javastandards.md

### Code Structure

Adhering to style standards normalizes syntactic details, but it generally does nothing to normalize the general organization and design of the code.  These are just as important, if not moreso, to rendering one's code readable by others.  While it is impossible to give a fully-general set of standards for how one should structure their code - this is driven by details of the problem space in which the project is situated - there are nonetheless some general principles which it is a good idea to follow.

NOTE:  To quote George Orwell: "Break any of these rules sooner than say anything outright barbarous."  None of these are absolutes.

#### Separation of Responsibilities (AKA: Each Piece of Code Should Have a Job)

When attempting to understand a piece of code, one of the most natural and effective strategies is to attempt to break the code into pieces and figure out what each piece is responsible for.  Humans have limited working memory; it is almost impossible to understand the entirety of a nontrivial software project at the same time.

Unfortunately, it is very easy to write code for which this strategy is doomed to failure, because either:

a) The code does not separate into smaller "pieces" (functions, classes, namespaces, whathaveyou) in the first place, or
b) The pieces the code separates into do not reflect any sort of sensible division of the code's functionality

This is often the case with "proof-of-concept" code, which grows rapidly and hapazardly as the programmer becomes familiar with the problem-space and new requirements are encountered.  Often, no thought at all is put into *where* new functionality should be added; this is determined by immediate convenience, or pure happenstance.

*Therefore*, ensure that your code separates into pieces, *and* that each piece has a clear functionality that can be understood without simultaneously understanding the rest of the code in full detail.  In object-oriented programming, this is often best-accomplished by making wise choices as to one's class structure - but the concept is applicable in all contexts.

#### Avoid Globals (AKA Pass Information Locally)

Global variables are almost always a bad idea.  Since a global variable can be modified or read from anywhere in the code, they directly contradict the notion of factoring the code into chunks that can be understood in isolation.  Code that makes heavy use of globals tends to be extremely difficult to read, and even harder to modify/debug.

There are, of course, some cases where globals are unavoidable.  There are others when they are defensible design choices (e.g. a service that everything does actually need to interface with, and that there will never be more than one of).  But if you find yourself using a global variable to pass state from one part of the program to another, you have almost certainly done something wrong.

#### Do Not Repeat Code Unnecessarily (AKA: Abstraction Is Good)

Figuring out what a piece of code does is hard enough.  Having to figure out what the same piece of code does multiple times over is infuriating.  Repetition is not just an inefficiency in *writing* code, but in *reading* it, as well.

Abstracting repeated code into a subroutine or class serves not only to remind the reader that they already know what it does, but it also allows them to view the code as a "black box" with a set of defined inputs and outputs.  As mentioned, the most effective way to understand complex systems is by breaking them down into small chunks that can be understood in relative isolation; repeated code almost always represents such a chunk, and so the structure of your program should reflect that.

*Therefore*, when you find yourself repeating a chunk of code, strongly consider creating a reusable abstraction.  Copy-pasting is a sure sign that abstraction is a good idea.

#### Do Not Overabstract (AKA: Abstraction Is Bad)

Abstraction is great, right up until it isn't so great.  Perhaps the only thing worse than having to mentally replace a lengthy, repeated block of code with an imagined summary due to the lack of a sensible abstraction, is [having to "unwrap" a summary of a summary of a summary of a summary only to find the equivalent of four lines of code at the bottom](https://pranksanonymouspullzone-s07ehlhq.netdna-ssl.com/wp-content/uploads/2019/02/SquareBox.jpg).

(For an intentionally egregious example of this, see [Enterprise FizzBuzz](https://github.com/EnterpriseQualityCoding/FizzBuzzEnterpriseEdition))

This can occur for a number of reasons.  Top-heavy, "waterfall" development practices often result in overabstracted code because the major design decisions are made before it becomes clear where flexibility is needed and where it is not.  Even in less-structured environments, the temptation to allow for future expansion before the need for such has demonstrated itself is pervasive.  "Scope creep" can eventually eat even the simplest of projects, as the incremental appeal of "just one more feature" is almost always more immediately salient than the eventual cost of repeatedly accumulating additional complexity.

Compounding this, developers familiar with a project find themselves in a uniquely poor situation to judge the onset of overabstraction.  Familiarity with the code "collapses" the layers as they compound - those close to the code build mental shortcuts to "cut through the cruft."  Even after the intent of the code has long-since become entirely obscure to the outside observer, the original developer retains privileged knowledge of its original purpose and design - at least, until they spend a sufficient amount of time away from the project, at which point they are often rendered as clueless as anyone else.

*Therefore*, stay constantly vigilant against "abstraction-creep."  Do not add more abstraction to a project to facilitate a new feature until/unless it is *certain* that the new feature is needed.  Beware scope-creep.  Constantly solicit feedback on the clarity of your design structure from those *without* intimate familiarity with the project.

#### Avoid Deeply-Nested Control Statements (AKA: The Actual Reason for Column Limits)

```java
if (cond1) {
  if (cond2) {
    for (i=0; i<10; i++) {
      while (cond3) {
        if (cond4) {
          // You've made a terrible mistake
```

Hopefully it is clear by now that the key to readable code is *not requiring the reader to think about too much at once.*

One of the easiest ways to violate this principle is by haphazardly nesting control statements.  This is exceedingly easy to do while writing code, as the programmer (who knows what they intend to do) can build such nests from the "inside-out," limiting the noticeable complexity at each stage of growth.  Unfortunately, it is also exceedingly difficult to comprehend later, even by the programmer who originally wrote the code, as one is forced to read the resulting mess from  the "outside-in," keeping track of all of the previous levels at each stage.  As the number of paths the programmer has to keep track of grows roughly exponentially with the depth of nesting, this rapidly becomes utterly intractable.

Additionally, the sheer visual noise of having many layers of indentation itself poses a barrier to readability, making it easy to lose track of identation levels and, eventually, requiring an unreasonable number of line continuations as the code butts up against the column limit.  This is, actually, a *feature* of a conservative column limit in many coding standards; rather than placing a limit on the number of nested control statements, the strict column limit simply makes overly-deep nesting pragmatically unusable as the programmer runs out of space.

*Therefore*, do not deeply nest control statements.  Good strategies for avoiding this include liberal use of early return/continue, collapsing nested if statements into single-level if statements with compound conditions, and, if all else fails, encapsulating some of the complexity in a subroutine.  If the problem seems intractable even with these tools, this is likely a symptom of a fundamental problem with your code design.

#### Keep Your File Structure Orderly (AKA: Where the Heck Is the `main` Function?)

Your code itself may be extremely elegant and self-explanatory, but all of this is for naught if it is buried in a cluttered directory.  Often, a new programmer entering a large project is overwhelmed by the sheer quantity of files.  If the structure of the project does not make it clear which files are responsible for what *without* reading the code, the programmer is forced to engage in a blind search through the source - tracing calls from file to file - as they attempt to piece together the general architecture of the project.

This is an *infuriatingly difficult* process.  Even if the code in each file is easy to read, the search time alone as one attempts to "back-trace" the control flow without any guidance can render a project uninterpretable.  And if the code *isn't* easy to read, well, there's no hope at all.  In the worst case, it can be impossible to even find the file responsible for primary program flow (e.g. one containing a `main()` function), leaving the programmer grasping at an assortment of parts with no idea what is determining how they are put together.

*Therefore*, always ensure that your project directory is sensibly-structured.  Define a directory structure that matches your project structure, and document it in a README included in the root directory.  *Always* consider how hard it will be for someone unfamiliar with the project to find the important files that control program flow, so that unfamiliar readers can work from the "inside-out" rather than from the "outside-in."
