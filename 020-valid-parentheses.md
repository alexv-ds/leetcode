# https://leetcode.com/submissions/detail/1265853840/

![020-valid-parentheses.png](img/020-valid-parentheses.png)

```c++
class Solution {
public:
    inline char get_close_parenthal(const char ch) {
        switch (ch) {
            case '(': return ')';
            case '{': return '}';
            case '[': return ']';
            default: return 0;
        }
    }

    inline char get_open_parenthal(const char ch) {
        switch (ch) {
            case ')': return '(';
            case '}': return '{';
            case ']': return '[';
            default: return 0;
        }
    }

    bool isValid(string s) {
        std::stack<char> stack;

        for (const char ch : s) {
            if (const char close_ch = get_close_parenthal(ch); close_ch != 0) {
                stack.push(ch);
            } else if (const char open_ch = get_open_parenthal(ch); open_ch != 0 && !stack.empty()) {
                if (stack.top() == open_ch) {
                    stack.pop();
                } else {
                    return false;
                }
            } else {
                return false;
            }
        }

        return stack.empty();
    }
};
```