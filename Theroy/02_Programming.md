# Need for progamming

computer has a control unit composed of the logic gates and then based on the instruction provided the control unit do the sepecific task for example if we assign 1001 instruction to the adding function whenever  control unit sees 1001 it adds the number so thats how using the control unit progamm is executed its a two stage process
- Doing the action
- Saving the action

## Problems
In the early stages beacuse of this approach the problem arose as we hv to input the machine code 1s and 0s to perform the action these were done uses swotches punch cards etc to input the data

## Solution
Based on the problem the solution which was deduced was to use the compilier its the software that converts the high level code into low level machine code

- The code is written in human readable way source code
- compiler takes the code
- converts it into binary code machine code

# Steps before Interpretation

## lexical Analysis / Tokenzation
It breaks down the text into token the token can have two values like for 3 it can store 3 as a value and int as its type for + it can store + as value and operators as the type so this is the lexical analysis the process of breaking down the input into tokens which will b stored in the list and then this will b passed to the parser
if we have to code like
1 + 3
it will return
[token(1,INT),token(+,OP),token(3,INT)]

## Parser / Parsing
It is used to process the tokens given by the lexical analysis to process em we will use the parser. In simple way parsing is understanding the patterns in the data
the parser does this using the bunch of the grammer rules for example we create a rule that our language can only add 2 numbers then this is the rule so the next time when we will give it the list of token it will look that the first token is int the second is operater and the third is int as well and then in doing so it can give us the output

### ways to write the rules in parser
- BNF : Its a way of writing the grammer rules example
The things in the <> are called the non terminal whereas the things like numbers and operators are called terminal
<expression> := <term> + <expression> | <term> - <expression> | <term> its a way of writing the rules the line repsent or

E = Term ((+|-)T)* The straic outside shows that the term inside the bracket can b repeated 0 or more times

<term> := <factor> * <term> | <factor> / <term> | <factor>

<Factor> := <integer>
<integer> := 0|1|2|3|......n 

### How will we parse 1+2*5
For this we will use the parser and the parser converts it into the binary tree and it can b written as 
[1+[2*5]]

### Expession
Its the term that is added or subtracted from any other term or a value 

### tree
For the equation [1+[2*5]] the tree can be

root node : +
left child : 1
right child : *
childs of right child
left child : 2
right child : 5