[Back](../07.%20puzzle6.md)

###  Solution using Playwright
```typescript 
test('should escape', async ({request}) => {  
    const response = await request.delete(`/duo/remove_lock/${escapeCode}`);  
    expect(response.ok()).toBeTruthy();  
    const responseAsJson = await response.json()  
    console.log(responseAsJson)  
}); 
```
When you got the last one right, run the complete set to be able to escape within 5 seconds!

[Next](../08.%20end.md)
