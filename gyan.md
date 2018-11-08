# Things to keep in mind when building for production 


## Start from these: 
-  Database Defaults: Each of the schema value in the your schema design should have proper and sensible defaults. 
-  Database values should always have single source of truth, updating one should ideally update this value's reference at all places it is fetched. 

-  Your whole backend and front end should work perfectly on an empty db. *Test this* . 
   - This means you might get an empty drop down somewhere. 
   - This also means your forms might give validation error as they don't get all the data to post.
   - But you should not get any 5xx errors. 
   - Any processing you're doing on the db data, is not assuming the db data to be there in all cases. 
   
   
   
-  Develop with dummy data, visibliy dummy data. *no accidents* 
   - valid emails in the development db can get emails, accidently. 
-  Values which are configration depenedent should be defined in a seperate file. *staging url*

-  API calls should ideally do one thing + error handling that one thing. 
   - DB fetch should also be an API call. 
   - Error handle the record not being there. 
   - Error handling of a variable in that record should not be in the DB fetch API but the API which processes this. 


-  getters API should always support commonly used filters: paging the result by count, etc. 
-  Use `GET` when you can say what you want in the terms of "get me x"
-  auto increment ids make things public which you may not want.
-  mongo id doesn't look good on display. use short-id?


## API Error Messages and Error Codes :
- Error messages are for the end user, the customer, should be things they can understand. 
- Prefer all the error messages being displayed at one place, either front end or backend, whichever is easier to change. 
- Error Codes are for the application to decide what to do next. 
- Error codes for handled errors and unhandled errors can be 




## What goes where? Frontend or backend: 
- In most cases, especiallly apps, I've found changing the backend will be way easier. 
