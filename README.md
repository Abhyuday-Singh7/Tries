"# Tries" 
class Node{
    public:
        Node* link[26];
        bool flag;
        bool alphabetexist(char a){
            return (link[a-'a']!=NULL);
        }
};
class Trie {
    Node* root;
public:
    Trie() {
        root=new Node();
    }
    
    void insert(string word) {
        Node *node=root;
        for(int i=0;i<word.length();i++){
            if(node->alphabetexist(word[i])!=true){
                node->link[word[i]-'a']=new Node();
            }
            node=node->link[word[i]-'a']; //To go to next node
        }
        node->flag=true; //sets the word has ended
    }
    
    bool search(string word) {
        Node *node=root;
        for(int i=0;i<word.length();i++){
            if(node->alphabetexist(word[i])!=true){
                return false;
            }
            node=node->link[word[i]-'a']; //To go to next node
        }
        return node->flag;
    }
    
    bool startsWith(string prefix) {
        Node *node=root;
        for(int i=0;i<prefix.length();i++){
            if(node->alphabetexist(prefix[i])!=true){
                return false;
            }
            node=node->link[prefix[i]-'a']; //To go to next node
        }
        return true;
    }
};
Note:
Using references instead of actually going to next object reduces time taken significantly
