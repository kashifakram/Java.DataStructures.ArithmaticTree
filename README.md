# Java.DataStructures.SubmissionHistory

Info 9105								Assignment 2 Report
Kashif Akram – 460458380

TESTS

testTree2Prefix()
Description:
Purpose of this test is to verify the functionality of tree2Prefix() method, i.e. converting the tree to a prefix notation string. We build tree by using prefix2tree() method and compare the output string with expected string.
Inputs:		String "+ 2 + 5 7"
Expected Output: 	String "+ 2 + 5 7"

testInvalidTree2Prefix()
Description:
Purpose of this test is to verify the if tree2Prefix() method validates the given tree. We build an invalid tree by adding operator as one of the external nodes and call tree2Prefix() method in try/catch block and expect IllegalArgumentException on fail test.
Inputs:		Add any operator as leaf node
Expected Output:	Throw IllegalArgumentException on when test fails

testTree2Infix()
Description:
Purpose of this test is to verify the functionality of tree2Infix() method, i.e. converting the tree to a infix notation string. We build a valid tree by adding operators as internal nodes and values as external, then we call tree2Infix() method and compare the output string with expected string.
Inputs:		Building tree from string "+ 2 - a b"
Expected Output: 	String "(2+(a-b))"

testInvalidTree2Infix()
Description:
Purpose of this test is to verify the if tree2Infix() method validates the given tree. We build an invalid tree by adding operator as one of the external nodes and call tree2Infix() method in try/catch block and expect IllegalArgumentException on fail test.
Inputs:		Add any operator as leaf node
Expected Output:	Throw IllegalArgumentException on when test fails

testIsArithmatic()
Description:
Purpose of this test is to verify the functionality of isArithmatic() method, i.e. to test if given tree is a valid arithmetic expression or not.
Inputs:		String " + 5 * 2 8"		String " + 5 * 2 -"
Expected Output: 	True					IllegalArgumentException thrown


testSubtitute()
Description:
Purpose of this test is to verify that testSubtitute() method replaces given variable's existing value with new value. We build a valid tree by adding at least one variable as external node and call subtitute() method to replace variable’s value with new value. Then we test output tree with expected tree.
Inputs:		String "+ 2 - a b" to build tree using prefix2tree()
Expected Output:   substitute(tree, "a", 4) will change tree to "+ 2 - 4 b"

testNullandInvalidSubtitute()
Description:
Purpose of this test is to verify testSubtitute() method with non-existing variable and with invalid tree. First call substitute() with a variable that doesn’t exist in tree and then we try to call substitute() on invalid tree.
Inputs:		String "+ 4 * a c" to build tree using prefix2tree()
Expected Output:   substitute(tree, "d", 5) will return original tree

testSubtituteHashMap()
Description:
Purpose of this test is to verify that testSubtitute() method replaces variables’ values with new values passed as HashMap. We build a valid tree by adding at least two variable as external node and a HashMap having keys as variable names and values as variables’ values. Then we call subtitute() method and test output tree with expected tree.
This test takes care of null and invalid tree as well.
Inputs:		String "+ - c 2 * a b" to build tree using prefix2tree()
Expected Output:   substitute(tree, hm) will change tree to "+ - 4 2 * 2 3" if hm has “a” = 2, “b” = 3 and “c” = 4

tesSimplify()
Description:
Purpose of this test is to verify the functionality of testSimplify() method, i.e. simplifying the arithmetic expressions and merging them in one node.
Inputs:		String " - x + 1 2" to build tree using prefix2tree()
Expected Output:  Tree  "- x 3" returned by testSimplify() method

tesSimplifyFancy()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() method.
Inputs:		String "* + 3 2 - 5 4" to build tree using prefix2tree()
Expected Output:  Tree  "5" returned by testSimplifyFancy() method

tesSimplifyFancy1()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “* 1 x = x”.
Inputs:		String "* 1 c" to build tree using prefix2tree()
Expected Output:  Tree  "c" returned by testSimplifyFancy() method


tesSimplifyFancy2()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “* x 1 = x”.
Inputs:		String "* c 1" to build tree using prefix2tree()
Expected Output:  Tree  "c" returned by testSimplifyFancy() method

