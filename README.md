#Penlight Lua Libraries

##Why a new set of libraries?

Penlight brings together a set of generally useful pure Lua modules,
focussing on input data handling (such as reading configuration files),
functional programming (such as map, reduce, placeholder expressions,etc),
and OS path management.  Much of the functionality is inspired by the
Python standard libraries.

## Module Overview

### Paths, Files and Directories

  * `path`: queries like `isdir`,`isfile`,`exists`, splitting paths like `dirname` and `basename`
  * `dir`: listing files in directories (`getfiles`,`getallfiles`) and creating/removing directory paths
  * `file`: `copy`,`move`; read/write contents with `read` and `write`

### Application Support

  * `app`: `require_here` to rebase `require` to work with main script path; simple argument parsing `parse_args`
  * `lapp`: sophisticated usage-text-driven argument parsing for applications
  * `config`: flexibly read Unix config files and Windows INI files
  * `strict`: check for undefined global variables - can use `strict.module` for modules
  * `utils`,`compat`: Penlight support for unified Lua 5.1/5.2 codebases
  * `types`: predicates like `is_callable` and `is_integer`; extended `type` function.

### Extra String Operations

  * `utils`: can split a string with a delimiter using `utils.split`
  * `stringx`: extended string functions covering the Python `string` type
  * `stringio`:  open strings for reading, and creating strings using standard Lua IO methods
  * `lexer`:  lexical scanner for splitting text into tokens; special cases for Lua and C
  * `text`:  indenting and dedenting text, wrapping paragraphs; optionally make `%` work as in Python
  * `template`:  small but powerful template expansion engine
  * `sip`:  Simple Input Patterns - higher-level string patterns for parsing text

### Extra Table Operations

  * `tablex`: copying, comparing and mapping over
  * `pretty`: pretty-printing Lua tables, and various safe ways to load Lua as data
  * `List`: implementation of Python 'list' type - slices, concatenation and partitioning
  * `Map`, `Set`, `OrderedMap`: classes for specialized kinds of tables
  * `Data`: reading tabular data into 2D arrays and efficient queries
  * `array2d`: operations on 2D arrays
  * `permute`: generate permutations

 ### Iterators, OOP and Functional

   * `seq`:  working with iterator pipelines; collecting iterators as tables
   * `class`: a simple reusable class framework
   * `func`: symbolic manipulation of expressions and lambda expressions
   * `utils`: `utils.string_lambda` converts short strings like '|x| x^2' into functions
   * `comprehension`: list comprehensions: `C'x for x=1,4'()=={1,2,3,4}`

##Requirements

The file and directory functions depend on LuaFileSystem (lfs). If you want
dir.copyfile to work elegantly on Windows, then you need Alien. (Both are
present in Lua for Windows.)

##Installation

The directory structure is

  lua
     pl
       (module files)
  examples
      (examples)
  tests
      (tests)
  docs
    (index.html)
    api
       (index.html)
       modules

All you need to do is copy the pl directory into your Lua module path, which
is typically /usr/local/share/lua/5.1 on a Linux system (of course, you
can set LUA_PATH appropriately.)

With Lua for Windows,  if LUA stands for 'c:\Program Files\Lua\5.1',
then pl goes into LUA\lua, docs goes into LUA\examples\penlight and
both examples and tests goes into LUA\examples

##Building the Documentation

Requires [ldoc](https://github.com/stevedonovan/LDoc), which is available
through LuaRocks.  Then it's a simple matter of running ldoc in the docs folder.

Penlight/docs$ ldoc .

