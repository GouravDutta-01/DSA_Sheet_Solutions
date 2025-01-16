# [Design Add and Search Words Data Structure](https://leetcode.com/problems/design-add-and-search-words-data-structure/)
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
class WordDictionary {
    TrieNode root;

    public WordDictionary() {
        root = new TrieNode();
    }
    
    public void addWord(String word) {
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
        return solve(0, root, word.toCharArray());
    }

    public boolean solve(int ind, TrieNode node, char[] arr){
        if(ind == arr.length){
            return node.eow;
        }
        if(arr[ind] == '.'){
            for(TrieNode t : node.children){
                if(t != null && solve(ind+1, t, arr)){
                    return true;
                } 
            }
            return false;
        }
        if(node.children[arr[ind]-'a'] == null){
            return false;
        }
        node = node.children[arr[ind]-'a'];
        return solve(ind+1, node, arr);
    }
}

/**
 * Your WordDictionary object will be instantiated and called as such:
 * WordDictionary obj = new WordDictionary();
 * obj.addWord(word);
 * boolean param_2 = obj.search(word);
 */
```
