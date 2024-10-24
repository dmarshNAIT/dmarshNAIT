---
layout: page
title: Arrays
permalink: /cpsc1012/arrays
parent: CPSC1012
nav_order: 10
---
# Arrays
Arrays are **collections** of items. Each item in an array must be of the same **data type**.

Arrays are also a set size: we can't change our mind and adjust the size later.

## Creating an array

### Default values
One way to create an array is to simply identify the **data type**, and set the **size**:
    
```csharp
const int ARRAY_SIZE = 5;
int[] myInts = new int[ARRAY_SIZE];
```
This means all elements in this array will be of type `int`, and there are `5` elements. Unless I initialize the value, they will all hold the **default** value for that data type.

`int`s have a default value of `0`, so right now, that array looks like:

| index: | 0 | 1 | 2 | 3 | 4 |
| :---:|:---:|:---:|:---:|:---:|:---:|
| value: | `0` | `0` | `0` | `0` | `0` |

> 💡 Remember: indexes start at 0, not 1.

***

### Loading data
Alternatively, we can load data into the array at the same time as we create it:

```csharp
string[] dayOfWeek = new string[7] {
        "SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT" };
```

Since we've provided 7 values, we've indirectly already provided the array size, so we can even drop the `new string[7]` part:

```csharp
string[] dayOfWeek = { 
    "SUN", "MON", "TUE", "WED", "THU", "FRI", "SAT" }; 
```

Both will result in an array that can be represented like this:

| index: | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| :---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| value: | `"SUN"` | `"MON"` | `"TUE"` | `"WED"` | `"THU"` | `"FRI"` | `"SAT"` | 

***

## Accessing elements in an array
Once an array exists, we can view or modify each element by using **square brackets** and the **index** of the element:

```csharp
const int ARRAY_SIZE = 10;
int[] someNumbers = new int[ARRAY_SIZE];
someNumbers[0] = 5;
```

I just set the 0th element of the array to the value `5`. The contents of my array are now:

| index: | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
| :---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---: |
| value: | `5` | `0` | `0` | `0` | `0` | `0` | `0` | `0` | `0` | `0` |

Because we know exactly how many elements are in the array, I could then **loop** through each element and set each value:

```csharp
const int ARRAY_SIZE = 10;
int[] someNumbers = new int[ARRAY_SIZE];

for (int index = 0; index < ARRAY_SIZE; index++) {
    someNumbers[index] = 6; // set every element to the value 6
}
```

We can assign values to the element using **literals** (as shown in the previous example), using **variable** names, or **expressions**. We can also leverage the `.Length` property, which returns the **number of elements** in an array.

```csharp
const int ARRAY_SIZE = 10;
int[] someNumbers = new int[ARRAY_SIZE];
Random numberGenerator = new Random();

for (int index = 0; index < someNumbers.Length; index++) {
    someNumbers[index] = numberGenerator.Next(1,11);
}
```

## Sorting arrays

`Array.Sort()` will sort the elements in a 1-dimensional array.

```csharp
int[] myArray = new int[5] { 6, 4, 7, 2, 8 };
Array.Sort(myArray); // now array is: {2, 4, 6, 7, 8}
```

## Multi-dimensional arrays
We are not limited to creating 1-D arrays: here is an example of creating a 3x3 (or 2-Dimensional) array.

```csharp
int [,] board = new int [3,3]; // first digit is the row, 2nd digit is the column
board [1,1] = 1;
```
We've created a 3x3 array, and then set the element in the 1st row and 1st column to the value `1`:

| indices | 0 | 1 | 2 |
| :---:|:---:|:---:|:---:|
| **0** | `0` | `0` | `0` |
| **1** | `0` | `1` | `0` |
| **2** | `0` | `0` | `0` |