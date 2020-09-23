# ANTLR v4

[![Java 11+](https://img.shields.io/badge/java-11+-4c7e9f.svg)](http://java.oracle.com)
[![License](https://img.shields.io/badge/license-BSD-blue.svg)](https://raw.githubusercontent.com/antlr/antlr4/master/LICENSE.txt)


## Versioning

ANTLR 4 supports 10 target languages, and ensuring consistency across these targets is a unique and highly valuable feature.
To ensure proper support of this feature, each release of ANTLR is a complete release of the tool and the 10 runtimes, all with the same version.
As such, ANTLR versioning does not strictly follow semver semantics:

* a component may be released with the latest version number even though nothing has changed within that component since the previous release
* major version is bumped only when ANTLR is rewritten for a totally new "generation", such as ANTLR3 -> ANTLR4 (LL(\*) -> ALL(\*) parsing)
* minor version updates may include minor breaking changes, the policy is to regenerate parsers with every release (4.11 -> 4.12)
* backwards compatibility is only guaranteed for patch version bumps (4.11.1 -> 4.11.2)

If you use a semver verifier in your CI, you probably want to apply special rules for ANTLR, such as treating minor change as a major change.

**ANTLR** (ANother Tool for Language Recognition) is a powerful parser generator for reading, processing, executing, or translating structured text or binary files. It's widely used to build languages, tools, and frameworks. From a grammar, ANTLR generates a parser that can build parse trees and also generates a listener interface (or visitor) that makes it easy to respond to the recognition of phrases of interest.

**Dev branch build status**

[![MacOSX, Windows, Linux](https://github.com/antlr/antlr4/actions/workflows/hosted.yml/badge.svg)](https://github.com/antlr/antlr4/actions/workflows/hosted.yml) (github actions)

<!--
* [![Windows](https://github.com/antlr/antlr4/actions/workflows/windows.yml/badge.svg?branch=dev)](https://github.com/antlr/antlr4/actions/workflows/windows.yml) (github actions)

* [![Circle CI Build Status (Linux)](https://img.shields.io/circleci/build/gh/antlr/antlr4/master?label=Linux)](https://app.circleci.com/pipelines/github/antlr/antlr4) (CircleCI)

[![AppVeyor CI Build Status (Windows)](https://img.shields.io/appveyor/build/parrt/antlr4?label=Windows)](https://ci.appveyor.com/project/parrt/antlr4) 
[![Travis-CI Build Status (Swift-Linux)](https://img.shields.io/travis/antlr/antlr4.svg?label=Linux-Swift&branch=master)](https://travis-ci.com/github/antlr/antlr4)
-->

## Repo branch structure

The default branch for this repo is [`master`](https://github.com/antlr/antlr4/tree/master), which is the latest stable release and has tags for the various releases; e.g., see release tag [4.9.3](https://github.com/antlr/antlr4/tree/4.9.3).  Branch [`dev`](https://github.com/antlr/antlr4/tree/dev) is where development occurs between releases and all pull requests should be derived from that branch. The `dev` branch is merged back into `master` to cut a release and the release state is tagged (e.g., with `4.10-rc1` or `4.10`.) Visually our process looks roughly like this:

<img src="doc/images/new-antlr-branches.png" width="500">

Targets such as Go that pull directly from the repository can use the default `master` branch but can also pull from the active `dev` branch:

```bash
$ go get github.com/antlr/antlr4/runtime/Go/antlr@dev
```

## Authors and major contributors

* [Terence Parr](http://www.cs.usfca.edu/~parrt/), parrt@cs.usfca.edu
ANTLR project lead and supreme dictator for life
[University of San Francisco](http://www.usfca.edu/)
* [Sam Harwell](http://tunnelvisionlabs.com/) (Tool co-author, Java and original C# target)
* [Eric Vergnaud](https://github.com/ericvergnaud) (Javascript, Python2, Python3 targets and maintenance of C# target)
* [Peter Boyer](https://github.com/pboyer) (Go target)
* [Mike Lischke](http://www.soft-gems.net/) (C++ completed target)
* Dan McLaughlin (C++ initial target)
* David Sisson (C++ initial target and test)
* [Janyou](https://github.com/janyou) (Swift target)
* [Ewan Mellor](https://github.com/ewanmellor), [Hanzhou Shi](https://github.com/hanjoes) (Swift target merging)
* [Ben Hamilton](https://github.com/bhamiltoncx) (Full Unicode support in serialized ATN and all languages' runtimes for code points > U+FFFF)
* [Marcos Passos](https://github.com/marcospassos) (PHP target)
* [Lingyu Li](https://github.com/lingyv-li) (Dart target)
* [Ivan Kochurkin](https://github.com/KvanTTT) has made major contributions to overall quality, error handling, and Target performance.
* [Justin King](https://github.com/jcking) has done a huge amount of work across multiple targets, but especially for C++.
* [Ken Domino](https://github.com/kaby76) has a knack for finding bugs/issues and analysis; also a major contributor on the [grammars-v4 repo](https://github.com/antlr/grammars-v4).
* [Jim Idle](https://github.com/jimidle) has contributed to previous versions of ANTLR and recently jumped back in to solve a major problem with the Go target.


## Useful information

* [Release notes](https://github.com/antlr/antlr4/releases)
* [Getting started with v4](https://github.com/antlr/antlr4/blob/master/doc/getting-started.md)
* [Official site](http://www.antlr.org/)
* [Documentation](https://github.com/antlr/antlr4/blob/master/doc/index.md)
* [FAQ](https://github.com/antlr/antlr4/blob/master/doc/faq/index.md)
* [ANTLR code generation targets](https://github.com/antlr/antlr4/blob/master/doc/targets.md)<br>(Currently: Java, C#, Python2|3, JavaScript, Go, C++, Swift, Dart, PHP)
* [Java API](http://www.antlr.org/api/Java/index.html)
* [ANTLR v3](http://www.antlr3.org/)
* [v3 to v4 Migration, differences](https://github.com/antlr/antlr4/blob/master/doc/faq/general.md)

You might also find the following pages useful, particularly if you want to mess around with the various target languages.
 
* [How to build ANTLR itself](https://github.com/antlr/antlr4/blob/master/doc/building-antlr.md)
* [How we create and deploy an ANTLR release](https://github.com/antlr/antlr4/blob/master/doc/releasing-antlr.md)

## The Definitive ANTLR 4 Reference

Programmers run into parsing problems all the time. Whether it’s a data format like JSON, a network protocol like SMTP, a server configuration file for Apache, a PostScript/PDF file, or a simple spreadsheet macro language—ANTLR v4 and this book will demystify the process. ANTLR v4 has been rewritten from scratch to make it easier than ever to build parsers and the language applications built on top. This completely rewritten new edition of the bestselling Definitive ANTLR Reference shows you how to take advantage of these new features.

You can buy the book [The Definitive ANTLR 4 Reference](http://amzn.com/1934356999) at amazon or an [electronic version at the publisher's site](https://pragprog.com/book/tpantlr2/the-definitive-antlr-4-reference).

You will find the [Book source code](http://pragprog.com/titles/tpantlr2/source_code) useful.

## Additional grammars
[This repository](https://github.com/antlr/grammars-v4) is a collection of grammars without actions where the
root directory name is the all-lowercase name of the language parsed
by the grammar. For example, java, cpp, csharp, c, etc...

# antlr4rust
ANTLR4 runtime for Rust programming language 

Tool(generator) part is currently located in rust-target branch of my antlr4 fork [rrevenantt/antlr4/tree/rust-target](https://github.com/rrevenantt/antlr4/tree/rust-target)
Latest version is automatically built to [releases](https://github.com/rrevenantt/antlr4rust/releases) on this repository.
Also you can checkout it and `mvn -DskipTests install`

For examples you can see [grammars](grammars), [tests/gen](tests/gen) for corresponding generated code 
and [tests/my_tests.rs](tests/my_test.rs) for actual usage examples

### Implementation status

Everything is implemented, "business" logic is quite stable and well tested, but user facing 
API is not very robust yet and very likely will have some changes.

For now development is going on in this repository 
but eventually it will be merged to main ANTLR4 repo

Currently, requires nightly version of rust. 
This likely will be the case until `coerce_unsize` or some kind of coercion trait is stabilized. 
There are other unstable features in use but only `CoerceUnsized` is essential. 

Remaining things before merge:
 - API stabilization
   - [ ] Rust api guidelines compliance  
   - [ ] more tests for API because it is quite different from Java

Can be done after merge: 
 - more profiling and performance optimizations
 - Documentation
   - [ ] Some things are already documented but still far from perfect, also more links needed.
 - Code quality
   - [ ] Rustfmt fails to run currently
   - [ ] Clippy sanitation 
   - [ ] Not all warning are fixed
 - cfg to not build potentially unnecessary parts 
 (no Lexer if custom token stream, no ParserATNSimulator if LL(1) grammar)  
 - run rustfmt on generated parser
###### Long term improvements
 - generate enum for labeled alternatives without redundant `Error` option
 - option to generate fields instead of getters by default
 - make tree generic over pointer type and allow tree nodes to arena.
 (requires GAT, otherwise it would be a problem for users that want ownership for parse tree)
 - support stable rust
 - support no_std(although alloc would still be required)  
  
### Usage

You should use the ANTLR4 "tool" to generate a parser, that will use the ANTLR 
runtime, located here. You can run it with the following command:
```bash
java -jar <path to ANTLR4 tool> -Dlanguage=Rust MyGrammar.g4
```
For a full list of antlr4 tool options, please visit the 
[tool documentation page](https://github.com/antlr/antlr4/blob/master/doc/tool-options.md).

You can also see [build.rs](build.rs) as an example of `build.rs` configuration 
to rebuild parser automatically if grammar file was changed

Then add following to `Cargo.toml` of the crate from which generated parser 
is going to be used:
```toml 
[dependencies]
antlr-rust = "=0.2"
```
and `#![feature(try_blocks)]`(also `#![feature(specialization)]` if you are generating visitor) in your project root module.  
 
### Parse Tree structure

It is possible to generate idiomatic Rust syntax trees. For this you would need to use labels feature of ANTLR tool.
You can see [Labels](grammars/Labels.g4) grammar for example.
Consider following rule :
```text
e   : a=e op='*' b=e   # mult
    | left=e '+' b=e   # add
		 
```
For such rule ANTLR will generate enum `EContextAll` containing `mult` and `add` alternatives, 
so you will be able to match on them in your code. 
Also corresponding struct for each alternative will contain fields you labeled. 
I.e. for `MultContext` struct will contain `a` and `b` fields containing child subtrees and 
`op` field with `TerminalNode` type which corresponds to individual `Token`.
It also is possible to disable generic parse tree creation to keep only selected children via
`parser.build_parse_trees = false`.
  
### Differences with Java
Although Rust runtime API has been made as close as possible to Java, 
there are quite some differences because Rust is not an OOP language and is much more explicit. 

 - Supports full zero-copy parsing including byte parsers.
 - If you are using labeled alternatives, 
 struct generated for rule is an enum with variant for each alternative
 - Parser needs to have ownership for listeners, but it is possible to get listener back via `ListenerId`
 otherwise `ParseTreeWalker` should be used.
 - In embedded actions to access parser you should use `recog` variable instead of `self`/`this`. 
 This is because predicate have to be inserted into two syntactically different places in generated parser
 - String `InputStream` have different index behavior when there are unicode characters. 
 If you need exactly the same behavior, use `[u32]` based `InputStream`, or implement custom `CharStream`.
 - In actions you have to escape `'` in rust lifetimes with `\ ` because ANTLR considers them as strings, e.g. `Struct<\'lifetime>`
 - To make custom tokens you should use `@tokenfactory` custom action, instead of usual `TokenLabelType` parser option.
 In Rust target TokenFactory is main customisation interface that allows to specify input type of token type. 
 - All rule context variables (rule argument or rule return) should implement `Default + Clone`.
 
### Unsafe
Currently, unsafe is used only to cast from trait object back to original type 
and to update data inside Rc via `get_mut_unchecked`(returned mutable reference is used immediately and not stored anywhere)

### Versioning
In addition to usual Rust semantic versioning, 
patch version changes of the crate should not require updating of generator part 
  
## Licence

BSD 3-clause 
