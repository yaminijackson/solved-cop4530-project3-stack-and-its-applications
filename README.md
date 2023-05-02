Download Link: https://assignmentchef.com/product/solved-cop4530-project3-stack-and-its-applications
<br>
<h2><span style="font-size: 16px;">Understand the stack ADT and its applications. Understand infix to postfix conversion and postfix expression evaluation.</span></h2>

<strong>Statement of Work:</strong> Implement a generic stack container as an adaptor class template. Implement a program that converts infix expression to postfix expression and implement a program that evaluates postfix expression using the stack container you develop.

<strong>Project Description:  </strong>

A <strong>Stack</strong> is a type of data container/ data structure that implements the LAST-IN-FIRST-OUT (LIFO) strategy for inserting and recovering data. This is a very useful strategy, related to many types of natural programming tasks as we have discussed in class.

Remember that in the generic programming paradigm, every data structure is supposed to provide <em>encapsulation</em> of the data collection, enabling the programmer to interact with the entire data structure in a meaningful way as a <strong>container of data</strong>. By freeing the programmer from having to know its implementation details and only exporting the interface of its efficient operations, a generic <strong>Stack</strong> provides separation of data access/manipulation from internal data representation. Programs that access the generic <strong>Stack</strong> only through the interface can be re-used with any other <strong>Stack</strong> implementation. This results in modular programs with clear functionality and that are more manageable.

<strong><u>Goals:  </u></strong>

<ol>

 <li>Implement a generic Stack as an adaptor class template</li>

 <li>Write a program that parses infix arithmetic expressions to postfix arithmetic expressions using a Stack</li>

 <li>Write a program that evaluates postfix arithmetic expressions using a Stack</li>

</ol>

More detailed descriptions for each of the above tasks are now provided.

<strong><u>Task1: Implement Stack adaptor class template:</u></strong>

<ul>

 <li><strong>Stack</strong> MUST store elements internally using a proper C++ STL container — which one is your choice (of course, you may not use the C++ STL stack container as the internal container).</li>

 <li>Your<strong> Stack</strong> implementation MUST:

  <ul>

   <li>be able to store elements of an arbitrary type.</li>

   <li>Every <strong>Stack</strong> instance MUST accept insertions as long as the system has enough free memory.</li>

  </ul></li>

 <li><strong>Stack</strong> MUST implement the full interface specified below</li>

 <li>You MUST provide the template and the implementation in two different files stack.h and stack.hpp, respectively. You must include stack.hpp into stack.h</li>

</ul>

<ul>

 <li>Your stack implementation MUST be in the namespace cop4530.</li>

</ul>

<strong><u>Interface:  </u></strong>

The interface of the<strong> Stack</strong> class template is specified below.

<strong>Stack()</strong>: zero-argument constructor.

<strong>~Stack ()</strong>: destructor.

<strong>Stack</strong> <strong>(const Stack&lt;T&gt;&amp;)</strong>: copy constructor.

<strong>Stack(Stack&lt;T&gt; &amp;&amp;)</strong>: move constructor.

<strong>Stack&lt;T&gt;&amp; operator= (const Stack &lt;T&gt;&amp;)</strong>: copy assignment operator=.

<strong>Stack&lt;T&gt; &amp; operator=(Stack&lt;T&gt; &amp;&amp;)</strong>: move assignment operator=

<strong>bool empty() const</strong>: returns true if the <strong>Stack</strong> contains no elements, and false otherwise.

void clear(): delete all elements from the stack.

<strong>void push(const T&amp; x)</strong>: adds  x  to the <strong>Stack</strong>.   copy version.

<strong>void push(T &amp;&amp; x)</strong>: adds x to the Stack. move version.

<strong>void pop()</strong>: removes and discards the most recently added element of the <strong>Stack</strong>.

<strong>T&amp; top()</strong>: returns a reference to the most recently added element of the <strong>Stack</strong> (as a modifiable L-value).

<strong>const T&amp; top() const</strong>: accessor that returns the most recently added element of the <strong>Stack</strong> (as a const reference)

<strong>int size() const</strong>: returns the number of elements stored in the <strong>Stack</strong>.

<strong>void print(std::ostream&amp; os, char ofc = ‘ ‘) const</strong>: print elements of Stack to ostream os. ofc is the separator between elements in the stack when they are printed out. <em>Note that print() prints elements in the opposite order of the Stack (that is, the oldest element should be printed first).</em>

The following non-member functions should also be supported.