tesSimplifyFancy3()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “* 0 x = 0”.
Inputs:		String "* 0 c" to build tree using prefix2tree()
Expected Output:  Tree  "0" returned by testSimplifyFancy() method

tesSimplifyFancy4()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “* x 0 = 0”.
Inputs:		String "* c 0" to build tree using prefix2tree()
Expected Output:  Tree  "0" returned by testSimplifyFancy() method

tesSimplifyFancy5()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “+ x 0 = x”.
Inputs:		String "+ x 0" to build tree using prefix2tree()
Expected Output:  Tree  "x" returned by testSimplifyFancy() method

tesSimplifyFancy6()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “* 0 x = x”.
Inputs:		String "* 0 x" to build tree using prefix2tree()
Expected Output:  Tree  "x" returned by testSimplifyFancy() method

tesSimplifyFancy7()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “- x 0 = x”.
Inputs:		String "- c 0" to build tree using prefix2tree()
Expected Output:  Tree  "c" returned by testSimplifyFancy() method

tesSimplifyFancy8()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “* 0 + a b = 0” (consider whole right or left subtree multiplying with 0).
Inputs:		String "* 0 + a b" to build tree using prefix2tree()
Expected Output:  Tree  "0" returned by testSimplifyFancy() method

tesSimplifyFancy9()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “* 1 + a b = + a b” (consider whole right or left subtree multiplying with 1).
Inputs:		String "* 1 + a b" to build tree using prefix2tree()
Expected Output:  Tree  "+ a b" returned by testSimplifyFancy() method

tesSimplifyFancy10()
Description:
Purpose of this test is to verify the functionality of testSimplifyFancy() rule “- - a b - a b = 0” (left subtree minus right subtree).
Inputs:		String "- - a b - a b" to build tree using prefix2tree()
Expected Output:  Tree  "0" returned by testSimplifyFancy() method

METHODS ANALYSIS

tree2Prefix(LinkedBinaryTree<String> tree) throws IllegalArgumentException
•	This method converts tree to prefix notation and throws IllegalArgumentException if non-valid or non-arithmetic expression tree provided, this statement runs in O(n) as isArithmaticExpression takes O(n)
•	It uses the private recursive tree2Prefix method which required tree and a node as parameters to convert left and right subtrees of given node (root) which runs in O(n)
•	Total running time for this method is O(n) + O(n) = O(n)
Private recursive tree2prefix(LinkedBinaryTree<String> tree, Position<String> node) running time
•	If tree has no right and left children return the root element runs in O(1) time
•	Otherwise build and return tree with recursive calls to left and right subtrees, each recursive call is T(n/2) and for left and right, it is 2T(n/2)
•	So total time of this helper method would be 2T(n/2) + O(1) which is O(n)

tree2Infix(LinkedBinaryTree<String> tree) throws IllegalArgumentException
•	This method converts tree to infix notation and throws IllegalArgumentException if non-valid or non-arithmetic expression tree provided, this statement runs in O(n) as isArithmaticExpression runs in O(n)
•	It uses the private recursive tree2Infix helper method which required tree and a node as parameters to convert left and right subtrees of given node (root) which runs in O(n)
•	Total running time for this method is O(n) + O(n) = O(n)
Private recursive tree2infix(LinkedBinaryTree<String> tree, Position<String> node) running time
•	If tree has no right and left children return the root element runs in O(1) time
•	Otherwise build and return tree with recursive calls to left and right subtrees, each recursive call is T(n/2) and for left and right, it is 2T(n/2)
•	So total time of this helper method would be 2T(n/2) + O(1) which is O(n)

simplify(LinkedBinaryTree<String> tree) throws IllegalArgumentException
•	This method simplifies the arithmetic expression in subtree of tree and result as node and throws IllegalArgumentException if non-valid or non-arithmetic expression tree provided, this statement runs in O(n) as isArithmaticExpression runs in O(n)
•	It uses the private recursive simplify helper method which required tree and a node as parameters to simplify left and right subtrees of given node (root) and runs in O(n) as briefed below.
•	Total running time for this method is O(n) + O(n) = O(n)
Private recursive simplify(LinkedBinaryTree<String> tree, Position<String> node) running time
•	If root is internal node of tree then checking if root’s element is operator or not by calling isOperator(root.getElement) method takes O(1)
•	If that is operator then calling simplify recursively for left and right subtrees takes O(n) as one recursive call will be T(n/2) and two recursive calls will be 2T(n/2)
•	So total time of this helper method would be 2T(n/2) + O(1) which is O(n)

