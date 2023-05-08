[Back](../05.%20puzzle4.md)

### Solution using Rest Assured Puzzle number 4
```java
// add these variables
    String solution2Header;
    int specialistNumber;
    @Test
    public void ecapeTheApi() {
        start();
        towersGet();
        combinationLock();
        // only add the new method
        towersPost();
    }

private void towersPost() {  
    Response towersPostResponse =  
            given().  
                    log().all().  
                    header("apikey", apikey).  
                    header("solution1", solution1Header).  
                    contentType("application/json").  
                    body(towersSolution).  
            when().  
                    post("/towers").  
            then().  
                    log().all().  
                    statusCode(200).  
            extract()  
                    .response();  
    if (!towersPostResponse.asString().contains("Playwright")) {  
        specialistNumber = 587426; //Jurian  
  } else if (!towersPostResponse.asString().contains("Postman")) {  
        specialistNumber = 32843; // David  
  } else if (!towersPostResponse.asString().contains("Cypress")) {  
        specialistNumber = 7346337; //Reinder  
  } else if (!towersPostResponse.asString().contains("Python")) {  
        specialistNumber = 6278456; //Martijn  
  } else {  
        specialistNumber = 527786; //Jarsto  
  }  
    solution2Header = towersPostResponse.header("solution2");  
    System.out.println("The solutionHeader for puzzle 1: " + solution2Header);  
}
```

[Next](../06.%20puzzle5.md)
