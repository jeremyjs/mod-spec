# Mod Spec

The Mod Spec is the specification of a powerful, general-purpose programming language.

The intent of the Mod Spec is that if you were to implement all features from the Mod Spec in the same language, you would have the Mod programming language.

By enforcing this distinction between the Mod Spec and Mod itself, we are able to iterate on the programming language design independent of any specific constraints or implementation decisions inherent in the existing implementation of Mod. Ideally, readers will understand the implications of the Mod Spec and propose improvements or create an alternative spec describing a language more powerful than Mod. Ideally, existing languages will be inspired by features described within the Mod Spec to improve and expand upon their existing language features.

## Table of Contents

- Unicode
- I18n
- Modules, Libraries, Programs, & Services
- Packages
- Types
  - Functions
  - Values
    - Numbers
    - Strings
    - Regex
  - Data Structures
    - Sets
    - Lists
    - Maps
    - Tuples
    - Graphs
- Streams
- Network
- Concurrency
- Security
- Testing

## Unicode

The language supports unicode characters. They may be used for all variable names, operators, and language keywords.

## I18N

The language supports programming in your native language.

## Modules, Libraries, Programs, & Services

Every File in the Codebase is a Module. Every Module is either a Library, Program, or Service. Only a Program or Service may be run. A Program or Service must have a Main Function. A Library can be loaded but has no Main Function. A Simple Program is meant to complete in a finite amount of time, producing side-effects (Events) or results (Values). A Service is a special kind of Program meant to run indefinitely and continue to perform tasks, subscribe to Events, or respond to external Requests until stopped.

## Packages

Any Module may be hosted in a Package Repository. Package metadata is defined in the Root Module for the Package. Packages are stored in a single Package Repository on the filesystem for local development. Package management is provided by the language. Package management is secure by default by implementing cryptographic standards.

## Types

Base Types
- Null
- Function (Operator)
- Value (Literal or Expression)
  - Boolean
  - Number (see: #Numbers)
  - Char
  - String (List of Char)
  - Regex
- Data Structure
  - Set
  - List (Array / Collection)
  - Map (Object / Dictionary)
  - Tuple (Array)
  - Graph
- Event

A Function Signature must be strictly typed (i.e. each parameter passed to the Function Call must be of the correct Type as defined by the Function Signature / inferred from the Function; the Return Value of a Function must be of the same Type as defined by the Function Signature / inferred from the Function). Types may be inferred whenever possible. Properties or Values within Types may be optional. Lists / Collections require that items are all of the same Type. Tuples may have items of different Types. Empty Values are allowed, but rarely useful.

New Composite Types or Alias Types may be specified within any Module.

Variables and Function Signatures may be annotated with Types. Otherwise, Types are inferred. Static Analysis should occur instantaneously during development. Type Ambiguity must be corrected before a Program may be run.

### Under Consideration

Graph Node Values must all have the same Type.

## Functions

The language supports Function-Level Programming [wikipedia](https://en.wikipedia.org/wiki/Function-level_programming).

A Function is defined as a List of Operations (an Operation is a Function Call or Expression. An Expression is a statement which evaluates to a Value or Event Publication). Side-effects are Event Publications. Errors are Event Publications. The Return Value of a Function is always a Tuple of (Value, List of Event Publications). Event Publications may be emitted as they are evaluated (Output Stream).

### Function Signatures

Function Signatures support spread of List or Object (named parameters). Function Signatures support default values.

## Numbers

Mathematics in programming has one primary tradeoff. Either the use case prefers accuracy / precision and is willing to trade off performance, or the use case prefers performance and is willing to trade off accuracy / precision. In the rare case the use case is not willing to trade off either, prefer accuracy / precision over performance.

There are four Number Types: Integer, Rational, Decimal, and [Binary Floating Point](https://en.wikipedia.org/wiki/IEEE_754)

These types are inferred by default but may be explicitly ascribed to Literal Values to enforce accuracy / precision or performance requirements.

Integer is internally represented according to number of digits.

Rational is internally represented as a ratio of two Integers.

Decimal is internally represented as a tuple of two Integers (one before and one after the decimal).

### Under Consideration

Is there anything to be gained by adopting support for [DEC64](http://dec64.com/)?

The Mod Spec is considering adding support for higher mathematical concerns such as imaginary and transcendental numbers.

## Strings

String is implemented as List of Char.

## Regex

TODO

## Sets

TODO

## Lists

TODO

## Maps

TODO

## Tuples

TODO

## Graphs

TODO

## Streams

Streams are an asynchronous communication channel.

TODO: add implementation details.

## Network

A Program may listen on a port or ports for Requests and reply with Responses. A Program may make external Requests and receive Responses. A Program may engage in higher order protocol behavior such as websocket communication.

### Message Broker

A Program may emit Events or publish them to Topics. A Program may subscribe to Topics.

### Event Loop

TODO: research the concept of "Event Loop" for usefulness

## Concurrency

The language follows the same ideals as https://golang.org/doc/effective_go.html#concurrency.

Memory is shared by inter-thread communication.

## Security

TODO

## Testing

TODO: We want the most powerful testing somehow.