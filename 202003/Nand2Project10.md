#### Token
* keywords
* symbols
* integers
* Strings
* identifiers


#### Grammer
* terminal rule  
right hand side includes constants only
* Non-terminal rule  
all other rules
* determining if a given input conforms to a grammar  
in the grammatical structure of the given input



#### Paser
* design  
    1. a set of compilerxxx methods, for each non-terminal rule;
    2. the handing of some rules is embedded is other rules

* LL LL(K) LL(1)

* while statements eg:

        compilerwhilestatement() {
            eat("while"); code to handle "while"
            eat("(");
            compilerExpression();
            eat(")");
        }

        eat(string) {
            if (currentToken <> string) {
                error;
            } else {
                advance;
            }
        }


#### JackGrammar
* expressions  
        expression term (op term)*


#### code
should add the line while fault
