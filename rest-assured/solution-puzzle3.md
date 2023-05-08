[Back](../04.%20puzzle3.md)

### Solution using Rest Assured Puzzle number 3
```java
// add this variable
String solution1Header;

    @Test
    public void ecapeTheApi() {
        start();
        towersGet();
        //only add the new method
        combinationLock();      
    }

  private void combinationLock() {
        Response combinationLockRespons =
                given().
                        log().all().
                        header("apikey", apikey).
                        queryParam("solution", sumSolution).
                 when().
                        get("/combination_lock").
                 then().
                        log().all().
                        statusCode(200).
                 extract()
                        .response();

        solution1Header = combinationLockRespons.header("solution1");
        System.out.println("The solutionHeader for puzzle 1: " + solution1Header);
    }
```


[Next](../05.%20puzzle4.md)
