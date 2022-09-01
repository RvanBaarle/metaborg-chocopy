# metaborg-chocopy

This repository contains an implementation of the [ChocoPy](https://chocopy.org/) programming language, with additional support for Python 3.6+-style exceptions. The implementation is written using version 3 of the [Spoofax language workbench](https://spoofax.dev/spoofax-pie/develop/). Part of this project was written as part as a case-study for [Dynamix: A Domain-Specific Language for Dynamic Semantics](http://resolver.tudelft.nl/uuid:8653ab24-a782-41f0-aefc-6b1c8d9a37d5).

You can import this repository in your Spoofax 3 eclipse instance by following the steps [here](https://www.spoofax.dev/spoofax-pie/develop/guide/eclipse_lwb/import/).

## Exception Extensions

This version of ChocoPy has additional support for exceptions. In particular, the following constructs have been added:

```python
raise exp

try:
    body
except ClassName as ident:
    body
finally:
    body
```

The behavior of exceptions largely mimics that of exceptions in Python, with a few key differences:
- Raised exceptions can be any object of any class, and do not need to inherit `Exception` (there's no `Exception` in ChocoPy).
- Caught exceptions bound in `except` blocks must be declared beforehand, similar to the loop variable for `for` blocks.
- Classes declared in an `except` block must match **exactly**. If `Bar` is a subclass of `Foo`, an `except Foo as ex:` block will ONLY catch `Foo` instances, not `Bar` instances.

## Contents

This language project contains the following parts:
- `chocopy/src/syntax`: The SDF3 grammar definition for ChocoPy, with extensions for exceptions.
- `chocopy/src/statics`: The Statix specification for ChocoPy, with extensions for exceptions and tagging for boxing operations.
- `chocopy/src/dynamics`: The Dynamix specification for ChocoPy, with extensions for exceptions and support for automatic boxing.

## Acknowledgements

The original SDF3 grammar and Statix specification for ChocoPy was written by [Alexander Sterk](https://github.com/AlexSterk) and [Tim Nederveen](https://github.com/jptned). Adjustments to add support for exceptions, as well as the Dynamix specification, are courtesy of [Thijs Molendijk](https://github.com/molenzwiebel). 

## License

The files in this repository are licensed under the [Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).
You may use the files in this repository in compliance with the license.