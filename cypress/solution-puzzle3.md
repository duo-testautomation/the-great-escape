[Back](../04.%20puzzle3.md)

### Solution using Cypress Puzzle number 3
Only thing to do with this request is using the answer variable which contains the right answer and use it in the request url. Then store the solution1 header in a new variable:
 ```typescript
 // Add this to the rest of the variables, or leave it here
let solution1

it("should solve math puzzel", () => {  
 // using backticks gives you the options to use a variable in a string like this:
    cy.request({  
        method: 'GET', url: `/duo/combination_lock?solution=${answer}`,  
        headers: {  
            'apikey': apiKey  
  }  
    }).then((response) => {  
        expect(response.status).to.eq(200)  
        // extract the solution1 response header
        solution1 = response.headers['solution1'];  
  
        console.log('Solution1 header found: ' + solution1)  
    })  
})
```

[Next](../05.%20puzzle4.md)