simplifyFancy(LinkedBinaryTree<String> tree) throws IllegalArgumentException
•	This method simplifies the subtrees of given tree and add simplified result as node if it can be simplified, otherwise it doesn’t modify the subtree if it cannot be simplified, this throws IllegalArgumentException if non-valid or non-arithmetic expression tree provided, this statement runs in O(n) as isArithmaticExpression runs in O(n)
•	It uses the private recursive simplifyFancy helper method which required tree and a node as parameters to simplify left and right subtrees of given node (root) and runs in O(n log n) if called with subtraction operator and O(n) if called without subtraction operator as briefed below.
•	Total running time for this method is O(n) + O(n log n) = O(n log n)
Private recursive simplifyFancy(LinkedBinaryTree<String> tree, Position<String> node) running time WITHOUT SUBTRACTION OPERATOR
•	If root is internal node of tree then checking if root’s element is operator or not by calling isOperator(root.getElement) method takes O(1)
•	Since we have rules without “-” operator and we don’t need to check if two trees are equal or not, so every rule requires O(1)
•	Then calling simplifyFancy recursively for left and right subtrees takes O(n) as one recursive call will be T(n/2) and two recursive calls will be 2T(n/2)
•	So total time of this helper method would be 2T(n/2) + O(1) which is O(n)
Private recursive simplifyFancy(LinkedBinaryTree<String> tree, Position<String> node) running time WITH SUBTRACTION OPERATOR
•	If root is internal node of tree then checking if root’s element is operator or not by calling isOperator(root.getElement) method takes O(1)
•	Since we have rules which requires to compare two subtrees after applying subtraction and equals method runs in O(n)
•	Then calling simplifyFancy recursively for left and right subtrees takes O(n) as one recursive call will be T(n/2) and two recursive calls will be 2T(n/2)
•	So total time of this helper method would be 2T(n/2) + O(n) which is O(n log n)

subtitute(LinkedBinaryTree<String> tree, String variable, int value) throws IllegalArgumentException
•	This method subtitutes the given variable with given integer if that variable exists in tree otherwise it doesn’t modify other variable, this throws IllegalArgumentException if non-valid tree or null variable provided, this statement runs in O(n) as isArithmaticExpression runs in O(n)
•	It uses the private recursive subtitute helper method which required tree, variable, value and node as parameters to subtitute variables’ values in left and right subtrees of given node (root) and runs in O(n) as briefed below.
•	Total running time for this method is O(n) + O(n) = O(n)
Private recursive subtitute(LinkedBinaryTree<String> tree, String variable, int value, Position<String> node)
•	If root is internal node of tree then we call substitute recursively for left and right subtrees which runs in 2T(n/2)
•	Otherwise we check if given node is not null and its element is equal to given variable then we replace node with given value which runs in O(1). This is our base case.
•	So total time of this helper method would be 2T(n/2) + O(1) which is O(n)

subtitute(LinkedBinaryTree<String> tree, HashMap<String, Integer> map) throws IllegalArgumentException
•	This method subtitutes the variables with integer values in given hash map if these variables exist in tree otherwise it doesn’t modify other variable, this throws llegalArgumentException if non-valid tree or null map provided, this statement runs in O(n) as isArithmaticExpression runs in O(n)
•	It uses the private recursive subtitute helper method which requires tree, hasmap of variable and value and node as parameters to subtitute variables’ values in left and right subtrees of given node (root) and runs in O(n) as briefed below.
•	Total running time for this method is O(n) + O(n) = O(n)
Private recursive subtitute(LinkedBinaryTree<String> tree, String variable, int value, Position<String> node)
•	If root is internal node of tree then we call substitute recursively for left and right subtrees which runs in 2T(n/2)
•	Otherwise we check if given node is not null and its element is equal to given hasmap’s key by calling hashmap’s containsKey method, if we find null value agains found key then we don’t replace it with variable and throw exception, and if we find a non-null value against the key then we replace tree’s variable with hashmap’s value. This if condition runs in O(1)
•	So total time of this helper method would be 2T(n/2) + O(1) which is O(n)

