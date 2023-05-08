[Back](../03.%20puzzle2.md)

### Solution using Python Puzzle number 2
Here you can create your own towers class to get the right order. The towers class used in this example look like this:
**Towers.py**
```python
class Tower(object):  
  
def __init__(self, name, height, construction_year):  
self.name = name  
self.height = height  
self.construction_year = construction_year  
  
  
martiniToren = Tower("martinitoren", 96.8, 1469)  
derAa = Tower("aKerk", 76, 1492)  
nieuweKerk = Tower("nieuweKerk", 47, 1660)  
stJozef = Tower("stJozefKerk", 75, 1887)  
academieGebouw = Tower("academiegebouw", 65.5, 1909)  
  
all_towers = [martiniToren, derAa, nieuweKerk, stJozef, academieGebouw]  
  
  
def sort_towers(tower_resp):  
def sort_alfa(item):  
return str(item.name).lower()  
  
def sort_height(item):  
return item.height  
  
def sort_year(item):  
return item.construction_year  
  
sort_method = ""  
  
if tower_resp.get('alphabetic'):  
all_towers.sort(key=sort_alfa)  
sort_method = "alphabetically"  
elif tower_resp.get('height'):  
all_towers.sort(key=sort_height)  
sort_method = "by height"  
elif tower_resp.get('constructionYear'):  
all_towers.sort(key=sort_year)  
sort_method = "by year of construction"  
  
print(f"Sorting the towers {sort_method}")  
  
data = {  
"aKerk": all_towers.index(derAa),  
"academieGebouw": all_towers.index(academieGebouw),  
"martini": all_towers.index(martiniToren),  
"nieuweKerk": all_towers.index(nieuweKerk),  
"stJozefKerk": all_towers.index(stJozef)  
}  
print(f"towers sorted:")  
return data
```
With that in place you can add the following code to the main.py file
```python
def get_towers_assigment():  
	print("Looking at the towers")  
	endpoint = baseUri + "duo/towers"  
	tower_resp = requests.get(endpoint, headers=apiKey)  
	assert tower_resp.ok  
	global towers  
	towers = Towers.sort_towers(tower_resp.json().get('towers'))
	
// at the end of the file
get_towers_assigment()
```

[Next](../04.%20puzzle3.md)
