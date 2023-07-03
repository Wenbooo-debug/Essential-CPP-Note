
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

    


