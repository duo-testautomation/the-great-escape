[Back](../05.%20puzzle4.md)

### Solution using Python
```python
def enter_towers_correct_order():  
	endpoint = baseUri + "duo/towers"  
	headers = apiKey.copy()  
	headers.update({"solution1": solution1})  
	  
	solution_resp = requests.post(endpoint, headers=headers, json=towers)  
	if not solution_resp.ok:  
	print("Sorting not correct, reason:")  
	print(solution_resp.text)  
	global solution2  
	solution2 = solution_resp.headers.get('solution2')  
	global tools  
	tools = solution_resp.json().get('tools')
	
// at the end of the file
enter_towers_correct_order()
```

[Next](../06.%20puzzle5.md)
