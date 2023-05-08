[Back](../05.%20puzzle4.md)

###  Solution using Playwright
```typescript
// Add these to the class variables, or leave them here
let solution2  
let specialist_number

test('should solve tower puzzle', async ({request}) => { 
// add the solution1 header 
// send the towers object in the data section
    const response = await request.post(`/duo/towers`, {  
        data: towers, headers: {'solution1': solution1}  
    });  
    expect(response.ok()).toBeTruthy();  
    //using text to make it easier to check for missing value  
    const responseAsJson = JSON.stringify(await response.text()) 
    // get the solution2 header from this response   
    solution2 = await response.headers().solution2;    
    console.log('Solution2 header found: ' + solution2)  
  
  // check which tool is missing and store the according number
    if (!responseAsJson.includes('Playwright')) {  
        console.log('Missing tool: Playwright')  
        specialist_number = 587426 //Jurian  
  } else if (!responseAsJson.includes('Postman')) {  
        console.log('Missing tool: Postman')  
        specialist_number = 32843 // David  
  } else if (!responseAsJson.includes('Cypress')) {  
        console.log('Missing tool: Cypress')  
        specialist_number = 7346337 //Reinder  
  } else if (!responseAsJson.includes('Python')) {  
        console.log('Missing tool: Python')  
        specialist_number = 6278456 //Martijn  
  } else {       
	    console.log('Missing tool: Java')  
        specialist_number = 527786 //Jarsto  
  }  
    console.log('Number to be called: ' + specialist_number)  
});
```

[Next](../06.%20puzzle5.md)
