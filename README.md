# Mini-Language-Lexical-Analyzer

[Full Documentation](https://github.com/monicahomescu/Mini-Language-Lexical-Analyzer/blob/main/documentation.pdf)

### Lexic

    Alphabet:
    	a. lower (a-z) and upper (A-Z) case letters of the English alphabet
    	b. decimal digits (0-9)
    
    Lexic:

	a.special symbols
	- operators
		+ - * / % = < <= == != => >
	- separators
		, : [ ] ( ) { }
	- reserved words
		program input output int char str given then otherwise aslongas repeat

	b.identifiers
	- a sequence of letters such that the first character is a #
		identifier ::= #letter | #letter{letter}
		letter ::= "a" | "b" | ... | "z" | "A" | "B" | ... | "Z"

	c.constants
	- integer
		integer ::= "0" | number | "-"number
		number ::= nonzerodigit{digit}
		digit ::= "0" | nonzerodigit
		nonzerodigit ::= "1" | ... | "9"
	- character
		character ::= 'letter' | 'digit'
	- string
		string ::= "char{char}"
		char ::= letter | digit

  ### Syntax

    program ::= "program" "{" decllist "\n" cmpdstmt "}"
    decllist ::= declaration | declaration "," decllist
    declaration ::= type ":" identifier
    type1 ::= "INT" | "CHAR" | "STR"
    arraydecl ::= type1 "[" number "]"
    type ::= type1 | arraydecl
    cmpdstmt ::= "{" stmtlist "}"
    stmtlist ::= stmt | stmt "\n" stmtlist
    stmt ::= simplstmt | structstmt
    simplstmt ::= assignstmt | iostmt | decllist
    assignstmt ::= identifier "=" expression
    expression ::= expression "+" term | term
    term ::= term "*" factor | factor
    factor ::= "(" expression ")" | identifier | const
    iostmt ::= "INPUT" "(" identifier ")" | "OUTPUT" "(" identifier ")" | "OUTPUT" "(" const ")"
    structstmt ::= cmpdstmt | ifstmt | whilestmt
    ifstmt ::= "GIVEN" "(" condition ")" "THEN" cmpdstmt ["OTHERWISE" cmpdstmt]
    whilestmt ::= "ASLONGAS" "(" condition ")" "REPEAT" cmpdstmt
    condition ::= expression relation expression
    relation ::= "<" | "<=" | "==" | "!=" | ">=" | ">"