<strong>std::ostream&amp; operator&lt;&lt; (std::ostream&amp; os, const Stack&lt;T&gt;&amp; a)</strong>: invokes the <strong>print()</strong> method to print the <strong>Stack&lt;T&gt; a</strong> in the specified ostream

<strong>bool operator== (const Stack&lt;T&gt;&amp;, const Stack &lt;T&gt;&amp;)</strong>: returns true if the two compared <strong>Stack</strong>s have the same elements, in the same order, and false otherwise

<strong>bool operator!= (const Stack&lt;T&gt;&amp;, const Stack &lt;T&gt;&amp;)</strong>: opposite of operator==().

<strong>bool operator&lt;= (const Stack&lt;T&gt;&amp; a, const Stack &lt;T&gt;&amp; b)</strong>: returns true if every element in <strong>Stack</strong> <strong>a</strong> is smaller than or equal to the corresponding element of<strong> Stack b</strong>, i.e., if repeatedly invoking top() and pop() on both <strong>a</strong> and <strong>b, </strong> we will generate a sequence of elements a<sub>i</sub> from a and b<sub>i</sub> from b, and for every i,  a<sub>i</sub> ≤ b<sub>i</sub>, until <strong>a</strong> is empty. (Note that this also means that <strong>a</strong> cannot have more elements than <strong>b</strong> for this condition to be true). Return false otherwise.

Analyze the worst-case run-time complexity of the member function clear() of Stack. Give the complexity in the form of Big-O. Your analysis can be informal; however, it must be clearly understandable by others.  Note that the time complexity of the function clear() depends on the underlying adaptee class you use for the implementation of Stack. Name the file containing the complexity analysis as “analysis.txt”, in which, you should state the time complexity of clear() in the Big-O notation, your discussions on why it is so, in particular, you need to include the information on the underlying adaptee class you used in the implementation of the Stack.

<strong><u>Task2: Convert infix arithmetic expressions into postfix arithmetic expressions and evaluate them (whenever possible)</u></strong>

For the sake of this exercise, an arithmetic expression is a sequence of <strong>space-separated</strong> strings. Each string can represent an operand, an operator, or parentheses.

Operands: can be either a numerical value or a variable. A variable name only consists of alphanumerical letters and the underscore letter “_”. A variable name starts with a English letter. Numerical operands can be either integer or floating point values.

Examples of operands: “34”, “5”, “5.3”, “a”, “ab”, “b1”, and “a_1”

Operators: one of the characters ‘+’, ‘-‘, ‘*’, or ‘/’. As usual, ‘*’ and ‘/’ are regarded as having higher precedence than ‘+’ or ‘-‘. Note that all supported operators are binary, that is, they require two operands.

Parentheses: ‘(‘ or ‘)’

An Infix arithmetic expression is the most common form of arithmetic expression used.

Examples:

( 5 + 3 ) * 12  – 7  is an infix arithmetic expression that evaluates to 89

5 + 3 * 12 – 7 is an infix arithmetic expression that evaluates to 34

For the sake of comparison, postfix arithmetic expressions (also known as reverse Polish notation) equivalent to the above examples are:

5 3 + 12 * 7 –

5 3 12 * + 7 –

Two characteristics of the Postfix notation are (1) any operator, such as ‘+’ or ‘/’ is applied to the two prior operand values, and (2) it does not require the use of parenthesis.

More examples:

a + b1 * c + ( dd * e + f ) * G  in Infix notation becomes

a b1 c * +  dd e * f + G * +  in Postfix notation

To implement infix to postfix conversion with a stack, one parses the expression as sequence of <strong>space-separated</strong> strings. When an operand is read in the input, it is immediately output.  Operators (e.g., ‘-‘, ‘*’) may have to be saved by placement in an operator stack. We also stack left parentheses. Start with an initially empty operator stack.

Follow these 4 rules for processing operators/parentheses:

