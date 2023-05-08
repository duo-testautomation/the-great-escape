[Back](../06.%20puzzle5.md)

###  Solution using Cypress Puzzle number 5
```typescript
 // Add this to the rest of the variables, or leave it here
let escapeCode

it("should solve tool puzzle", () => {  
// add the solution2 header
    cy.request({  
        method: 'GET', url: `/duo/tool_support/call_specialist/${specialist_number}`,  
        headers: {  
            'apikey': apiKey,  
            'solution2': solution2  
  }  
    }).then((response) => {  
        expect(response.status).to.eq(200)  
  
        const body = JSON.parse(response.body)  
        // extract the escapecode
        escapeCode = body.escapecode;  
  
        console.log('EscapeCode is : ' + escapeCode)  
    })  
})
```

[Next](../07.%20puzzle6.md)
