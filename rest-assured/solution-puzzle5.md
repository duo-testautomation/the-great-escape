[Back](../06.%20puzzle5.md)

### Solution using Rest Assured
```java
// add this variable
int escapeCode;

    @Test
    public void ecapeTheApi() {
        start();
        towersGet();
        combinationLock();
        towersPost();
        // only add the new method
        toolSupport();     
    }
    
    private void toolSupport() {
        Response toolsupport =
                given().
                        log().all().
                        header("apikey", apikey).
                        header("solution2", solution2Header).
                        pathParam("specialistNumber", specialistNumber).
                when().
                        get("/tool_support/call_specialist/{specialistNumber}").
                then().
                        log().all().
                        statusCode(200).
                extract()
                        .response();

        escapeCode = toolsupport.jsonPath().get("escapecode");
        System.out.println("The escapecode is: " + escapeCode);
    }
```

[Next](../07.%20puzzle6.md)
