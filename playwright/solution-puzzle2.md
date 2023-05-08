[Back](../03.%20puzzle2.md)

### Solution using Playwright Puzzle number 2
For this solution I have chosen to create a typescript class which represents the towers. I made a class in the same dir as the test and named it **towers.ts** with this content:
 ```typescript
 export class Towers{  
    aKerk: number;  
    academieGebouw: number;  
    martini: number;  
    nieuweKerk: number;  
    stJozefKerk: number;  
  
    constructor(aKerk: number, academieGebouw: number,
     martini: number, nieuweKerk: number, stJozefKerk: number) {  
        this.aKerk = aKerk;  
        this.academieGebouw = academieGebouw;  
        this.martini = martini;  
        this.nieuweKerk = nieuweKerk;  
        this.stJozefKerk = stJozefKerk;  
    }  
}
```

With that in place I added this test to the spec.ts file:
```typescript
// Add this to the class variables, or leave it here
let towers: Towers;

test('should get the towers assignment', async ({request}) => {  
    const response = await request.get(`/duo/towers`);  
    expect(response.ok()).toBeTruthy();  
    const responseAsJson = await response.json();   
    if (responseAsJson.towers.alphabetic) {  
        console.log('Alphabetic:');  
        towers = new Towers(1, 0, 2, 3, 4)  
    } else if (responseAsJson.towers.height) {  
        console.log('Height:');  
        towers = new Towers(3, 1, 4, 0, 2)  
    } else {  
        console.log('Construction year:');  
        towers = new Towers(1, 4, 0, 2, 3)  
    }  
    console.log('Answer puzzle 2: ' + JSON.stringify(towers));  
});
```

[Next](../04.%20puzzle3.md)
