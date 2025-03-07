# https://leetcode.com/submissions/detail/1552763973/

![003-longest-substring-without-repeating-characters.png](img/003-longest-substring-without-repeating-characters.png)

```c++
namespace {
  int substring_unique_size(const std::string_view sub) {
    std::bitset<256> bitset;
    int size = 0;
    for (const char ch : sub) {
      decltype(bitset)::reference ch_state =
        bitset[static_cast<std::size_t>(std::bit_cast<unsigned char>(ch))];
      if (ch_state == true) {
        return size;
      }
      ch_state = true;
      ++size;
    }
    return size;
  }
}

class Solution {
public:
  int lengthOfLongestSubstring(string s) {
    int max_size = 0;
    for (auto it = s.begin(); it != s.end(); ++it) {
      max_size = std::max(substring_unique_size({it, s.end()}), max_size);
    }
    return max_size;
  }
};
```