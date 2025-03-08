# https://leetcode.com/submissions/detail/1208967559/

![012-integer-to-roman.png](img/012-integer-to-roman.png)

```c++
#include <map>

#include <map>
#include <string>
#include <iostream>

const std::map<int, std::string> symbols = {
    {1, "I"},
    {4, "IV"},
    {5, "V"},
    {9, "IX"},
    {10, "X"},
    {40, "XL"},
    {50, "L"},
    {90, "XC"},
    {100, "C"},
    {400, "CD"},
    {500, "D"},
    {900, "CM"},
    {1000, "M"}
};

std::string make_symbol(int& i) {
  std::string result;
  for (auto it = symbols.rbegin(); it != symbols.rend(); ++it) {
    if (i >= it->first) {
      i -= it->first;
      result += it->second;
      return result;
    }
  }
  return result;
}

std::string int2roman(int i) {
  std::string str;
  while(i > 0) {
    str += make_symbol(i);
  }
  return str;
}

class Solution {
public:
    string intToRoman(int num) {
        return int2roman(num);
    }
};
```