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
