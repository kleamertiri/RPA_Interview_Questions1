# :hourglass: RPA Interview Questions Part1
### Exercise #1
Your main workflow should ask the user to provide 2 numbers. However, you can not sum those numbers in the main workflow. Show how you can use arguments in this scenario?

:pushpin:**Use of Arguments:**
1. **IN**             Variable => Argument
2. **OUT**            Argument => Variable

### Exercise #2
There is an array which contains names of various objects.

*arrayObjects = {Pen, Mobile, Pencil, Charger, Key}*

The user will be asked for an object and it will be returned the index of that object.

**:pushpin:**
`*StrConv(objectName, VbStrConv.ProperCase)* - converting the first letter of the word in uppercase`
### Exercise  #3
You have been given an excel file which contains names and password expiry date. From the entire excel file you have to notify the user whose password is going to expire in the next 7 days. The dates are in different formats.

:pushpin:
- `*expiryDate = Convert.ToDateTime(row(1))* - converting the dates into DateTime and in the same format`
- `*expiryDate < Now.AddDays(7)* - the condition`

### Exercise #4
Value of the variable A = 1 and B = 2. You are free to choose the variable data type. Create a workflow and display the output A + B = 3 and A + B = 12 in a single run.

**Condition:** Once the variable type is selected, you must not change it to achieve this result.

:pushpin:

![2](https://user-images.githubusercontent.com/105167291/230345952-152a6453-913f-4215-87f1-45adf54ef443.PNG)

### Exercise #5
Consider an array of Integer *numArray = {1, 2, 3, 4, 5}*. How can you print this array?

And, is it possible to add another number 6 to this array? If yes, print and show the output.

:pushpin:

1. `String.Join(", ", numArray)` - to print the elements of an array, using comma as a delimiter
2. Add another number
   - Convert the array into a list `(. toList())` and add another element with **Add to Collection Activity** 
   - `numArray.Concat({6}).ToArray` - to add directly a new element to the array

### Exercise #6
If the array is initialized and you have a fixed size of the array, is it possible to concat another number to the same array?

:pushpin:

`New Int32(1){1 , 2}` - initializing an array with fixed size
*Yes, it is possible because if we concat the new value of the array in the workflow, it takes precedence and the array declared in the Variable tab is not important anymore.*

### Exercise #7
Check if the string contains a word “SUCCESS” or “FAILED” and using Switch Activity, print the status message.

1. The file uploaded successfully
2. The file upload has Failed

:pushpin:

![2](https://user-images.githubusercontent.com/105167291/230347693-4fdfbcac-a3e5-4564-9ab4-945434d58424.PNG)

### Exercise #8
Create ListA and add default values {1 ,2}. `New List(of Int32) from {1,2}`.

Create List B and use Add to Collection Activity to add value 3. Concat ListA and ListB and display the output in ListC.

:pushpin:

- When used **Add to Collection Activity**, to add values to a list, the list should always be initialized `New List(Of Int32)` 
- To merge two lists together, we use `.concat()` method and `.toList()`

### Exercise #9
Create a Dictionary as BirthdayData:
- Store the name and birthdate using default value
  - `New Dictionary(Of String, String) From {{"John", "May/01/1991"}}`
- Store 2 more data using Assign Activity
- Print entire dictionary
- Print only Keys
- Print only Values
- Print Values using the key

### Exercise #10
You have been given the date of birth (DOB) in string format. How will you convert it into DateTime format?

:pushpin:

1. Working with datetime to string

`Convert.ToDateTime(DOB).ToString("MM/dd") + "/" + Now.Year.ToString("00")`

2. Working with datetime

 `New DateTime(Now.Year, newDOB.Month,newDOB.Day) - newDOB a datetime variable`

### Exercise #11
Create a Dictionary with names and birthdates. Find out how many days passed by or number of days to wait from/starting today.

:pushpin:
`countOfDays = DateDiff(DateInterval.Day, newBirthDate, todayDate)`  (type = Int64)

### Exercise #12
Create a list of names and sort the names in Ascending and Descending order. Post each sort in a message box, only the top 3 data.

:pushpin:

1. Using LINQ

`newList = names.OrderByDescending(Function(x) x).ToList`

`newList = names.OrderBy(Function(x) x).ToList`

`String.Join(", ", newList.GetRange(0,3))` - To post just the top 3

2. Using **Invoke Method Activity**

### Exercise #13
What is the output?

:pushpin:

`String.Format(“His name is {0}, whose rank is {1}”, ”John”, 1)`

### Exercise #15
Using dictionary data type, count the number of Books written by each Author?

:pushpin:

- Creating a new dictionary where:
  - Key = Author (Str)
  - Value = nr. of books (Int)

- `tempBooks.ContainsKey(item)`
- Creating a counter
  - `tempBooks(item) = tempBooks(item) + 1`


