#include <iostream>
#include <string>

const int TABLE_SIZE = 128;

class HashNode {
public:
    std::string key;
    int value;
    HashNode* next;
    HashNode(std::string key, int value) {
        this->key = key;
        this->value = value;
        this->next = NULL;
    }
};

class HashTable {
private:
    HashNode** table;
public:
    HashTable() {
        table = new HashNode*[TABLE_SIZE]();
    }
    int hashFunction(std::string key) {
        int hash = 0;
        for (int i = 0; i < key.length(); i++) {
            hash = (hash + (int)key[i]) % TABLE_SIZE;
        }
        return hash;
    }
    void insert(std::string key, int value) {
        int hash = hashFunction(key);
        if (!table[hash]) {
            table[hash] = new HashNode(key, value);
        } else {
            HashNode* entry = table[hash];
            while (entry->next) {
                entry = entry->next;
            }
            entry->next = new HashNode(key, value);
        }
    }
    int search(std::string key) {
        int hash = hashFunction(key);
        if (table[hash]) {
            HashNode* entry = table[hash];
            while (entry) {
                if (entry->key == key) {
                    return entry->value;
                }
                entry = entry->next;
            }
        }
        return -1;
    }
};

int main() {
    HashTable ht;
    ht.insert("hello", 1);
    ht.insert("world", 2);
    std::cout << ht.search("hello") << std::endl;
    std::cout << ht.search("world") << std::endl;
    return 0;
}
