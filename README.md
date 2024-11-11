Ex-5-RECOGNITION-OF-THE-GRAMMAR-anb-where-n-10-USING-YACC
NAME:N.Inesh
reg.no:212223220036
RECOGNITION OF THE GRAMMAR(anb where n>=10) USING YACC

Aim:
To write a YACC program to recognize the grammar anb where n>=10.

ALGORITHM
Start the program.
Write a program in the vi editor and save it with .l extension.
In the lex program, write the translation rules for the variables a and b.
Write a program in the vi editor and save it with .y extension.
Compile the lex program with lex compiler to produce output file as lex.yy.c. eg $ lex filename.l
Compile the yacc program with yacc compiler to produce output file as y.tab.c. eg $ yacc –d arith_id.y
Compile these with the C compiler as gcc lex.yy.c y.tab.c
Enter a string as input and it is identified as valid or invalid.
PROGRAM:
Grammar.l:

%{
#include "y.tab.h"
%}

%%
a    { return A; }  // Recognize 'a' as token A
b    { return B; }  // Recognize 'b' as token B
.    { return 0; }  // End of input
%%

int yywrap() {
    return 1;
}
Grammar.y:

%{
#include <stdio.h>
int yylex(void);
void yyerror(const char *s);
%}

%token A B

%%
S   : A A A A A A A A A A B    { printf("Valid string\n"); }
    | A S B                    { printf("Valid string\n"); }
    ;

%%

int main() {
    printf("Enter a string:\n");
    yyparse();
    return 0;
}

void yyerror(const char *s) {
    printf("Invalid string\n");
}
OUTPUT
Screenshot 2024-10-24 133423

RESULT
The YACC program to recognize the grammar anb where n>=10 is executed successfully and the output is verified.

