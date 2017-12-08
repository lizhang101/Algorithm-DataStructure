# [205. Isomorphic Strings](https://leetcode.com/problems/isomorphic-strings/description/)
## Problem Description
Given two strings s and t, determine if they are isomorphic.

Two strings are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

For example,
```
Given "egg", "add", return true.

Given "foo", "bar", return false.

Given "paper", "title", return true.
```
Note:
You may assume both s and t have the same length.

## Solution
- solution 1

  Basic idea : normalize pattern for each string and compare them char by char.
  ```
   "egg" -> 122, "add" -> 122  ====> equal       ====> return true
   "foo" -> 122, "bar" -> 123  ====> not equal   ====> return false     
  ```
  Code
  ```
  var isIsomorphic = function(s, t) {
      var s_code = s.split("").map(c => c.charCodeAt(0));
      var t_code = t.split("").map(c => c.charCodeAt(0));
      var s_map = new Array(256);
      var t_map = new Array(256);
      s_map.fill(-1);
      t_map.fill(-1);

      for (var i = 0; i < s.length; i++) {
          if (!(s_map[s_code[i]]  === t_map[t_code[i]]))    return false;
          s_map[s_code[i]] = t_map[t_code[i]] = i;
      }
      return true;
  };
  ```
  
- solution 2

  Basic idea : build map between string1's character and string2's corresponding position character.
  ```
  var isIsomorphic = function(s, t) {    
    var map = {};    
    if (s.length !== t.length){
        return false;
    }
    
    for (var i = 0; i < s.length; i++){
      // if key-value not exist and value not occurred before, add key-value pair to map
      if ((typeof map[s[i]]) === "undefined" && t.slice(0,i).indexOf(t[i]) === -1){
        map[s[i]] = t[i];
        continue;
      }
      if (map[s[i]] === t[i]){
        continue;
      }
      return false;
    }    
    return true;
  };
  ```

# [290. Word Pattern](https://leetcode.com/problems/word-pattern/description/)
## Problem Description
Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

Examples:
```
pattern = "abba", str = "dog cat cat dog" should return true.
pattern = "abba", str = "dog cat cat fish" should return false.
pattern = "aaaa", str = "dog cat cat dog" should return false.
pattern = "abba", str = "dog dog dog dog" should return false.
```
Notes:
You may assume pattern contains only lowercase letters, and str contains lowercase letters separated by a single space.

## Solution
- solution 1
  The basic idea is exactly same as problem 205. solution 2.
  ```
  var wordPattern = function(pattern, str) {
      var ptn_arr = pattern.split("");
      var str_arr = str.split(" ");
      if (ptn_arr.length !== str_arr.length)   return false;

      var map = {};
      for (var i = 0; i < pattern.length; i++) {
          if ((typeof map[ptn_arr[i]] === "undefined") && (str_arr.slice(0, i).indexOf(str_arr[i]) == -1)) {
              map[ptn_arr[i]] = str_arr[i];
              continue;
          }
          if (map[ptn_arr[i]] === str_arr[i])   continue;
          return false;
      }
      return true;
  };
  ```
  
- solution 2

  Use two Map(), one is pattern-str map, the other one is str-pattern map. For each character/substr of pattern/str, check the two maps.
  The pattern <-> str should either all exist or all non-exist. If not, return false.
  
  ```
  var wordPattern = function(pattern, str) {
      var ptn_arr = pattern.split("");
      var str_arr = str.split(" ");
      if (ptn_arr.length !== str_arr.length)   return false;

      var p2sMap = new Map();
      var s2pMap = new Map();

      for (var i = 0; i < ptn_arr.length; i++) {
          if (p2sMap.has(ptn_arr[i])) {
              if (p2sMap.get(ptn_arr[i]) !== str_arr[i])    return false;
          } else if (s2pMap.has(str_arr[i])) {
              if (s2pMap.get(str_arr[i]) !== ptn_arr[i])    return false;
          } else {
              p2sMap.set(ptn_arr[i], str_arr[i]);
              s2pMap.set(str_arr[i], ptn_arr[i]);
          }
      }
      return true;
  };
  ```

## JavaScript knowledge
### [Map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Map)

The Map object holds key-value pairs. Any value (both objects and primitive values) may be used as either a key or a value. 
- Syntax : `var myMap = new Map([iterable])`. `Map.prototype.size` returns the number of key/value pairs in the Map object.
- A Map object iterates its elements in insertion order — a _**for...of**_ loop returns an array of [key, value] for each iteration.
- methods:

  methods | description
  ------- | -----------------------------------------------------------------------------------------------------
  `Map.prototype.set(key, value)` | Sets the value for the key in the Map object. Returns the Map object.
  `Map.prototype.get(key)` | Returns the value associated to the key, or undefined if there is none.
  `Map.prototype.has(key)` | Returns a boolean asserting whether a value has been associated to the key in the Map object or not.
  `Map.prototype.delete(key)` | Returns true if an element in the Map object existed and has been removed, or false if the element does not exist. Map.prototype.has(key) will return false afterwards.
  `Map.prototype.clear()` | Removes all key/value pairs from the Map object.
  `Map.prototype.keys()` | Returns a new Iterator object that contains the keys for each element in the Map object in insertion order.
  `Map.prototype.values()` | Returns a new Iterator object that contains the values for each element in the Map object in insertion order.
  `Map.prototype.entries()` | Returns a new Iterator object that contains an array of [key, value] for each element in the Map object in insertion order.
  `Map.prototype.forEach(callbackFn[, thisArg])` | Calls callbackFn once for each key-value pair present in the Map object, in insertion order. If a thisArg parameter is provided to forEach, it will be used as the this value for each callback.
  

  
