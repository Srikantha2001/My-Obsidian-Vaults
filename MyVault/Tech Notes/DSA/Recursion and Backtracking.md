- <mark style="background: #D2B3FFA6;">Recursion</mark> -> Converting a problem ( solution ) to its smaller version.
```
fibonacci(n) = fibonacci(n-1) + fibonacci(n-2);
```
- <mark style="background: #FFB86CA6;">Tail Recursion</mark> -> 
	- if the last statement of the recursive function is the recursion call.
	- Can be converted to loops.
- Parts of Recursion
	- <mark style="background: #FFB8EBA6;">Base Condition</mark> : 
		- the condition which terminates the recursion
		- simplest case of the problem that recursion is solving
	- <mark style="background: #FFB8EBA6;">Recursive Call</mark> :
		- Smaller version of the same problem.
```Java
public int fibonacci(int n){
	// base condition
	if(n==0 || n==1) return n;
	// recursive call
	return fibonacci(n-1) + fibonacci(n-2);
}
```

NOTES : 
1. Where-ever recursion is involved, there is an additional <mark style="background: #D2B3FFA6;">space requirement</mark> for Function Call stack
2. <mark style="background: #ADCCFFA6;">Parameterized</mark> : the aggregate parameter is sent in function call as an argument.
3. <mark style="background: #FFF3A3A6;">Functional</mark>  : the function itself return desired result


## PROBLEMS  

### 1. TOWER OF HANOI

- Given **n** discs and 3 pegs (*source*,*destination*,*intermediate*), all the discs have to be moved from source to destination following the following rules
	- All discs initially in source. they are arranged in increasing weight. disc of higher weight can't be placed on lower ones.
	- Only one disc can be moved in an operation.
```Java
/*
 * 
 *                PROBLEM 01 - TOWER OF HANOI
 * 
 *      To move n discs from source to destination via intermediate, following steps are have to be followed
 *          1. first move n-1 discs from source to intermediate
 *          2. then move nth disc from source to destination.
 *          3. then move remaining n-1 discs from source to destination
 */

import java.util.Scanner;

public class Prog1 {

    static void TowerOfHanoi(int discCount,String source,String dest, String intermediate){
        // base condition : only variable parameter is number of disc, base case is when we have only one disc, then we move it from source to dest
        if(discCount == 1){
            System.out.println("Move Disc " + discCount + " from " + source + " to " + dest);
            return;
        }
        TowerOfHanoi(discCount-1, source, intermediate, dest);
        System.out.println("Move Disc " + discCount + " from " + source + " to " + dest);
        TowerOfHanoi(discCount-1, intermediate, dest, source);

    }

    public static void main(String [] args){
        String source="SOURCE", dest="DESTINATION", intermediate="INTERMEDIATE" ;
        Scanner sc = new Scanner(System.in);
        int discCount = sc.nextInt();
        TowerOfHanoi(discCount,source,dest,intermediate);
    }
}
```

