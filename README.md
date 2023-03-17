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


public static List<Book> OrderList(List<Book> bookList, List<int> orderedIds)
	{
		
		Dictionary<int, int> idMap = new Dictionary<int, int>();
		int n = orderedIds.Count;
		for(int i=0; i<n;i++){
			
			idMap.Add(orderedIds[i], i);
		}
		int m = bookList.Count;
		for(int i=0; i<m; i++){
			int currentBookId = bookList[i].Id;
			if(!idMap.ContainsKey(currentBookId)){
				idMap.Add(bookList[i].Id, n);
				n = n+1;
			}
				
		}
		
		bookList.Sort((x,y) => (idMap[x.Id] - idMap[y.Id]));
		
		return bookList;
	}


```
**4. What’s the computational complexity of your solution? (approximately)**
```
Computational complexity would be O(n*log(n)), where n is number of books, since that is the sorting complexity. All used dictionary operations are O(1) amortised.
Since filling the dictionary is O(m) for the first loop and O(n) for the second one, it doesn't affect overall complexity of O(n*log(n)). 
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
The search is not case sensitive. The response could contain duplicates. 
```
**2. What’s the computational complexity of the above solution? (approximately)**
```
The computational complexity is O(m*n) where m is number of search terms and n is number of books.
```
**3. Can you refactor the above function in order to satisfy all requirements without changing the input and output structure?**
```csharp
// Your C# refactored code goes here

public static List<Book> SearchList(List<Book> bookList, List<string> searchTerms)
	{
		List<Book> results = new List<Book>();
		
		foreach(Book book in bookList)
		{
			foreach(string term in searchTerms)
			{
				if(book.Title.ToLower().Contains(term) || book.Description.ToLower().Contains(term))
				{
					results.Add(book);
					continue;
				}
			}
		}
	
		return results;
	}
```
**4. What’s the computational complexity of your solution? (approximately)**
```
The computational complexity would be O(n*m) where n is the number of books and m the number of terms.
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
	public static List<Book> TopRankList(List<Book> bookList, int rankListLength)
	{
	// Add code to find top ranked items
		PriorityQueue<Book, decimal> q = new PriorityQueue<Book, decimal>();
		int lowest = bookList[0].Upvotes - bookList[0].Downvotes;
		int highest = lowest;
		foreach(var book in bookList){
			lowest = lowest > (book.Upvotes - book.Downvotes) ? (book.Upvotes - book.Downvotes) : lowest;
			highest = highest < (book.Upvotes - book.Downvotes) ? (book.Upvotes - book.Downvotes) : highest;
		}
		
		int difference = highest - lowest;
		
		foreach(var book in bookList)
		{
			var udPoints = (book.Upvotes - book.Downvotes)*1.0/difference * 10.0;
			q.Enqueue(book, -(book.PublisherStars + (decimal)udPoints));		
		}
		List<Book> res = new List<Book>();
		for(int i=0;i< rankListLength; i++){
			res.Add(q.Dequeue());
		}
		
		return res;
	}
```
**2. What’s the computational complexity of your solution? (approximately)**
```
Computational complexity is O(n*log(n)), where n is number of books.
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
