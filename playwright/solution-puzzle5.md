[Back](../06.%20puzzle5.md)

###  Solution using Playwright Puzzle number 5
```typescript
 // Add this to the class variables, or leave it here
let escapeCode

test('should solve tool puzzle', async ({request}) => {  
	// add the solution2 header
    const response = await request.get(`/duo/tool_support/call_specialist/${specialist_number}`
    ,{headers: {'solution2': solution2}});  
      
    expect(response.ok()).toBeTruthy();  
    const responseAsJson = await response.json()
    // extract the escapecode     
    escapeCode = responseAsJson.escapecode;  
  
    console.log('EscapeCode is : ' + escapeCode)  
});
```

[Next](../07.%20puzzle6.md)
