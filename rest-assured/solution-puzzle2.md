[Back](../03.%20puzzle2.md)

### Solution using Rest Assured Puzzle number 2
For this solution I have chosen to create a java class which represents the towers. I made a class in the same dir as the test and named it **towers.java** with this content:
 ```java
 public class Towers {
    int aKerk;
    int academieGebouw;
    int martini;
    int nieuweKerk;
    int stJozefKerk;

    public Towers(int aKerk, int academieGebouw, int martini, int nieuweKerk, int stJozefKerk) {
        this.aKerk = aKerk;
        this.academieGebouw = academieGebouw;
        this.martini = martini;
        this.nieuweKerk = nieuweKerk;
        this.stJozefKerk = stJozefKerk;
    }   
}
```

Then you can add the following code to the Escapi class:
```java
// add this variable
Towers towersSolution;  
String solution1Header;

@Test  
public void ecapeTheApi() {  
    start();
    // only add the new method  
    towersGet();  
}

// the new method to handle this request
private void towersGet() {  
    Response towersGetRespons =  
            given().  
                    log().all().  
                    header("apikey", apikey).  
                    when().  
                    get("/towers").  
                    then().  
                    log().all().  
                    statusCode(200).  
                    extract()  
                    .response();  
    // create tower answer  
  if (towersGetRespons.jsonPath().get("towers.alphabetic")) {  
        towersSolution = new Towers(1, 0, 2, 3, 4);  
    } else if (towersGetRespons.jsonPath().get("towers.height")) {  
        towersSolution = new Towers(3, 1, 4, 0, 2);  
    } else {  
        towersSolution = new Towers(1, 4, 0, 2, 3);  
    }  
}
```

[Next](../04.%20puzzle3.md)