<ol>

 <li>If input symbol is ‘(‘, push it into stack.</li>

</ol>

<ol>

 <li>If input operator is ‘+’, ‘-‘, ‘*’, or ‘/’, repeatedly print the top of the stack to the output and pop the stack until the stack is either (i) empty ; (ii) a ‘(‘ is at the top of the stack; or (iii) a lower-precedence operator is at the top of the stack. Then push the input operator into the stack.</li>

</ol>

<ol>

 <li>If input operator is ‘)’ and the last input processed was an operator, report an error. Otherwise, repeatedly print the top of the stack to the output and pop the stack until a ‘(‘ is at the top of the stack. Then pop the stack discarding the parenthesis. If the stack is emptied without a ‘(‘ being found, report error.</li>

</ol>

<ol>

 <li>If end of input is reached and the last input processed was an operator or ‘(‘, report an error. Otherwise print the top of the stack to the output and pop the stack until the stack is empty.  If an ‘(‘ is found in the stack during this process, report error.</li>

</ol>

For more details on how the conversion works, look up the lecture notes and Section 3.6 of the textbook.

<strong><u>Evaluating postfix arithmetic expressions </u></strong>

After converting a given expression in infix notation to postfix notation, you will evaluate the resulting arithmetic expression IF all the operands are numeric (int, float, etc.) values. Otherwise, if the resulting postfix expression contains characters, your output should be the same as the input (the postfix expression).

Example inputs:

5 3 + 12 * 7 –

5 3 12 * + 7 –

3 5 * c – 10 /

Example outputs:

89

34

3 5 * c – 10 /

To achieve this, you will have an operand stack, initially empty. Assume that the expression contains only numeric operands (no variable names). Operands are pushed into the stack as they are ready from the input. When an operator is read from the input, remove the two values on the top of the stack, apply the operator to them, and push the result onto the stack. If an operator is read and the stack has fewer than two elements in it, report an error.  If end of input is reached and the stack has more than one operand left in it, report an error. If end of input is reached and the stack has exactly one operand in it, print that as the final result, or 0 if the stack is empty.

For more information on the evaluation of postfix notation arithmetic expressions, look up the lecture notes and Section 3.6 of the textbook.

<strong><u>Summarizing task 2</u></strong>.

Your program should expect as input from (possibly re-directed) stdin a series of space-separated strings. Each line of input is one expression. Each of the space-separated strings within the line is a token (an operand, an operator, or a parethesis). The user should type “exit” on a single line to end processing the inputs.

Regarding tokens: If you read a1 (no space) this is the name of the variable a1 and not “a” followed by “1”.  Similarly, if you read “bb 12”, this is a variable “bb” followed by the number “12” and not “b” ,”b”, “12” or “bb”, “1” ,”2″.

For each expression (i.e. each line of input), the resulting postfix expression should be printed to stdout, followed by the evaluation of the expression. If the expression contains only numeric operands, evaluate the expression (using the post-fix evaluation algorithm described above) and print the results to stdout. If the expression contains variable names (i.e. not just numeric operands), then just print out the postfix expression in this spot.

<strong><u>Restrictions </u></strong>

The infix to postfix conversion MUST be able to convert expressions containing both numbers and variable names.

Your program MUST be able to produce floating number evaluation (i.e., deal with floats correctly).

Your program MUST NOT attempt to evaluate postfix expressions containing variable names. It should print the postfix-converted result to stdout and MAY NOT throw an exception nor reach a runtime error in that case.

Your program MUST check for mismatched parentheses (this should be taken care of if you infix to postifx expression conversion is performed properly.

Your program MUST check invalid infix expressions and report errors. We consider the following types of infix expressions as invalid expressions: 1) an operator does not have the corresponding operands, 2) an operand does not have the corresponding operator; or ) mismatched parentheses. Note that some checks can be performed in the expression conversion or postfix evaluation.

Your program MUST re-prompt the user for the next infix expression. Your program must be able to process several inputs before terminating (check the provided executable in2post.x to see the behavior of the program).

<strong>Deliverable Requirements</strong>

Your implementation should be contained in three files, which MUST be named stack.h, stack.hpp and in2post.cpp. Submit your implementation in a tar file including the three files (stack.h, stack.hpp, and in2post.cpp), the makefile you use, and the analysis.txt file for time complexity of the clear() function of Stack.

<strong>Sample Executable Code</strong>

<a href="https://www.cs.fsu.edu/~myers/cop4530/hw/hw3files">AT THIS LINK</a> you can download a sample test driver (test_stack1.cpp) for the Stack class, as well as an example test file (test0.txt) for your in2post main program. You are encouraged to come up with more test cases, for testing Stack features and for testing your Infix-To-Postfix program. The provided files are just a few sample tests, but they do not necessarily comprise a thorough test suite.

You can also run our sample executable for in2post.x from linprog, at the location: ~myers/dsprog/in2post.x. So for example, run the test file given above with the command:

~myers/dsprog/in2post.x &lt; test0.txt


