# CODE EVALUATION & REFACTORING TASK [DEV TASK 2022C]
**Evaluate and Refactor C# snippets**

[![Kroon](kroon.svg)](https://kroonstudio.com/)

> Teodora Vasić

# A) AN ORDERING FUNCTION:
### Questions:
**1. Which requirements are not satisfied in the above solution?**
```
Requirement number 4 is not satisfied. If some books are in the bookList but their id is not in the orderedIds, this
book isn't contained in the result list. The method isn't optimised, so it can't work fast enough for large input.
```
**2. What’s the computational complexity of the above solution? (approximately)**
```
Computational complexity is O(n*m) where n is number of ids in orderIds and m is number of books in bookList.
```
**3. Can you refactor the above function in order to satisfy all requirements without changing the input and output structure?**
```csharp
// Your C# refactored code goes here
```
**4. What’s the computational complexity of your solution? (approximately)**
```
Your answer...
```
**5. Can you write a unit test for the above function?**
```csharp
// Your C# unit test goes here
```

---

# B) A SEARCH FUNCTION:
### Questions:
**1. Which requirements are not satisfied in the above solution?**
```
The search is not case sensitive. The response could contain duplicates. The method is not optimised.
```
**2. What’s the computational complexity of the above solution? (approximately)**
```
The computational complexity is O(m*n) where m is number of search terms and n is number of books.
```
**3. Can you refactor the above function in order to satisfy all requirements without changing the input and output structure?**
```csharp
// Your C# refactored code goes here
```
**4. What’s the computational complexity of your solution? (approximately)**
```
Your answer...
```
**5. Can you write a unit test for the above function?**
```csharp
// Your C# unit tests go here
```

---

# C) A RANKING FUNCTION:
### Questions:

**1. Can you write the function as described in the above requirements?**
```csharp
// Your C# code goes here
```
**2. What’s the computational complexity of your solution? (approximately)**
```
Your answer...
```
**3. Can you write a unit tests for your function?**
```csharp
// Your C# unit test goes here.
```

---

# GENERAL NOTES AND EXPLANATIONS:
```
Put here any general notes regarding your solution...
```

---

# IMPRESSIONS:
```
Feedback is very important for us so, feel free to add some words regarding the task... Thank you! :)
```
