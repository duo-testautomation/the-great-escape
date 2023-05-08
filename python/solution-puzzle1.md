[Back](../02.%20puzzle1.md)
### Solution using Python Puzzle number 1
In this example solution the `requests` library was used. You can install it with the following command:
``pip install requests``

After you finished every step you can execute your code to see if it works by pressing Shift+F10.

**main.py**
```python
import requests as requests

baseUri = "https://ta-workshop.nl/duo"
apiKey = {"apiKey": "<replace-by-your-api-key>"}

def calc_sum(resp_dict):
	print("Calculating correct code for combination lock")
	getal1 = resp_dict.get('sum').get('number1')
	getal2 = resp_dict.get('sum').get('number2')
	if resp_dict.get('divide'):
	return getal1 / getal2
	if resp_dict.get('add'):
	return getal1 + getal2
	if resp_dict.get('multiply'):
	return getal1 * getal2
	if resp_dict.get('subtract'):
	return getal1 - getal2
 
def start():  
	resp = requests.get(baseUri + "/start", headers=apiKey)  
	assert resp.ok  
	global sum  
	sum = int(calc_sum(resp.json()))  
	print(f"Combination lock code is {sum}")
	
// at the end of the file
start()
```

[Next](../03.%20puzzle2.md)
