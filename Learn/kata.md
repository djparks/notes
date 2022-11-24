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

4 CAESAREAN CIPHER -
4.1 1/O Filters
4.1.1 Understanding stream I/0
4.1.2 Writing a simple filter
4.1.3 Working a filter at the command prompt
4.2 On the Front Lines with Caesar
4.2.1 Rotating 13 characters
4.2.2 Devising a more Caesarean cipher
4.3 Deep Into Filter Madness
4.3.1 Building the hex output filter
4.3.2 Creating a NATO filter
4.3.3 Filtering words
4.4 Summary
5 ENCODING AND DECODING V
5.1 The Concept of Plain Text
5.1.1 Understanding ASCII
5.1.2 Exploring the control codes
5.1.3 Generating non-character output
5.1.4 Playing with ASCII conversion tricks
5.2 The Hex Encoder/Decoder
5.2.1 Writing a simple hex encoder/decoder
a 5.2.2 Coding a better hex encoder/decoder
5.2.3 Adding a wee bit of error-checking
5.3 URL Encoding
5.3.1 Knowing all the URL encoding rules
5.3.2 Writing a URL encoder
5.3.3 Creating a URL decoder
6 PASSWORD GENERATORS
6.1 Password Strategies
6.1.1 Avoiding basic and useless passwords
6.1.2 Adding password complexity
6.1.3 Applying the word strategy
6.2 The Complex Password Jumble
6.2.1 Building a silly random password program
6.2.2 Adding conditions to the password program
6.2.3 Improving upon the password
6.3 Words in Passwords
6.3.1 Generating random words, Mad Libs style
6.3.2 Building random word password generator
7 STRING UTILITIES
7.1 Strings in C
7.1.1 Understanding the string
7.1.2 Measuring a string
7.1.3 Reviewing C string functions
7.1.4 Returning versus modifying directly
7.2 String Functions Galore
7.2.1 Changing case
7.2.2 Reversing a string
7.2.3 Trimming a string
7.2.4 Splitting a string
7.2.5 Inserting one string into another
7.2.6 Counting words in a string
7.2.7 Converting tabs to spaces
7.3 A String Library
7.3.1 Writing the library source and header file
7.3.2 Creating a library
7.3.3 Using the string library
7.4 A Kinda OOP Approach
7.4.1 Adding a function to a structure
7.4.2 Creating a string "object"
8 UNICODE AND WIDE CHARACTERS
8.1 Text Representation in Computers
8.1.1 Reviewing early text formats
8.1.2 Evolving into ASCII text and code pages
8.1.3 Diving into Unicode
8.2 Wide Character Programming
8.2.1 Setting the locale
8.2.2 Exploring character types
8.2.3 Generating wide character output
8.2.4 Receiving wide character input
8.2.5 Working with wide characters in files
9 HEX DUMPER
9.1 Bytes and Data
9.1.1 Reviewing storage units and size mayhem
9.1.2 Outputting byte values
9.1.3 Dumping data
9.2 Dump That File!
9.2.1 Reading file data
9.2.2 Fixing uneven output
9.3 Command Line Options
9.3.1 Using the getopt() function
9.3.2 Updating the dumpfile program code
9.3.3 Setting abbreviated output
9.3.4 Activating octal output
10 DIRECTORY TREE
10.1 The File System
10.2 File and Directory Details
10.2.1 Gathering file info
10.2.2 Exploring file type and permissions
10.2.3 Reading a directory
10.3 Subdirectory Exploration
10.3.1 Using directory exploration tools
10.3.2 Diving into a subdirectory
10.3.3 Mining deeper with recursion
10.4 A Directory Tree
10.4.1 Pulling out the directory name
10.4.2 Monitoring directory depth
11 FILE FINDER
11.1 The Great File Hunt
11.2 A File Finder
11.2.1 Coding the Find File utility
11.2.2 Understanding the glob
11.2.3 Using wildcards to find files
11.3 The Duplicate File Finder
11.3.1 Building a file list
11.3.2 Locating the duplicates
12 HOLIDAY DETECTOR
12.1 The Operating System Wants Its Vig
12.1.1 Understanding exit status versus the termination stat
12.1.2 Setting a return value
12.1.3 Interpreting the return value
12.1.4 Using the preset return values
12.2 All About Today
12.2.1 Getting today's date
12.2.2 Obtaining any old date
12.3 Happy Holidays
12.3.1 Reviewing holidays in the US
12.3.2 Discovering holidays in the UK
12.4 Is Today a Holiday?
12.4.1 Reporting regular date holidays
12.4.2 Dealing with irregular holidays
12.4.3 Calculating Easter
12.4.4 Running the date gauntlet
13 CALENDAR
13.1 The Calendar Program
13.2 Good Dates to Know
13.2.1 Creating constants and enumerating dates
13.2.2 Finding the day of the week
13.2.3 Calculating the first day of the month
13.2.4 Identifying leap years
13.2.5 Getting the time zone correct
13.3 Calendar Utilities
13.3.1 Generating a week
13.3.2 Showing a month
13.3.3 Displaying a full year
13.3.4 Putting the full year into a grid
13.4 A Calendar in Color
13.4.1 Understanding terminal colors
13.4.2 Generating a tight-but-colorful calendar
13.4.3 Coloring holidays
14 LOTTO PICKS
14.1 A Tax for Those Who Are Bad at Math
14.1.1 Playing the lottery
14.1.2 Understanding the odds
14.1.3 Programming the odds
14.2 Here Are Your Winning Numbers
14.2.1 Generating random values
14.2.2 Drawing lotto balls
14.2.3 Avoiding repeated numbers, another approach
14.3 Never Tell Me the Odds
14.3.1 Creating the lotto() function
14.3.2 Matching lottery picks
14.3.3 Testing the odds
15 TIC-TAC-TOE
