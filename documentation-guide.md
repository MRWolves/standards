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

All of these levels are important, and all of them require documentation.  But the *type* of documentation required by each is not the same; high-level architectural decisions can be explained by technical prose, but low-level implementation details will almost always require either pseudocode or actual source.  Just as our actual understanding of a system "cleaves" naturally into layers based on levels-of-abstraction, so too does the ideal structure of project documentation.

So, "where is the documentation?"  It should be woven throughout.  The structure of the documentation should match the structure of our understanding of the system.

*Therefore*, documentation is implemented in a layered fashion.  In particular, code documentation for our software projects should have three layers:

1. **Usage Documentation**:  This includes wide-scope overviews of the tool and its purpose, example projects, code excerpts, and design guides.  This layer is usually the first one to be encountered/read by a new user.
2. **API Documentation**:  This includes rigorous reference material for all of the "surface" parts of the tool (i.e. public-facing API classes and methods).  This layer is usually primary reference for an ordinary user making typical use of the tool.
3. **Source Documentation**:  This includes comments, meaningful naming conventions, and best-practices for code design and readability.  This ensures that advanced users are able investigate, debug, and/or modify the tool when necessary.

It is important to note that this "layering" is not perfect: these layers overlap, and depend on each other.  Usage documentation should refer extensively to API documentation.  API documentation is often source-generated, and so overlaps with best practices for code commenting.  Nevertheless, this provides us with a baseline framework with which we can situate our best-practices.

The standards for each layer will be covered below in reverse-order, as that is the order in which the documentation is naturally developed during the course of code development.
