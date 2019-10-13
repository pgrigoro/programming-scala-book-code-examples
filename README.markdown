# Programming Scala, Third Edition

## README for the Code Examples

*Dean Wampler*<br/>
*August 11, 2014* - Second edition<br/> 
*October 13, 2019* - Started third edition changes<br/>

[![Join the chat at https://gitter.im/deanwampler/prog-scala-2nd-ed-code-examples](https://badges.gitter.im/deanwampler/prog-scala-2nd-ed-code-examples.svg)](https://gitter.im/deanwampler/prog-scala-2nd-ed-code-examples?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This repo contains all the code examples found in [Programming Scala, Third Edition](http://shop.oreilly.com/product/todo), with the exception of some trivial code snippets in the text. There are also some examples in this distribution that aren't actually in the book. 

The third edition supports Scala 3.0 and Scala 2.14, with Scala 3.0 the default. The third edition releases for Scala 3 and Scala 2.14 are tagged with `release-3.X.Y`. If you want the original third-edition code (with a few bug fixes) from the book, download the latest [3.0.Y](https://github.com/deanwampler/programming-scala-book-code-examples/releases/) build or check out the `release-3.0.Y` branch. If you want the original second-edition code, which is also in this repo, download the tagged [2.1.0](https://github.com/deanwampler/programming-scala-book-code-examples/releases/tag/2.1.0) build or check out the `release-2.1.0` branch. In general, the latest `2.X.Y` release and `release-2.X.Y` branch include all the updates for Scala 2.12 and 2.13 to the original, second-edition code examples.

## How the Code Is Used in the Book

In the book's text, when an example corresponds to a file in this distribution, the listing begins with a path in a comment with the following format:

```
// src/main/scala/../filename
```

And similarly for Java files (yes, there are Java files!). Following the usual conventions, tests are in `src/test/...`.

Use these comments to find the corresponding source file. This archive also contains unit tests to validate some of the code. Most of these tests are not reproduced in the text of the book, except when discussing testing itself.

## Naming Conventions

The examples include "scripts" that are run with the `scala` command (or within SBT using the `console`), source files that are compiled with `scalac`, and source files that deliberately fail to compile to demonstrate common errors. To keep them straight and to support building with SBT, the following naming conventions are used for the files:

- `build.sbt` - The SBT build script (described below).
- `*.scala` - Source files that are compiled with `scala`. In fact, this is the community-standard extension for all Scala files, code to be compiled or scripts. But to keep the build process simple, I use different conventions for files that aren't compiled, discussed next.
- `*.sc` - Script files that are executed directly, e.g., `scala foo-script.sc`. This file extension is not a standard, but it is used by the newer IDE *worksheet* feature I discuss in the book. So, I stole the convention; SBT will ignore these scripts when compiling. These script don't have tests to verify them (TODO).
- `*.javaX`, `*.scalaX` and `*.scX` - Java and Scala source files and scripts with deliberate errors, so they don't compile and run, or building them would require significant changes to the build that were deemed unnecessary. Most contain comments explaining what's wrong with them or in some cases, the corresponding section of the book provides the details.

## Required and Optional Tools

To build and run the examples, all you need to do is install [SBT](http://www.scala-sbt.org/release/docs/Getting-Started/Setup.html). SBT is the de-facto standard build tool for Scala. When you run SBT, it will bootstrap itself with the correct version of its jar file, Scala, and project dependencies, which are specified in the `build.sbt` file in the root directory and other build files in the `project` directory.

Follow these [installation instructions](http://www.scala-sbt.org/release/docs/Getting-Started/Setup.html).

If you want to install Scala separately and *Scaladocs* (recommended), go to [scala-lang.org](http://scala-lang.org), but this isn't strictly required.

### Editors, IntelliJ, Visual Studio Code, and Other IDEs

Most editors and IDEs now have some sort of Scala support:

* [IntelliJ](https://www.jetbrains.com/idea/): Either the Community or Ultimate additions will work. Install the Scala plugin, which has built-in support for SBT.
* [Visual Studio Code](https://code.visualstudio.com/): Use the new [Scala Metals](https://scalameta.org/metals/) plugin instead of older plugins.

For other IDEs and text editors, try [Scala Metals](https://scalameta.org/metals/). I've used it with [Sublime Text](https://www.sublimetext.com/), for example. You may also need additional, third-party tools for syntax highlighting, etc.

After installing the required plugins, load this project in your IDE, which should detect and use the SBT project automatically.

## Building the Code Examples

After installing SBT, open a command/terminal window and run the `sbt test` command. By default, it uses Scala 3.0. To build and test for Scala 2.14 _and_ 3.0, run `sbt +test`.

Outside of SBT, you could, in principle, run the script files manually at the console/terminal prompt.

    scala src/main/scala/.../foo.sc

However, many of the scripts require other project code that has been compiled (which is in `target/scala-.../classes`) and occasionally third-party libraries that are part of the project dependencies.

For example, if build artifacts are required on the class path, use the following command from the *root* directory of the distribution:

    scala -classpath target/scala-.../classes src/main/scala/.../foo.sc

Usually, the best way to run the scripts is to start `sbt` and run `console` to start the Scala REPL with all the dependencies added to the classpath. Then, use the REPL `:load src/main/scala/.../foo.sc` to load and run the script.

## Feedback

I welcome feedback on the book and these examples. Please post comments, corrections, etc. to one of the following places:

* This GitHub repo's [Gitter channel](https://gitter.im/deanwampler/prog-scala-2nd-ed-code-examples) or [Issues](https://github.com/deanwampler/prog-scala-2nd-ed-code-examples/issues)
* The book's Twitter account, [@ProgScala](https://twitter.com/ProgScala)
* The O'Reilly book site, [Programming Scala, Third Edition](http://shop.oreilly.com/product/todo)
* The [O'Reilly errata page](http://oreilly.com/catalog/errata.csp?isbn=todo)

There is also a dedicated site for the book where occasional updates, clarifications, corrections, and lame excuses will be posted: [programming-scala.org](http://programming-scala.org).
