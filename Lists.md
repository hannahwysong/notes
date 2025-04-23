## Lists 
A ***list*** is a common ADT for holding ordered data, having operations like append a data item, remove a data item, check if a data item exists, and print the list.\\
### Common List Operations:
Append(X) 	|Inserts X at end of list 	|list.Append(44)  list: (99, 77, 44) |
Prepend(X) 	|Inserts X at start of list 	|list.Prepend(44)  list: (44, 99, 77) |
InsertAfter(W, X) 	|Inserts X after W 	|list.InsertAfter(99, 44) list: (99, 44, 77) |
Remove(X) 	|Removes X 	|list.Remove(77) list: (99) |
Contains(X) 	|Returns true if X is in the list, false otherwise 	|list.Contains(99) returns true list.Contains(22) returns false |
Print() 	|Prints list's items in order 	|list.Print() outputs: 99, 77 |
Sort() 	|Sorts list's items in ascending order 	|list.Sort() list: (77, 99) |
IsEmpty() 	|Returns true if list has no items 	|list.IsEmpty() returns false |
GetLength() 	|Returns the number of items in the list 	|list.GetLength() returns 2 |
