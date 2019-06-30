# Things to keep in mind when building for production 
#### [Public APIs](https://public-apis.xyz/) is a good place to look for dummy data. 
### Read Before : 
[Microsoft API guidelines](https://github.com/Microsoft/api-guidelines/blob/vNext/Guidelines.md)

**_Disclamier: _** These are intended to very _opinionated_ checklist, primarily refelecting my battle stories. 
## Start from these: 

- Fail Loudly. 
- Fail Fast. 
- Handle Failure from being exposed to the client. 
----------------------------
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

-  API calls should ideally do one thing : error handling is also one thing, seperate it out in a function. 
   - DB fetch should also be an API call. 
   - Error handle the record not being there. 
   - Error handling of a variable in that record should not be in the DB fetch API but the API which processes this. 

-  Use `GET` when you can say what you want in the terms of "get me x"
-  For nested documents, filter can work great. So if `GET /tweets/` gets me a array of tweets with comments as foreign key then `GET /tweets?embed=comments` gets me the comments embedded in the tweets data array. 
-  getters API should always support commonly used filters: paging the result by count, etc. 
-  API response should not be expected in any particular order by default. Ordering if any should be passed as a argument in the url. 
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
- In most cases, especiallly apps, I've found modifying the backend once deployed will be way easier. 
- Frontend should ideally have everything you need to display an empty db.  
- Any counts of a list of items can be part of API response, helps in pagination, etc. 
- The structure in which data is displayed *need* not be same as in which it is sent from API. Last logged in : Yesterday, API response: datetime
- Error message dispalyed to the end user should be in the API response and not generated based on HTTP code or error code.
- Ideally even small dropdowns should be mapped to API calls. Any update in them can be handled easily. 
- Error messages can also be a json file that the front-end calls only one time when loading the site and stores in the front end based on the user preference of language. 
- Error messages in some use case in the front end also makes sense. Your server and the front end device may have the same amount of memory!

## Basics Security: 

- You don’t want to store credit card numbers, health data or passwords in plain text! If it comes out, and it will, you will loose all the goodwill you have created with your customer base. 
- If data is stored or transfered as plain text, if older/weaker encryption (please dont use md5 anymore) is used, or if data is decrypted carelessly, attackers can gain acces and exploit the data.
- Authentication :
  - if using JWT, ensure the ip address of the request and the ip address of the creator of session token is same?
  - the token timeout should be optimum based on your use case, keeping a small timeout makes the user choose a weaker password and a very long timeout should not make sense. Last use vs the generated token timeout seems preferable. 
  - use vulnerability detection services, synk.io or npm and yarn native service to keep a check on your package dependenices.
  - [good link](https://medium.com/@nodepractices/were-under-attack-23-node-js-security-best-practices-e33c146cb87d)



