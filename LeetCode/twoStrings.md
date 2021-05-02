Given two strings a and b, return the minimum number of times you should repeat string a so that string b is a substring of it. If it is impossible for b​​​​​​ to be a substring of a after repeating it, return -1.

Notice: string "abc" repeated 0 times is "",  repeated 1 time is "abc" and repeated 2 times is "abcabc".

Example 1:  

Input: a = "abcd", b = "cdabcdab"  
Output: 3  
Explanation: We return 3 because by repeating a three times "abcdabcdabcd", b is a substring of it.  
Example 2:  

Input: a = "a", b = "aa"  
Output: 2  


Example 3:  

Input: a = "a", b = "a"  
Output: 1  


Example 4:  

Input: a = "abc", b = "wxyz"  
Output: -1  
 

Constraints:  

1 <= a.length <= 104  
1 <= b.length <= 104  
a and b consist of lower-case English letters.    


```
func repeatedStringMatch(a string, b string) int {

	if b == "" {
		return 0
	}

	if isSubString(a,b){
		return 1
	}


	temp := a
	n := len(a)

	count := 2

	a = a + temp

	for {


		if isSubString(a, b) {
			return count
		}

		count++

		if len(a) - len(b) >= n {

			return -1
		}

		a = a + temp

	}

}

func isSubString(a, b string) bool {


	aLen := len(a)
	bLen := len(b)



	if bLen > aLen {

		return false
	}


	for i := 0; i <= aLen-bLen; i++ {

		if b == a[i:i+bLen] {
			return true
		}

	}

	return false
}

```
