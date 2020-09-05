##### specifications

grammar | example | language
---- | --- | ---
lit(s) | lit('a') | {a}
seq(x, y) | seq(lit('a'), lit('b')) | {ab}
alt(x, y) | alt(lit('a'), lit('b')) | {a, b}
star(x) | star(lit('a')) | {'', a, aa, aaa, ...}
oneof(c) | oneof('abc') | {a, b, c}
eol | eol| {''}
 | seq(lit('a', eol)) | {a}
dot | dot | {a,b, c, ...}

interpreter
* an interpreter takes a pattern and a text and operator

compiler

1.
*  compilation function return a compiled object
*  execution of that compiled object
2.
* a description for what the pattern look like
* a description for what the compiled code look like
