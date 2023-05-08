[Back](../02.%20puzzle1.md)

### Solution using Playwright
Working with playwright gives you the option to set a baseUrl and headers which will be added to every request playwright does. To use that add this to your `playwright.config.ts`
 ```json
 use: {   
  baseURL: 'https://ta-workshop.nl/duo',  
  extraHTTPHeaders: {  
    'apikey': '<replace-by-your-api-key>',  
  },  
},
```

Because this isnt a normal test and we need to make several api requests and handle their responses, you want to overide the default setting to run with multiple workers.  The reason for this is we want to run our test in a specific order, and when you are using multiple workers you might end up doing a request when you dont have the correct data to do it yet. So in the config chance the line which starts with
``workers: process.env.CI``  to ``workers: 1,``.

When you have that config in place you can let playwright do the work by making a new spec.ts file and insert this test:

```typescript
import {test, expect} from '@playwright/test';

// You need some class variables to store values you need in other tests
let number1  
let number2  
let answer

test('should start the room and get math assignment', async ({request}) => {  
	// the baseurl from the config will be used so we only need the last bit of the url
    const response = await request.get(`/start`);  
    expect(response.ok()).toBeTruthy();  
    // with .json() playwright gives you a json object you can use
    const responseAsJson = await response.json()  
	// so you can extract values likes this
    number1 = responseAsJson.sum.number1;  
    number2 = responseAsJson.sum.number2;  
    if (responseAsJson.divide) {  
        answer = number1 / number2;  
    } else if (responseAsJson.add) {  
        answer = number1 + number2;  
    } else if (responseAsJson.multiply) {  
        answer = number1 * number2;  
    } else {  
        answer = number1 - number2;  
    }  
    console.log('Answer puzzle 1: ' + answer)  
});
```
[Next](../03.%20puzzle2.md)
