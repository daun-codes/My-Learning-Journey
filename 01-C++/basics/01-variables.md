# C++ Variables - Lesson 01

**Date Reviewed:** February 23, 2026

**Last Updated:** February 23, 2026

**Difficulty:** ⭐☆☆☆☆ (Easy)

**Status:** ✅ Completed

---

## What I Review Today

In this lesson, we will learn about variables in C++ and how to declare and use them. We will also learn about the best practices in getting user input and how to use the getline() function to get user input with spaces.

Variables is like a box that holds a value. We can use variables to store data that we want to use in our program. We can also use variables to store data that we get from the user.

---

## Code Snippets

### Basic Variable Declaration

Let's start with a simple variable declaration. We'll use `int` for whole numbers, `double` for decimal numbers, `string` for text, `char` for single letters, and `bool` for true/false values. This is hardcoded values and does not require input from the user.

```cpp
#include <iostream>     // Ginagamit natin ang libary ng iostream to print out values sa console using cout.
using namespace std;    // We used this to avoid writing 'std::cout' all the time. Bale para siyang shortcut. But it is up to you if you prefer to use it or not.

int main() {
    // Integer - whole numbers
    int age = 20;

    // Double - decimal numbers
    double grade = 1.5;
    float pi = 3.14f;  // 'f' suffix for float

    // String - text
    string name = "Juan Dela Cruz";

    // Character - single letter
    char initial = 'J';

    // Boolean - true/false
    bool isStudent = true;

    // I-print ang values
    cout << "Name: " << name << endl;
    cout << "Initial: " << initial << endl;
    cout << "Age: " << age << endl;
    cout << "Grade: " << grade << endl;
    cout << "Pi: " << pi << endl;

    return 0;
}
```

**Output:**

```
Name: Juan Dela Cruz
Age: 20
Grade: 1.5
```

---

### Basic Variable with User Input

Earlier, we had learn that we can use cout to print out values to the console. Now, let's see how we can get user input and store it in a variable.

```cpp
#include <iostream>
using namespace std;

int main() {
    int age;
    string firstName; // Here we declared a string variable but without any value

    /*

    Note: You can declare a variable without assigning a value but make sure to initialize it later before using it.

    */

    cout << "Enter your first name: ";
    cin >> firstName;
    cout << "Enter your age: ";
    cin >> age;


    // I-print ang values
    cout << "First Name: " << firstName << endl;
    cout << "Age: " << age << endl;

    return 0;
}
```

**Output:**

```
Enter your first name: Juan
Enter your age: 20
First Name: Juan
Age: 20
```

### Initializing Variables and Getting User Input with spaces in between

Now that we know how we can get a user input but what if we want to get a user input with spaces in between such as for example 'Juan dela Cruz'? We can use the getline() function to get the user input with spaces.

```cpp
#include <iostream>
using namespace std;

int main() {
    int age;
    string name;

    cout << "Enter your name: ";
    getline(cin, name);         // We used getline() to get the user input with spaces
    cout << "Enter your age: ";
    cin >> age;

    // I-print ang values
    cout << "Name: " << name << endl;
    cout << "Age: " << age << endl;

    return 0;
}
```

**Output:**

```
Enter your name: Juan Dela Cruz
Enter your age: 20
Name: Juan Dela Cruz
Age: 20
```

---

## Problems I Encountered before

### Problem 1: `cin` vs `getline()`

**Situation:** Nagki-click agad ang program ko, hindi naghihintay ng input even though may cin tayo na ginawa. Ito ay nagiging problema sa `getline()`.

**Code:**

```cpp
// ❌ PROBLEM
int age;
string name;

cin >> age;        // May natitirang newline sa buffer
getline(cin, name); // Hindi gagana!
```

**Solution:**

```cpp
// ✅ SOLUTION
cin >> age;
cin.ignore();      // I-clear ang newline
getline(cin, name);
```

**Explanation:** Pag cinagamit ang `cin >>`, nag-iiwan ito ng `\n` sa input buffer. Kailangan itong i-clear bago gumamit ng `getline()`.

---

## Key Takeaways

1. **Always initialize variables** - Huwag iwan na walang laman ang variables until you use them.
2. **Choose the right data type** - `int` para sa whole numbers, `double` para sa decimals
3. **Remember `cin.ignore()`** - Pag may `cin` bago `getline()`
4. **Strings are objects** - Hindi primitive data type ang `string`

---

## References

- [LearnCpp.com - Variables](https://www.learncpp.com/cpp-tutorial/variables/)
- [Cplusplus.com - Data Types](http://www.cplusplus.com/doc/tutorial/variables/)
- [My Student Management System Project](https://github.com/daun-codes/CPP-Activities-Portfolio/tree/main/Activity-2-Addition-Calculator) ← Check my example program here

---

## Personal Notes

```cpp
// Reminders:
// Ang "int" ay para sa edad, score, attempts or anything that you can calculate and expect a whole number
// Ang "double" para sa grades (1.5, 1.75) or you can also use this for sales prices or anything that you can calculate and expect a decimal
// Ang "string" para sa pangalan o any other text that you want to display.
```

> "Ang variables ay parang mga kahon - may label at may laman."

---

## Related Lessons

- [Next: Data Types](./02-data-types.md)
- [Back to C++ Home](./README.md)

---

## Practice Exercises

1. **Gumawa ng program** na may variables para sa:
   - Pangalan (string)
   - Edad (int)
   - Grade (double)
   - Section (char)

2. **Calculate future age**
   ```cpp
   int currentAge = 20;
   int futureAge = currentAge + 5;
   cout << "In 5 years, you will be " << futureAge;
   ```

---

## Progress Tracker

| Concept              | Status | Date   |
| -------------------- | ------ | ------ |
| Variable declaration | ✅     | Feb 23 |
| Data types           | ❌     | -      |
| Input/Output         | ❌     | -      |
| Constants            | ❌     | -      |

---

## Goals for Next Time

- [ ] Mag-practice ng `const` variables
- [ ] Gumawa ng program gamit ang `float` vs `double`
- [ ] Mag-upload ng notes sa GitHub
