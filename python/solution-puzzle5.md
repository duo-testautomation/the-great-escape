[Back](../06.%20puzzle5.md)

### Solution using Python Puzzle number 5
```python
toolMap = {  
"Postman": 32843,  
"Playwright": 587426,  
"Java": 527786,  
"Cypress": 7346337,  
"Python": 6278456,  
}  
  
  
def find_phone_number():  
	for tool, number in toolMap.items():  
	if tool not in tools:  
	return number  
  
  
def call_specialist():  
	phone_number = find_phone_number()  
	header = apiKey.copy()  
	header.update({"solution2": solution2})  
	print(f"Calling the specialist on {phone_number}")  
	resp = requests.get(baseUri + "duo/tool_support/call_specialist/" + str(phone_number), headers=header)  
	assert resp.ok  
	global escapecode  
	escapecode = resp.json().get('escapecode')
	
// at the end of the file add
call_specialist()
```

[Next](../07.%20puzzle6.md)
