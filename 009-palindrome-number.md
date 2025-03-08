# https://leetcode.com/submissions/detail/1265864134/

![009-palindrome-number.png](img/009-palindrome-number.png)

```c++
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0) {
            return false;
        }
        if (x == 0) {
            return true;
        }
        const std::string num_forward = std::to_string(x);
        const std::string num_reverse = [](const std::string& num) {
            std::string reverse = num;
            std::reverse(reverse.begin(), reverse.end());
            reverse.erase(reverse.begin(), std::find_if(reverse.begin(), reverse.end(), [](auto ch) {
                return ch != '0';
            }));
            return reverse;
        }(num_forward);
        return num_forward == num_reverse;  
    }
};
```