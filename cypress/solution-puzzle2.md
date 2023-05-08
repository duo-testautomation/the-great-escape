[Back](../03.%20puzzle2.md)

### Solution using Cypress Puzzle number 2
Using cypress I have chosen to make a json file for each of the three possibilities and put them in the fixtures folder. So I have 3 jsons and named them:

- alphabetic.json
- construction.json
- height.json

You can copy the content for these files from the previous section.
Then you can add this to your cy.ts file
 ```typescript
// Add these imports at the top of your file
const alphabetic = require('../fixtures/alphabetic.json')  
const height = require('../fixtures/height.json')  
const construction = require('../fixtures/construction.json')

// then within the describe add this variable
let towers;

// and this test
it("should get the towers assignment", () => {  
    cy.request({  
        method: 'GET', url: '/duo/towers',  
        headers: {  
            'apikey': apiKey  
  }  
    }).then((response) => {  
        expect(response.status).to.eq(200)  
        const body = JSON.parse(response.body)    
        if (body.towers.alphabetic) {  
            console.log('Alphabetic:');  
            towers = alphabetic  
		} else if (body.towers.height) {  
            console.log('Height:');  
            towers = height  
		} else {  
	        console.log('Construction year:');  
            towers = construction  
		}  
        console.log('Answer puzzle 2: ' + towers);  
    })  
})
```

[Next](../04.%20puzzle3.md)
