# [Implement Trie (Prefix Tree)](https://leetcode.com/problems/implement-trie-prefix-tree/)
**Difficulty:** Medium

### Solution in Java
```java
class TrieNode{
    TrieNode[] children;
    boolean eow;
    public TrieNode(){
        children = new TrieNode[26];
        eow = false;
    }
}
class Trie {
    TrieNode root;

    public Trie() {
        root = new TrieNode();
    }
    
    public void insert(String word) {
        TrieNode curr = root;
        for(char ch : word.toCharArray()){
            int ind = ch-'a';
            if(curr.children[ind] == null){
                curr.children[ind] = new TrieNode();
            }
            curr = curr.children[ind];
        }
        curr.eow = true;
    }
    
    public boolean search(String word) {
        TrieNode curr = root;
        for(char ch : word.toCharArray()){
            int ind = ch-'a';
            if(curr.children[ind] == null){
                return false;
            }
            curr = curr.children[ind];
        }
        return curr.eow;
    }
    
    public boolean startsWith(String prefix) {
        TrieNode curr = root;
        for(char ch : prefix.toCharArray()){
            int ind = ch-'a';
            if(curr.children[ind] == null){
                return false;
            }
            curr = curr.children[ind];
        }
        return true;   
    }
}

/**
 * Your Trie object will be instantiated and called as such:
 * Trie obj = new Trie();
 * obj.insert(word);
 * boolean param_2 = obj.search(word);
 * boolean param_3 = obj.startsWith(prefix);
 */
```
