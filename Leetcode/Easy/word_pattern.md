## [290. Word Pattern](https://leetcode.com/problems/word-pattern/description/)
### Description
Given a _**pattern**_ and a string _**str**_, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.
```
Examples:
pattern = "abba", str = "dog cat cat dog" should return true.
pattern = "abba", str = "dog cat cat fish" should return false.
pattern = "aaaa", str = "dog cat cat dog" should return false.
pattern = "abba", str = "dog dog dog dog" should return false.
```
Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters separated by a single space.

### Solution
Build map between pattern character and String words.
```
public boolean wordPattern(String pattern, String str) {
        String[] arr= str.split(" ");
        HashMap<Character, String> map = new HashMap<Character, String>();
        if(arr.length!= pattern.length())
            return false;
        for(int i=0; i<arr.length; i++){
            char c = pattern.charAt(i);
            if(map.containsKey(c)){
                if(!map.get(c).equals(arr[i]))
                    return false;
            }else{
                if(map.containsValue(arr[i]))
                    return false;
                map.put(c, arr[i]);
            }    
        }
        return true;        
    }
```

### Java Knowledge
- String to char array  
  - method syntax : `public char[] toCharArray()`
  - example code
  ```
  String str = "hello";  
  char[] ch = str.toCharArray();     // ['h', 'e', 'l', 'l', 'o']
  ```
- split String by whitespace or tabs
  ```
  // 1. split by single whitespace
  String lineOfCurrencies = "USD JPY AUD SGD HKD CAD CHF GBP EURO INR"; 
  String[] currencies = lineOfCurrencies.split(" ");    // ["USD", "JPY", "AUD", "SGD", "HKD", "CAD", "CHF", "GBP", "EURO", "INR"]
  System.out.println("output string: " + Arrays.toString(currencies));
  
  // 2. split by multiple whitespaces
  String lineOfPhonesWithMultipleWhiteSpace = "iPhone  Galaxy   Lumia"; 
  String[] phones = lineOfPhonesWithMultipleWhiteSpace.split("\\s+");  // ["iPhone", "Galaxy", "Lumia"]
  
  // 3. split String with leading and trailing whitespace
  String linewithLeadingAndTrallingWhiteSpace = " Java C++ "; 
  String[] languages = linewithLeadingAndTrallingWhiteSpace.split("\\s");   // ["", "Java", "C++"]
  languages = linewithLeadingAndTrallingWhiteSpace.trim().split("\\s+");    // ["Java", "C++"]
  ```
