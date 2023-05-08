[Back](../02.%20puzzle1.md)

### Solution using Cypress Puzzle number 1
Also cypress gives you the option to make use of a baseUrl. You can set this url in the `cypress.config.ts` for typescript or `cypress.config.js` if you use javascript.
Add this line in the e2e object of your config: `baseUrl: 'https://ta-workshop.nl/duo',`

When you have that config in place you can let cypress do the work by making a new cy.ts file and insert this test:
 ```typescript
 describe('automate the escape with cypress', () => {  
 // You need some class variables to store values you need in other tests
  const apiKey = '<replace-by-your-api-key>'  
  let number1  
  let number2  
  let answer  
  
  it("should start the room", () => {  
  // the baseurl from the config will be used so we only need the last bit of the url
        cy.request({  
            method: 'GET', url: '/start',  
            headers: {  
                'apikey': apiKey  
  }  
        }).then((response) => {  
            expect(response.status).to.eq(201) 
            // you have to use JSON.parse to create a json object from the response 			 
            const body = JSON.parse(response.body)  
            // So you can extract values like this
            number1 = body.sum.number1  
            number2 = body.sum.number2    
            if (body.divide) {  
                answer = number1 / number2;  
            } else if (body.add) {  
                answer = number1 + number2;  
            } else if (body.multiply) {  
                answer = number1 * number2;  
            } else {  
                answer = number1 - number2;  
            }    
            console.log('Answer puzzle 1: ' + answer)  
        })  
    })  
})
```
[Next](../03.%20puzzle2.md)
