Location: https://leetcode.com/problems/implement-trie-prefix-tree/description/
# Question
A trie (pronounced as "try") or prefix tree is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:

- Trie() Initializes the trie object.
- void insert(String word) Inserts the string word into the trie.
- boolean search(String word) Returns true if the string word is in the trie (i.e., was inserted before), and false otherwise.
- boolean startsWith(String prefix) Returns true if there is a previously inserted string word that has the prefix prefix, and false otherwise.
# Example

## Example 1:

Input\
["Trie", "insert", "search", "search", "startsWith", "insert", "search"]\
[[], ["apple"], ["apple"], ["app"], ["app"], ["app"], ["app"]]

Output\
[null, null, true, false, true, null, true]

Explanation\
Trie trie = new Trie();\
trie.insert("apple");\
trie.search("apple");   // return True\
trie.search("app");     // return False\
trie.startsWith("app"); // return True\
trie.insert("app");\
trie.search("app");     // return True

## Constraints:

1 <= word.length, prefix.length <= 2000\
word and prefix consist only of lowercase English letters.\
At most 3 * 104 calls in total will be made to insert, search, and startsWith.
 

# My solution 
```python
class Trie(object):

    def __init__(self):
        self.words = set()
        

    def insert(self, word):
        """
        :type word: str
        :rtype: None
        """
        self.words.add(word)
        

    def search(self, word):
        """
        :type word: str
        :rtype: bool
        """
        return word in self.words
        

    def startsWith(self, prefix):
        """
        :type prefix: str
        :rtype: bool
        """
        for word in self.words:
            if word[:len(prefix)] == prefix:
                return True
        return False
        
```
