[Back](../07.%20puzzle6.md)

### Solution using Python
```python
def open_door():  
	print(f"The code for the door is {escapecode}")  
	print("Opening the door")  
	resp = requests.delete(baseUri + "duo/remove_lock/" + str(escapecode), headers=apiKey)  
	  
	if resp.ok:  
	print("Successfully escaped")  
	else:  
	print(resp)
	
// at the end of the file add
open_door()
```
Then press Shift+F10 to execute the python code

[Next](../08.%20end.md)
