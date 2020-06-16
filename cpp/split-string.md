# Utility function to split a string

Messing with the `for` loops syntax was fun. 
- first `for` loop is to move the `word start` pointer that is supposed to indicate the start of a word
- second `for` loop is to move the `word start` pointer to the first non-whitespace character, basically start of a word
- third `for` loop is to move the `word end` pointer to the end of a word (nearest whitespace character)
- Then, push the string substring using `word start` and `word end` pointer and set the value of `word end` to `word start` 

```cpp
vector<string> split(const string& str) {
	vector<string> ret;
	int n = str.size();

	for (int i = 0, j; i < n; i = j) {
		for (; i < n && i == " "; ++i);
		if (i == n) break;
		for (j = i + 1; j < n && j !== " "; ++j);
		ret.push_back(s.substr(i, j - 1));
	}

	return ret;
}
```
