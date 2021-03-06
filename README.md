# py-compiler

This program has two modes: **compiler** and **pre-interpreter**.

## Pre-interpreter

The pre-interpreter scans the source code for syntax errors in order to generate a json file with all the useful informations. This json can then be given to [Endiver](https://github.com/NoKe-Language/Endiver) in order to execute the file.
- **Why a pre-interpreter?** There are very useful modules in python to scan and handle the source file, while Crystal is very fast for the execution.
- **It is complicated...** It is, but in the future, [Endiver](https://github.com/NoKe-Language/Endiver) will include the python pre-compiler.
The pre-interpreter is fully functionnal for the current implemented features of NoKe.

## Compiler

The compiler does not generate a json file, but goes further with the analysis. Basically, it generates an executable from the source code. 
- **Why python** ? Because it is flexible and provides useful modules to handle strings. Eventually, the compiler will be translated, but nowadays, python is not as slow as before.

The compiler is not currently functionnal, please use [Endiver](https://github.com/NoKe-Language/Endiver) for now.

## How to use

This program supports command line options and arguments.

Format : ``python ncompiler.py <source_file> [options]``

- **source_file**: The path to the .idk file. Currently, NoKe doesn't handle multiple files.
- **options**: (optional)
    - ``--output <output_file>`` or ``-o <output_file>`` : The path to the output file (executable if compiler, json if interpreter).
    - ``--verbose`` or ``-v`` : Enable log.
    - ``--override`` or ``-o`` : Always override output file.
    
    One of these: (not both)
    - ``--compile`` or ``-c`` : Compile the NoKe script.
    - ``--interpret`` or ``-i`` : Convert the NoKe script to a .json file to use with [Endiver](https://github.com/NoKe-Language/Endiver). (default)

Exemple : ``python ncompiler.py main.idk -i -o output.json --verbose`` 


## Milestones
### Completed
- **Syntax**: Agree on a syntax for NoKe
- **Parser** : Converts the source code into an absract syntax tree (AST).
- **Error** : Handle exceptions, syntax errors, locate error in the source code ...
- **Json exporter**: Exports the AST to a json file that can be interpreted by [Endiver](https://github.com/NoKe-Language/Endiver).
- **Command line support** : support for a command line usage (such as ``ncompiler main.idk -i``)
### To do
- **Find a good name for the compiler** : because "compiler" is too generic ^^
- **Official documentation** for NoKe
- **Semantic analysis** : Check if the source code is semantically coherent
- **Translator** : Convert the AST into intermediate code (3AC)
- **Optimizer** : Optimize the 3AC
- **Assembly translation** : Convert the 3AC to Assembly language.

## Implemented NoKe features
NoKe **can** currently handle :
- **Modules** : A set of other modules (Module, class, function).
- **Functions** : A set of statements or modules.
- **Call** : Call a function
- **Branch** : if/else if/else
- **For loop**
- **While/Do While loop**
- **Assignement**
- **Declaration**
- **Operation/Comparison**
- **Variables**

NoKe **cannot** currently handle: (but will in the future)
- **Classes**
- **"var" type** : Auto type selector
- **Multiple files**
- **Imports**
- **Foreach** loop
- **Events**
- **Data structures** (arrays, etc)

NoKe **cannot** currently handle: (not sure if it will)
- **Delegates/function pointers/...** : Store a function ref in a variable
- **Pointers**
- **public, private, protected... keywords**
- **Multithreading**
