# My Learning Journey

# 📘 C++ Variables - Lesson 01

**Date Reviewed:** February 23, 2026

**Last Updated:** February 23, 2026

**Difficulty:** ⭐☆☆☆☆ (Easy)

**Status:** ✅ Completed / 🟡 In Progress / ❌ Not Started

---

## 📌 What I Review Today

Sa C++, ang **variables** ay parang lalagyan ng data sa memory. Kailangan nating sabihin kung anong uri ng data ang ilalagay bago natin ito gamitin. Huwag iwan na walang laman ang variables.

---

## 💻 Code Snippets

### Basic Variable Declaration

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
    cout << "Age: " << age << endl;
    cout << "Grade: " << grade << endl;

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

## 🔥 Problems I Encountered before

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

## 💡 Key Takeaways

1. **Always initialize variables** - Huwag iwan na walang laman ang variables until you use them.
2. **Choose the right data type** - `int` para sa whole numbers, `double` para sa decimals
3. **Remember `cin.ignore()`** - Pag may `cin` bago `getline()`
4. **Strings are objects** - Hindi primitive data type ang `string`

---

## 📚 References

- [LearnCpp.com - Variables](https://www.learncpp.com/cpp-tutorial/variables/)
- [Cplusplus.com - Data Types](http://www.cplusplus.com/doc/tutorial/variables/)
- [My Student Management System Project](https://github.com/daun-codes/CPP-Activities-Portfolio/tree/main/Activity-2-Addition-Calculator) ← Check my example program here

---

## 📝 Personal Notes

```cpp
// Reminders:
// Ang "int" ay para sa edad, score, attempts or anything that you can calculate and expect a whole number
// Ang "double" para sa grades (1.5, 1.75) or you can also use this for sales prices or anything that you can calculate and expect a decimal
// Ang "string" para sa pangalan o any other text that you want to display.
```

> "Ang variables ay parang mga kahon - may label at may laman."

---

## 🔗 Related Lessons

- [Next: Data Types](./02-data-types.md)
- [Back to C++ Home](./README.md)

---

## ✅ Practice Exercises

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

## 📊 Progress Tracker

| Concept              | Status | Date   |
| -------------------- | ------ | ------ |
| Variable declaration | ✅     | Feb 23 |
| Data types           | ❌     | -      |
| Input/Output         | ❌     | -      |
| Constants            | ❌     | -      |

---

## 🎯 Goals for Next Time

- [ ] Mag-practice ng `const` variables
- [ ] Gumawa ng program gamit ang `float` vs `double`
- [ ] Mag-upload ng notes sa GitHub
