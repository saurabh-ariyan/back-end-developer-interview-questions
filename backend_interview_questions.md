### <a name="general"> General Questions</a>

    - What happens when I type into my browser address medium.com? How does the request reach the server, and how does it go back? Granularity is as small as possible.
    - What is the difference between TCP and UDP? In which case is UDP preferred?
    - Is it possible to kill a thread inside a specific process with the kill command?
    - How can I sort a file by 100GB, in which the numbers are arranged in random order, by 1 number per line? Limitations — the amount of RAM on the machine is 1GB.
    - What is your favorite technology (can it be a database, a queue server, a library — anything)? And why?
    - What decisions would you make as a technical director at your current / past job?
    - What topic would you like to discuss?

### <a name="ms"> microservices </a>

    - What do you think are microservices?
    - What advantages do you see in microservice architecture in comparison with monolith? And what are the disadvantages?
    - What difficulties have you encountered in building a microservice architecture?
    - What have you used (or heard about) to trace services? For monitoring? And for logging?
    - How to deal with the consistency of data between several microservices?

### <a name="devops"> infrastructure and deployment </a>

    - What is blue-green deployment?
    - What was the process of deployment in your current (or previous) place of work? What disadvantages do you see in this approach?
    - Have you worked in CI/CD system before?
    - What tasks the container orchestration systems solve?

### <a name="dbms"> caching and databases </a>

    - What problems in data caching did you encounter?
    - How would you solve a problem when at the same time many clients do not receive data from the cache, and all of them go to the master data source at the same time (for example, to the database)?
    - What are the pros and cons of relational DBMS in comparison with NoSQL solutions? In which case would you prefer to choose NoSQL? What NoSQL solutions did you work with? And what difficulties did you encounter while working with these solutions?

### <a name="golang"> golang </a>

    - What is the string data type in the Golang language? Can I change a specific character in a string?
    -  What happens when concatenating strings?
    — how to effectively concatenate a lot of strings?
    ```While Go does allow you to concatenate strings with the + operator, this can become pretty inefficient when concatenating a lot of strings together.
        You can also use the strings.Join function if you have all of the strings ahead of time.
        It is much more efficient to use a bytes.Buffer and then convert it to a string once you have concatenated everything.
        ```
    - What will happen when a concurrect map write occurs? How can this problem be solved?
        ```Control access to the map with sync.RWMutex{}. Use this option if you have single reads and writes, not loops over the map
        ```
    - Should I lock a structure with a mutex if there is a concurrent write in a different fields of the struct?
