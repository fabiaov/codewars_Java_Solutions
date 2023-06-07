# Codewars Java Solutions
## First Kata
1) Create a function with two arguments that will return an array of the first n multiples of x.

Assume both the given number and the number of times to count will be positive numbers greater than 0.

Return the results as an array or list ( depending on language ).

Exemples

```java
countBy(1,10)  // should return  {1,2,3,4,5,6,7,8,9,10}
countBy(2,5)  // should return {2,4,6,8,10} 
```  
### Solution 1

```java
import java.util.stream.IntStream;

public class Kata{
  public static int[] countBy(int x, int n){
    
    return IntStream.rangeClosed(1, n)
      .map(i -> i * x)
      .toArray();
  }
}

```
### Solution 2

```java
public class Kata{
  public static int[] countBy(int x, int n){
    int[] arr = new int[n];
    for(int i = 0; i < n; i++)  arr[i] = x * (i+1);
    return arr;
  }
}
```


# Counting Sheeps
### Solution 1
```java
import java.util.Arrays;

public class Counter {
  public int countSheeps(Boolean[] arrayOfSheeps) {
    // TODO May the force be with you
    return Arrays.stream(arrayOfSheeps).filter(x -> x != null).filter(x -> x == true).toArray().length;
  }
}

```
### Solution 2
```java
import java.util.Arrays;
import java.util.Collections;

public class Counter {
  public int countSheeps(Boolean[] arrayOfSheeps) {
    return Collections.frequency(Arrays.asList(arrayOfSheeps), true);
  }
}

```
### Solution 3
```java
import java.util.*;
public class Counter {
  public int countSheeps(Boolean[] arrayOfSheeps) {
     return (int)Arrays.stream(arrayOfSheeps)
                 .filter(Objects::nonNull)
                 .filter(Boolean::booleanValue).count();
  }
}
```

# Calculate BMI
### Solution 1
```java
public class Calculate {
  public static String bmi(double weight, double height) {
     double bmi =weight/(height*height);
    return bmi <= 18.5 ? "Underweight": bmi <=25.0 ? "Normal" : bmi<=30.0 ? "Overweight" : "Obese";
    }
    }

```
### Solution 2
```java
public class Calculate {
  public static String bmi(double weight, double height) {
	
		double bmi = weight/(height*height);
    
    String gewicht = "";
		
		if (bmi <= 18.5) {
			gewicht = "Underweight";
		} else if (bmi <= 25.0) {
			gewicht =  "Normal";
		} else if (bmi <= 30.0) {
			gewicht =  "Overweight";
		} else if(bmi > 30) {
			gewicht =  "Obese";
		}
    return gewicht; 
	}
}

```
# Count of positives / sum of negatives
Given an array of integers.

 Return an array, where the first element is the count of positives numbers and the second element is sum of negative numbers.

 If the input array is empty or null, return an empty array.

 The passed array should NOT be changed. Read more here.

 For example:

 input int[] {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, -11, -12, -13, -14, -15} 
 return int[] {10, -65}.
 
 ### Solution 1 Clever one
```java
import java.util.stream.*;

public class Kata {

  public static int[] countPositivesSumNegatives(int[] input) {
    return input == null || input.length == 0 ? 
      new int[0] : 
      new int[] { (int)IntStream.of(input).filter(i->i>0).count(), IntStream.of(input).filter(i->i<0).sum() };
  }
}

```
### Solution 2 
```java
public class Kata
{
    public static int[] countPositivesSumNegatives(int[] input)
    {
       if (input == null || input.length == 0) return new int[] {};
       int count = 0,sum = 0;
       for (int i : input) {
         if (i > 0) count ++;
         if (i < 0) sum += i;
       }
       return new int[] {count,sum};
    }
}

```

# Abbreviate A Two Word Name
Write a function to convert a name into initials. This kata strictly takes two words with one space in between them.

The output should be two capital letters with a dot separating them

Example
Sam Harris => S.H

Patrick Feeney => P.F

### Solution 1
```java
public class AbbreviateTwoWords {

  public static String abbrevName(String name) {
    String[] names = name.split(" ");
    return (names[0].charAt(0) + "." + names[1].charAt(0)).toUpperCase();
  }
}

```

### Solution 2
```java
public class AbbreviateTwoWords {

  public static String abbrevName(String name) {
    return name.toUpperCase().replaceAll("(.).*\\s(.).*", "$1.$2");
  }
  
}

```
### Solution 3
```java
import java.util.Arrays;
import java.util.stream.Collectors;

public class AbbreviateTwoWords {

  public static String abbrevName(String name) {
    return Arrays.stream(name.split(" "))
                 .map(String::toUpperCase)
                 .map(word -> word.substring(0, 1))
                 .collect(Collectors.joining("."));
               
  }
  
}

```
