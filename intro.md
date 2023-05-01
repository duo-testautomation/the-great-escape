# Automate the escape using Postman

If all goes well, you should now have a collection in Postman with requests for the following methods and endpoints:

- GET to /start
- GET to /towers
- GET to /combination_lock?solution=###
- POST to /towers
- GET to /tool_support/call_specialist/#####
- DELETE to /remove_lock/####

With these six steps/requests, it's possible to escape, but you need to share quite a bit of information between the different API calls, so it's never going to be possible to do this within the given five seconds. To succeed, we'll need to use some code to share the necessary data between the API calls.

In the following steps, we'll examine which data we'll need at a later time for each request, and of course, which data we need to use from a previous call.

Within Postman, it's relatively easy to use data (variables) back and forth between requests. We use Postman Variables for this purpose, which can be found on the Variables tab. This tab can be accessed by clicking on your Postman collection.

Before we start working on our requests, let's create two variables that each call will need:

- baseUrl
- apikey

For each request, the baseUrl is specified before the endpoint ("/start", "/towers", etc.). And each API call requires an apikey so that the API knows who sent the message.



> #### :keyboard: ***create variables***
> 
> If everything is set up correctly, you shouldn't see any variables yet on the Variables tab.
> 
> - Start by typing "Add new variable" and create a variable with the name "baseUrl".
> - For the current value, enter "https://escape.ta-workshop.nl/duo".
> - Create another variable with the name "apikey" and set its value to your own API key.


