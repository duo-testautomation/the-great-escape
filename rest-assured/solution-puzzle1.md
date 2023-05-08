[Back](../02.%20puzzle1.md)
### Solution using Rest Assured Puzzle number 1
In this example solution we used a maven project with the following dependencies:

- junit
- rest-assured
- jackson-databind

You can create a java class and name it Escapi, in where you can code the rest assured solution.
The sample solution for this puzzle is:

```java
import io.restassured.response.Response;  
import org.junit.Before;  
import org.junit.Test;  
  
import static io.restassured.RestAssured.*;  
  
  
public class Escapi {  
  
    String apikey = "<replace-by-your-api-key>";  
    int sumSolution;  
  
  // set the baseuri for every test
    @Before  
  public void setup() {  
        baseURI = "https://ta-workshop.nl/duo";  
    }  
  
  // from here you can run your solution
    @Test  
  public void ecapeTheApi() {  
        start();  
    }  
  
  // the actual request
    private void start() {  
        Response startCallResponse =  
                given().  
                        // logs the request in the console  
  log().all().  
                        header("apikey", apikey).  
                        when().  
                        // combines the baseURI with /api and makes a GET request  
  get("/start").  
                        then().  
                        // logs the response in the console  
  log().all().  
                        // validates that that the statuscode from the respons is 200  
  statusCode(201).  
                        // checks if the body contains a gender node with value female  
  extract()  
                        // this will save the response in the exampleRequest variable  
  .response();  
        // extract the needed values from the response  
  int number1 = startCallResponse.jsonPath().get("sum.number1");  
        int number2 = startCallResponse.jsonPath().get("sum.number2");  
        if (startCallResponse.jsonPath().get("divide")) {  
            sumSolution = number1 / number2;  
        } else if (startCallResponse.jsonPath().get("add")) {  
            sumSolution = number1 + number2;  
        } else if (startCallResponse.jsonPath().get("multiply")) {  
            sumSolution = number1 * number2;  
        } else {  
            sumSolution = number1 - number2;  
        }  
        // prints output to the console  
  System.out.println("The solution should be: " + sumSolution);  
    }  
      
}
```

[Next](../03.%20puzzle2.md)
