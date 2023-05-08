[Back](../04.%20puzzle3.md)

### Solution using Python Puzzle number 3
```python
def enter_combination_lock():  
	print(f"Entering the code {sum} in the combination lock")  
	params = {"solution": sum}  
	resp = requests.get(baseUri + "duo/combination_lock", params=params, headers=apiKey)  
	assert resp.ok  
	global solution1  
	solution1 = resp.headers.get('solution1')
	
// at the end of the file
enter_combination_lock()
```


[Next](../05.%20puzzle4.md)
