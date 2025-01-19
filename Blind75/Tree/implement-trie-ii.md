# [Implement Trie ll](https://www.naukri.com/code360/problems/implement-trie_1387095)
**Difficulty:** Medium

### Solution in Java
```java
import java.util.* ;
import java.io.*; 
class TrieNode{
    TrieNode[] children;
    boolean eow;
    int count;//counts total words that ends with the given node
    int count1;//counts total words that contains the given node at its prefix
    public TrieNode(){
        children = new TrieNode[26];
        eow = false;
        count = 0;
        count1 = 0;
    }
}
public class Trie {
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
            curr.count1++;
        }
        curr.count++;
        curr.eow = true;
    }

    public int countWordsEqualTo(String word) {
        TrieNode curr = root;
        for(char ch : word.toCharArray()){
            int ind = ch-'a';
            if(curr.children[ind] == null){
                return 0;
            }
            curr = curr.children[ind];
        }
        return curr.count;
    }

    public int countWordsStartingWith(String word) {
        TrieNode curr = root;
        for(char ch : word.toCharArray()){
            int ind = ch-'a';
            if(curr.children[ind] == null){
                return 0;
            }
            curr = curr.children[ind];
        }
        return curr.count1;
    }

    public void erase(String word) {
        TrieNode curr = root;
        for(char ch : word.toCharArray()){
            int ind = ch-'a';
            curr.children[ind].count1--;
            if(curr.children[ind].count1 == 0){
                curr.children[ind] = null;
                return;
            }
            curr = curr.children[ind];
        }
        if(curr.count >= 1){
            curr.count--;
        }
    }

}
```