isArithmetic(LinkedBinaryTree<String> tree) throws llegalArgumentException
•	This method returns true if given tree can be converted to valid arithmetic expression otherwise false and throws llegalArgumentException if given tree is empty or null, this statement runs in O(1).
•	It uses the private recursive isArithmetic helper method which requires tree and node as parameters to check if tree is an arithmetic function or not which runs in O(n) as briefed below.
•	Total running time for this method is O(1) + O(n) = O(n)
Private recursive isArithmetic(LinkedBinaryTree<String> tree, Position<String> node)
•	If root is internal node of given tree then we check if root is operator or not if not then we return false, this condition runs in O(1)
•	If root is internal and operator then we check it’s left and right operands for null, if any of them is null then we return false, O(1)
•	Otherwise we make recursive call to this method for left and right subtrees or nodes and save Boolean result in variable by applying AND condition on both recursive outputs and return result. Recursive call to one side is T(n/2) and for both left and right sides is 2T(n/2)
•	If the given node (root) is not internal then we check node for operator if it is operator then we return false O(1)
•	Otherwise we return true O(1)
•	Total running time for this method is O(1) + O(1) + 2T(n/2) + O(1) + O(1) = 2T(n/2) + O(1) = O(n)

Suggested Methods

String evaluateEquation(LinkedBinaryTree<String> tree):
Description:
There could be another advanced version of simplifyFancy function which could solve any algebraic expression, instead of just taking care of 8 rules.

Functionality:
For example if a tree has multiple like terms and unlike terms with different operators, this function would return the final simplified solution of algebraic equation by applying algebraic rules (e.g. only like terms can be added or subtracted, unlike terms can be multiplied etc.).

Usage:
This could be useful to solve complex and nested algebraic equations.

String equationType(LinkedBinaryTree<String> tree):
Description:
There could be isPolynomial function which takes a tree as input and performs operations on its nodes to evaluate and test that if the equation obtained from tree nodes is a Polynomial equation or not.

Functionality:
For example if a tree consists of different variables and values and we call simplify, simplifyFancy or evualteEquation function and want to know what is the resultant equation type.

Usage:
This method could be very useful as it would use evaluateEquation method and perform complex calculations to return the resultant equation type, either equation is (Linear, Radical, Quadratic etc). 

Position<String> division(Position<String> node1, Position<String> node2) throws IllegalArgumentException:
Description:
As existing solution misses the division operator, we can add another method division just to perform division operation on tree nodes.

Funcitonality:
Method will take node 1 and node 2 as inputs and would test the parameters validity, 
their elements should be integers or doubles
second node’s element shouldn’t be 0
if above conditions met then it would perform node1.getElement() / node2.getElement() operation, converts it to tree Position<String> element and return it.

Usage:
This would be useful to perform division operations.
Position<String> logrithm(Position<String> node1, int base) throws IllegalArgumentException:
Description:
As we are computer scientists and we are interested in logs always, we can add another method logrithm to calculate log of given node in given base.

Functionality:
Method will take node and base as inputs and would test the parameters validity, 
their elements should be integers or doubles
if above conditions met then it would calculate node1.getElement() logarithm in given base, converts it to tree Position<String> element and return it.

Usage:
This would be useful to calculate log in different bases.

LinkedBinaryTree<String> tree history(LinkedBinaryTree<String> tree) throws IllegalArgumentException:
Description:
There could be a method history to view history of operations performed on a given tree.

Functionality:
We can build history of operations performed on a given tree, operations can be categorized into different categories, for example, “deleting nodes operations, adding nodes operation, modifying variables operations etc”. 
These operations would be the internal nodes of tree and nodes on which operations were performed would be external nodes.

Usage:
This would be useful to view operations performed on nodes.
