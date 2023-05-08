[Back](../07.%20puzzle6.md)

###  Solution using Cypress
```typescript
it("should escape", () => {  
    cy.request({  
        method: 'delete', url: `/duo/remove_lock/${escapeCode}`,  
        headers: {  
            'apikey': apiKey  
  }  
    }).then((response) => {  
        expect(response.status).to.eq(200)  
        console.log(response.body)  
    })  
})
```
When you got the last one right, run the complete set to be able to escape within 5 seconds!

[Next](../08.%20end.md)
