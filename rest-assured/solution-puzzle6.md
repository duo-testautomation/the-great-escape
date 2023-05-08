[Back](../07.%20puzzle6.md)

### Solution using Rest Assured Puzzle number 6
```java
    @Test
    public void ecapeTheApi() {
        start();
        towersGet();
        combinationLock();
        towersPost();
        toolSupport();
        // and add the last one
        escapeTheRoom();
    }

    private void escapeTheRoom() {
        given().
                log().all().
                header("apikey", apikey).
                pathParam("escapecode", escapeCode).
        when().
                delete("/remove_lock/{escapecode}").
        then().
                log().all().
                statusCode(200);
    }
```
When you got the last one right, run the complete set to be able to escape within 5 seconds!

[Next](../08.%20end.md)
