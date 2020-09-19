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


##### N Ary function
* from f(x, y) -> f(x...)
    *. f = g(f)

#### Type Of Tools

Debug | Performance | Expressivenes
---- | --- | ---
countcalls | memo | n_arf
trace | |
disable | |


##### Write Grammar
* Grammar
* Language

###### descriptionary
    Exp    => Term[+-] Exp | Term
    Term   => Factor | [*/] Term | Factor
    Factor => Funcall | Var | Num |[(] Exp [)]
    Funcall=> Var [(] Exps [)]
    Exps   => Exp, Exps | Exp
    Var    => [a-zA-z]\w*
    Num    => [-+]?[0-9]+(.[0-9]*)?
