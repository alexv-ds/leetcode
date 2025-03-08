# https://leetcode.com/submissions/detail/1567342498/

![014-longest-common-prefix.png](img/014-longest-common-prefix.png)

```c++
namespace {
  std::string longestCommonPrefixImpl(const std::vector<std::string>& strs) {
    if (strs.empty()) {
      return "";
    }
    if (strs.size() == 1) {
      return strs.front();
    }

    std::size_t min_size = std::numeric_limits<std::size_t>::max();
    for (const auto& str : strs) {
      min_size = std::min(str.size(), min_size);
    }

    if (min_size == 0) {
      return "";
    }

    std::size_t ch_idx = 0;
    for (; ch_idx < min_size; ++ch_idx) {
      const char ch = strs.front()[ch_idx];
      for (auto it = strs.begin() + 1; it != strs.end(); ++it) {
        if ((*it)[ch_idx] != ch) {
          return {strs.front().begin(), strs.front().begin() + ch_idx};
        }
      }
    }

    return {strs.front().begin(), strs.front().begin() + ch_idx};
  }
}

class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        return longestCommonPrefixImpl(strs);
    }
};
```