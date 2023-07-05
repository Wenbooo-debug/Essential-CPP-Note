
``` C++
#include <iostream> 
#include <string>
using namespace std;

int main()
{
  string user_name;
  cout<<"Please enter your first name:";
  cin>> user_name;
  cout<<'\n'
    <<"Hello, "
    <<user_name
    <<"... and goodbye! \n";
  return 0;
}
```
# 1.4 Conditional Statements & Loop Statements
## Conditional Statements
a. if - else  
b. switch
```C++
switch (num_tries)
{
  case 1:
    cout << " num_tries == 1 output /n"
    break;
  case 2:
    cout << " num_tries == 2 output /n"
    break;
  case 3:
    cout << " num_tries == 3 output /n"
    break;
  default:
    cout << " neither 1 2 3 output /n"
    break;
}
```
**switch** keyword expression must evaluate to an **integral value** (integral type: int, char, bool)  
## Loop Statements
A loop can be terminated within the body of its code sequence by the execution of a **break** statement 
```C++
int max_tries = 3;
int tries_cnt = 0;
while (tries_cnt<max_tries)
{
  //read user guess
  if(user_guess == next_elem)
    break; // terminate loop


  tries_cnt++;
  //more statements
}
```
Current iteration of the loop can be short-circuit by the execution of **continue**(the *continue* statement cause the current loop iteration to terminate)
```C++
string word;
const int min_size = 4;
while(cin>>word){
  if(word.size()<min_size)
    //terminate this iteration
    continue;
    //reach here only if the word is greater than or equal min_size
    process_text(word);
}
```
# 1.5 Arrrays & Vectors
## Built-in array
To define a built-in array, need specify **type**,**name**,**dimension**.  
The **dimension** must be a **constant expression** which doesn't require run-time evaluation.
```C++
const int seq_size = 18;
int pell_seq [seq_size];
//type name [dimension]
```
## Object of the standard library vector class
To define a vector class object, must first include the vector header file.  
Indicate the type of its element in brackets following the name of the class.  
The dimension is placed in parentheses which doesn't need to be a constant expression.  
```C++
#include <vector>
vector<int> pell_seq(seq_size);
```
## Initialization
Built-in array can specify an initialization list.
```C++
int elem_seq [seq_size]={
  1,2,3,3,4,7,2,5,12,
  3,6,10,4,9,16,5,12,22};
```
The vector class does not support an explicit initialization list.
```C++
vector<int> elem_seq(seq_size);
elem_seq[0]=1;
elem_seq[1]=2;
//...
elem_seq[17]=22;
```
(One alternative is to use built-in array to initialize the vector)  
## Difference
vector knows its size.
```C++
elem_seq.size();
//returns the number of elements contained within the vector elem_seq
```
# 1.6 Pointers
A pointer holds the address of an object of a particular type.  
```C++
int ival = 1024;
int *pi; //pi is a pointer to can object of type int
ival; //evaluates to the value of ival
&ival; //evaluates to the address of ival
int *pi = &ival; //initialize pi to ival's address
//dereference pi to access the object it addresses
if(*pi != 1024) //read
  *pi = 1024;  //write
pi; //evaluates to the address held by pi
*pi; //evaluates to the value of the object addressed by pi
```
A pointer that addresses no object had an address value of 0 (null pointer)  
```C++
//initialize each pointer to address no object
int *pi = 0;
double *pd = 0;
string *ps = 0;
//to guard against dereferencing a null pointer,
if(pi&&*pi!=1024)
  *pi = 1024;
```
Pointer form: type_of_object_pointed_to * name_of_pointer_object  
Ex. vector<int> *pv = 0;  
```C++
const int seq_cnt = 6;
//an array of seq_cnt pointers to objects of type vector<int>
vector<int> *seq_addrs[seq_cnt] = {
  &fibonacci,&lucas,&pell,
  &triangular,&square,&pentagonal};
```
Poiner to a class object might be slightly special since a class object has an associated set of operations.
```C++
fibonacci.empty(); //use '.' select class operation
pv->empty();       //pointer select class operation
pv && pv->empty(); //check pv's address is non zero before invoke empty()
```
# 1.7 Writing and Reading Files
To read and write to a file, we must include the **fstream** header file
```C++
#include <fstream>
```
## To open a file for output
Define an ofstream (an output file stream) class object, passing it the name of the file to open
```C++
ofstream outfile ("seq_data.txt");
//if file doesn't exist, file is created and opened for output
//if exist, it is opened for output and any  existing data in the file is discarded
if(!outfile)
  //open failed for some reason
  cerr<< "unable to save session data!\n";
else
  //outfile is open, let's write the data
  outfile<<usr_name <<' '
    <<num_tries <<' '
    <<num_right << endl;
```
## To open a file for input
Define an ifstream (an input file stream) class object, passing it the name of the file to open
```C++
ifstream infile ("seq_data.txt");
int num_tries = 0;
int num_cor = 0;
if(!infile)
{
  //open failed for some reason
  //persume it is a new user
}
else
{
  //read each line of the input file see if user has played before
  string name;
  int nt;
  int nc;
  while(infile>>name) //infile>>name read the next line of the file until the end of file is reached
  {
    infile>>nt>>nc; //read in previous record
    if(name == user_name)
      {
        cout<<"Welcome back,"<<usr_name
            <<"\nYour current score is "<<nc
            <<"out of "<<nt<<"\nGood Luck!\n";
        num_tries = nt;
        num_cor = nc;
      }
  }
}
```
## To both read from and wirte to the same file
```C++
fstream iofile("seq_data.txt");
if(!iofile)
  //open filed for some reason
else
{
  //reposition to front of file to begin reading
  iofile.seekg(0);
  //
}



















    


