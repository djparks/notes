# Kata for Practicing

PERSONAL:
docker retag:

<https://www.nurkiewicz.com/2018/09/brute-forcing-seemingly-simple-number.html>

<https://blog.frankel.ch/sieve-eratosthenes/>

<https://duckduckgo.com/?q=programming+dojo&atb=v138-7__&ia=web>

<https://medium.freecodecamp.org/how-to-think-like-a-programmer-lessons-in-problem-solving-d1d8bf1de7d2>

<https://coderbyte.com/>

<https://lambdaschool.com/blog/>

<https://www.globalsoftwaresupport.com/most-common-programming-interview-questions-in-2019/>

Factorial
Remove Duplicates
Char: "hello".charAt(0);
Fibonacci
Prime
Numeric Palindrome: palindrome %10; reverse*10+remainder...
Reverse String
Arrays
to Map
sort
printing

JS Kata — <https://jsbin.com/romun/edit?js,console>
var _ = R;

/*****************************************
      C U R R Y I N G  E X A M P L E
******************************************/

// We've got a nice multiply function.
// It takes two arguments.

console.log( _.multiply(3, 4) );

// But it has been secretly curried already
// so we can feed it fewer arguments and it
// will return a new function.
//
// How about making a function to double a
// value? Done.
var double = _.multiply(2);

console.log( double(13) );

/*****************************************
               Y O U R  T U R N
******************************************/

// _.split pulls a string apart around a
// given value
console.log( _.split('i', 'mississippi') );

// -- Challenge 1 ------------------------
// Make a function called "words" which
// returns a list of words in a string.
// Use only the split function and
// currying.

console.log("Testing challenge 1...");

var words = undefined; // change this
assertEqualArrays(
  ['one', 'two', 'three'],
  words('one two three')
);
console.log("passed");

// -- Challenge 2 ------------------------
// Create a function to triple every
// number in a list using only
// _.multiply and _.map.

console.log("Testing challenge 2...");

var tripleList = undefined;
assertEqualArrays([3,6,9], tripleList([1,2,3]));

console.log("passed");

// -- Challenge 3 ------------------------
// Create a function to find the largest
// number in a list. You can use the
// greater(a,b) function which returns the
// greater of its two inputs. You can do
// this with currying and one of the list
// functions _.map, _.filter, or _.reduce.

console.log("Testing challenge 3...");

var greater = function(a,b) {
  return a > b ? a : b;
};

var max = _.indentity;
assertEqual(9, max([1,-3483,9,7,2]));
assertEqual(-1, max([-21,-3483,-2,-1]));

console.log("passed");


console.log("All tests pass.");
/******************************************
        B A C K G R O U N D  C O D E
*******************************************/

function assertEqualArrays(x,y) {
  if(x.length !== y.length) throw("expected "+x+" to equal "+y);
  for(var i in x) {
    if(x[i] !== y[i]) {
      throw("expected "+x+" to equal "+y);
    }
  }
}
function assertEqual(x,y){
  if(x !== y) throw("expected "+x+" to equal "+y);
}
