Location: https://leetcode.com/problems/design-add-and-search-words-data-structure/description/
# Question
Design a data structure that supports adding new words and finding if a string matches any previously added string.

Implement the WordDictionary class:

- WordDictionary() Initializes the object.
- void addWord(word) Adds word to the data structure, it can be matched later.
- bool search(word) Returns true if there is any string in the data structure that matches word or false otherwise. word may contain dots '.' where dots can be matched with any letter.
# Example

## Example 1:

Input\
["WordDictionary","addWord","addWord","addWord","search","search","search","search"]\
[[],["bad"],["dad"],["mad"],["pad"],["bad"],[".ad"],["b.."]]

Output\
[null,null,null,null,false,true,true,true]

Explanation\
WordDictionary wordDictionary = new WordDictionary();\
wordDictionary.addWord("bad");\
wordDictionary.addWord("dad");\
wordDictionary.addWord("mad");\
wordDictionary.search("pad"); // return False\
wordDictionary.search("bad"); // return True\
wordDictionary.search(".ad"); // return True\
wordDictionary.search("b.."); // return True

## Constraints:

1 <= word.length <= 25\
word in addWord consists of lowercase English letters.\
word in search consist of '.' or lowercase English letters.\
There will be at most 2 dots in word for search queries.\
At most 104 calls will be made to addWord and search.
 

# My solution (follows instructions on solutions)
```python
class TrieNode:
    def __init__(self):
        self.children = {}  # Dictionary to store child nodes
        self.is_end = False  # Marks the end of a word

class WordDictionary(object):

    def __init__(self):
        self.root = TrieNode()

    def addWord(self, word):
        """
        :type word: str
        :rtype: None
        """
        node = self.root
        for w in word:
            if w not in node.children:
                node.children[w] = TrieNode()
            node = node.children[w]
        node.is_end = True

    def search(self, word):
        """
        :type word: str
        :rtype: bool
        """
        return self._search_pattern(word, self.root)
    
    def _search_pattern(self, pattern, node):
        for ind, w in enumerate(pattern):
            if w == ".":
                for child in node.children.values():
                    if self._search_pattern(pattern[ind+1:], child):
                        return True
                return False
            elif w not in node.children:
                return False
            node = node.children[w]
        return node.is_end
        
```
