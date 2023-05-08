[Back](../05.%20puzzle4.md)

### Solution using Cypress Puzzle number 4
 ```typescript
  // Add these to the rest of the variables, or leave them here	
  let solution2  
  let specialist_number

     it("should solve tower puzzel", () => {
     // add the solution1 header 
	 // send the towers object in the body section
        cy.request({
            method: 'post', url: `/duo/towers`,
            headers: {
                'apikey': apiKey,
                'solution1': solution1
            }, body: towers
        }).then((response) => {
            expect(response.status).to.eq(200)
            // get the solution2 header from this response   
            solution2 = response.headers['solution2'];
            const tools: string[] = response.body.tools 
            // check which tool is missing and store the according number   
            if (!tools.includes('Playwright')) {
                console.log('Missing tool: Playwright')
                specialist_number = 587426 //Jurian
            } else if (!tools.includes('Postman')) {
                console.log('Missing tool: Postman')
                specialist_number = 32843 // David
            } else if (!tools.includes('Cypress')) {
                console.log('Missing tool: Cypress')
                specialist_number = 7346337 //Reinder
            } else if (!tools.includes('Python')) {
                console.log('Missing tool: Python')
                specialist_number = 6278456 //Martijn
            } else {            
                console.log('Missing tool: Java')
                specialist_number = 527786 //Jarsto
            }
            console.log('Number to be called: ' + specialist_number)
        })
    })
 ```

[Next](../06.%20puzzle5.md)
