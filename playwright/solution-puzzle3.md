[Back](../04.%20puzzle3.md)

### Solution using Playwright Puzzle number 3
Only thing to do with this request is using the answer variable which contains the right answer and use it in the request url. Then store the solution1 header in a new variable:
 ```typescript
 // Add this to the class variables, or leave it here
let solution1

 test('should solve math puzzle', async ({request}) => {  
    // using backticks gives you the options to use a variable in a string like this:
    const response = await request.get(`/duo/combination_lock?solution=${answer}`);  
    expect(response.ok()).toBeTruthy();  
    // extract the solution1 response header
    solution1 = await response.headers().solution1;  
    console.log('Solution1 header found: ' + solution1)  
});
```

[Next](../05.%20puzzle4.md)
