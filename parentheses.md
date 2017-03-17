# Parentheses Problem
### Valid Parentheses
[problem description](https://leetcode.com/problems/valid-parentheses/#/description)

Ideas:
- Using stack, whenever meeting a right bracket:
- If stack is empty, return False
- Pop out the toppest element, if they don't pair, return false
- In the end, if the stack is not empty, return False; otherwise, True
```
class Solution(object):
    def isValid(self, s):
        stack = []
        labels = {'(': (')', -1), ')': ('(', 1), '[': (']', -1), ']': ('[', 1), '{':('}', -1), '}':('{', 1)}
        for ch in s:
            pair, val = labels[ch]
            if val<0:
                stack.append(ch)
            if val>0:
                if len(stack) == 0:
                    return False
                top = stack.pop()
                if top != pair:
                    return False
        if len(stack) != 0:
            return False
        return True
```
