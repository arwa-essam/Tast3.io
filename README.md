# Tast3.io

                                                                "constant"
                                                                   
Constant Variables:

There are a certain set of rules for the declaration and initialization of the constant variables:
The const variable cannot be left un-initialized at the time of the assignment.
It cannot be assigned value anywhere in the program.
Explicit value needed to be provided to the constant variable at the time of declaration of the constant variable.

Example:

>#include <iostream>
using namespace std;
int main()
{
    // const int x;  Compile Time error
    // x = 9;   Compile Time  error
    const int y = 10;
    cout << y;
    return 0;
}
  
  
Const Keyword With Pointer Variables:
 Pointers can be declared with a const keyword. So, there are three possible ways to use a const keyword with a pointer, which are as follows:
When the pointer variable point to a const value:
  
Example:
  
>#include <iostream>
using namespace std; 
int main()
{
    int x{ 10 };
    char y{ 'M' };
    const int* i = &x;
    const char* j = &y;
    // Value of x and y can be altered,
    // they are not constant variables
    x = 9;
    y = 'A';
    // Change of constant values because,
    // i and j are pointing to const-int
    // & const-char type value
    // *i = 6;
    // *j = 7;
    cout << *i << " " << *j;
}
  
When the const pointer variable point to the value:
  
Example:
  
>#include <iostream>
using namespace std;
int main()
{
    // x and z non-const var
    int x = 5;
    int z = 6;
    // y and p non-const var
    char y = 'A';
    char p = 'C';
    // const pointer(i) pointing
    // to the var x's location
    int* const i = &x;
    // const pointer(j) pointing
    // to the var y's location
    char* const j = &y;
    // The values that is stored at the memory location can modified
    // even if we modify it through the pointer itself
    // No CTE error
    *i = 10;
    *j = 'D';
    // CTE because pointer variable
    // is const type so the address
    // pointed by the pointer variables
    // can't be changed
    // *i = &z;
    // *j = &p;
    cout << *i << " and " << *j
        << endl;
    cout << i << " and " << j;
    return 0;
}
  
When const pointer pointing to a const variable:
  
Example:
  
>#include <iostream>
using namespace std;
int main()
{
    int x{ 9 };
    const int* const i = &x;
    // *i=10;  
    // The above statement will give CTE
    // Once Ptr(*i) value is
    // assigned, later it can't
    // be modified(Error)
    char y{ 'A' };
    const char* const j = &y;
    // *j='B';
    // The above statement will give CTE
    // Once Ptr(*j) value is
    // assigned, later it can't
    // be modified(Error)
    cout << *i << " and " << *j;
    return 0;
}
  
Pass const-argument value to a non-const parameter of a function cause error: Passing const argument value to a non-const parameter of a function isn’t valid it gives you a compile-time error.
  
Example:
  
>#include <iostream>
using namespace std;
int foo(int* y)
{
    return *y;
}
int main()
{
    int z = 8;
    const int* x = &z;
    cout << foo(x);
    return 0;
}

Constant Methods:
  
When a function is declared as const, it can be called on any type of object, const object as well as non-const objects.
Whenever an object is declared as const, it needs to be initialized at the time of declaration. However, the object initialization while declaring is possible only with the help of constructors.
  
There are two ways of a constant function declaration:
  
Ordinary const-function Declaration:
  
>const void foo(){
   //void foo() const Not valid
}                  
int main(){
   foo(x);
}  
  
A const member function of the class:
  
>class{
   void foo() const {
       //.....
   }
}
  
Example:
  
>#include <iostream>
using namespace std;
 class Test {
    int value;
public:
    Test(int v = 0)
    {
        value = v;
    }
    // We get compiler error if we
    // add a line like "value = 100;"
    // in this function.
    int getValue() const
    {
        return value;
    }
    // a nonconst function trying to modify value
    void setValue(int val) {
        value = val;
    }
};
int main(){
    Test t(20);
    // non-const object invoking const function, no error
    cout << t.getValue() << endl;
    // const object
      const Test t_const(10);
    // const object invoking const function, no error
    cout << t_const.getValue() << endl;
    // const object invoking non-const function, CTE
    // t_const.setValue(15);
    // non-const object invoking non-const function, no error
    t.setValue(12);
    cout << t.getValue() << endl:
    return 0;
}
  
Constant Function Parameters And Return Type:
  
A function() parameters and return type of function() can be declared as constant. Constant values cannot be changed as any such attempt will generate a compile-time error.
  
Example:
  
>#include <iostream>
using namespace std;
void foo(const int y)
{
    // y = 6; const value
    // can't be change
    cout << y;
}
void foo1(int y)
{
    // Non-const value can be change
    y = 5;
    cout << '\n'
         << y;
}
int main()
{
    int x = 9;
    const int z = 10;
    foo(z);
    foo1(x);
    return 0;
}
  
For const return type: 
  
The return type of the function() is const and so it returns a const integer value to us.
  
Example:
  
>#include <iostream>
using namespace std;
const int foo(int y)
{
    y--;
    return y;
}
int main()
{
    int x = 9;
    const int z = 10;
    cout << foo(x) << '\n'
         << foo(z);
    return 0;
}
  
For const return type and const parameter:
  
Here, both return type and parameter of the function are of const types.
  
Exapmle:
  
>#include <iostream>
using namespace std;
const int foo(const int y)
{
    // y = 9; it'll give CTE error as
    // y is const var its value can't
    // be change
    return y;
}
int main()
{
    int x = 9;
    const int z = 10;
    cout << foo(x) << '\n'
         << foo(z);
    return 0;
}
  
                                                             " &"
  
The unary address-of operator (&) returns the address of (that is, a pointer to) its operand. The operand of the address-of operator can be a function designator. Or, it can be an lvalue that refers to an object that's not a bit field.

The address-of operator can only be applied to certain lvalue expressions: either to variables of fundamental, structure, class, or union types, or to subscripted array references. In these expressions, a constant expression (one that doesn't include the address-of operator) can be added to or subtracted from the address-of expression.

When applied to functions or lvalues, the result of the expression is a pointer type (an rvalue) derived from the type of the operand. For example, if the operand is of type char, the result of the expression is of type pointer to char. The address-of operator, applied to const or volatile objects, evaluates to const type * or volatile type *, where type is the type of the original object.
  
Example:
  
Address of a reference type
Applying the address-of operator to a reference type gives the same result as applying the operator to the object to which the reference is bound. 
  
>#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
  
Example:
  
Function address as parameter
The following example uses the address-of operator to pass a pointer argument to a function:
  
>#include <iostream>
using namespace std;
// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}
int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}



