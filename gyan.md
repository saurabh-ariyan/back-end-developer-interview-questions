# Things to keep in mind when building for production 


## Start from these: 
-  Database Defaults: Each of the schema value in the your schema design should have proper and sensible defaults. 
-  Database values should always have single source of truth, updating one should ideally update this value's reference at all places it is fetched. 

-  Your whole backend and front end should work perfectly on an empty db. *Test this* . 
   - This means you might get an empty drop down somewhere. 
   - This also means your forms might give validation error as they don't get all the data to post.
   - But you should not get any 5xx errors. 
   - Any processing you're doing on the db data, is not assuming the db data to be there in all cases. 
   - Do not limit this to the database defaults. If you're looking for an image and the image is not found, your system should not give a 5xx error but should generate the output with sensible defaults. Or give a handled error. 
   
-  Develop with dummy data, visibliy dummy data. *no accidents* 
   - valid emails in the development db can recieve your development emails, accidently. 
-  Values which are configration depenedent should be defined in a seperate file. *staging url*

-  API calls should ideally do one thing + error handling that one thing. 
   - DB fetch should also be an API call. 
   - Error handle the record not being there. 
   - Error handling of a variable in that record should not be in the DB fetch API but the API which processes this. 

-  Use `GET` when you can say what you want in the terms of "get me x"
-  getters API should always support commonly used filters: paging the result by count, etc. 
-  API response should support additional metadata and namespaces. 
   - GET /users/:id
   ```
        {
          "data": {
            "name": "Phil Sturgeon",
            "id": "511501255"
            }
          }
   ```
   - GET /users
   ```
          {
          "count" : 2
          "data": [
             {"name": "Hulk Hogan",
             "id": "100002"
            },
            {"name": "Mick Foley",
            "id": "100003"
            }
            ]
         }
     ``` 

-  auto increment ids make things public which you may not want.
-  mongo id doesn't look good on display. use short-id?


## API Error Messages and Error Codes :
- Error messages are for the end user, the customer, should be things they can understand. 
- Error Codes are for the application to decide what to do next. 
- Both Error codes and error messages are different from the HTTP error codes. These error codes can be anything you decide and are closely tied with your appication. 
- The error message is almost necessary for any application, having a error code along with it helps in doing conditionals.
- Changing error messages should not break the code in any place. (No conditional checking on the message itself)
    - Twitter example:
     ```
     {"errors":[{"message":"Sorry, that page does not exist","code":34}]}

     ```
    Example Twitter Error code for HTTP error 404 :
     
     
| Error Codes | Error                                                                        | Error Message                                                                 |
|-------------|------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| 17          | No user matches for specified terms                                          | It was not possible to find a user profile matching the parameters specified. |
| 34          | The specified resource was not found                                         | Sorry, that page does not exist                                               |
| 144         | The requested Tweet ID is not found (if it existed, it was probably deleted) | This tweet cannot be found                                                    |

- Error codes and the message should be handled in a single function. Call this helper function with arguments for the error code and the messages are only written in this fuction. So when the messages need to change they can change at only one place. 



## What goes where? Frontend or backend: 
- In most cases, especiallly apps, I've found changing the backend will be way easier. 
