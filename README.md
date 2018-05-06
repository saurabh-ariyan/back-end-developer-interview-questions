Full Stack Developer Interview Questions
======================================

This is a living and breathing document and generally works as a agenda for my interviews. The updation are intended to be frequent. 
Apart from the language section the document is intended to be as language, hence framework, agnositic as possible. 



## <a name="toc">Table of Contents</a>
* [General Questions](#general)
* [Design Pattern Specific Questions](#dpspecific)
	* [MVC](#mvcspecific)
	* [MVVM](#mvvmspecific)
	* [Repository](#repospecific)
	* [Dependency Injection](#dispecific)
	* [Visitor](#vspecific)
* [JS Code examples](#jscodeexamples)
* [JS Specific Questions](#jsspecific)
* [Database Specific Questions](#databasespecific)
* [ORM Specific Questions](#ormspecific)
	* [Doctrine](#doctrine)
* [HTTP Specific Questions](#httpspecific)
* [Operating System Specific Questions](#osespecific)
* [Web Services Specific Questions](#webservicesespecific)
	* [Common Server Response Codes](#csrcspecific)
* [Network Specific Questions](#networkspecific)

**[[⬆]](#toc) return to Table of Contents**

### <a name="general">General Questions</a>

* What did you learn yesterday/this week? Or most recently?
* How do you go about testing your JS code?
* Have you ever looked at the source code of the libraries/frameworks you use?
* When do you optimize your code?
* What's the biggest problem faced on your projects and how did you solve it?
* What do you consider one of your failures in your current job?

**[[⬆]](#toc) return to Table of Contents**

### <a name="dpspecific">Design Pattern Specific Questions</a>

* <a name="mvcspecific">MVC</a>
    * Question: In the MVC design pattern what's M stands for? **Answer: M stands for Model, it is the data and data-management of the application.** 
* <a name="mvvmspecific">MVVM</a>
* <a name="repospecific">Repository</a>
* <a name="dispecific">Dependency Injection</a>
* <a name="vspecific">Visitor</a>
    * The classes and/or objects participating in this pattern are? **Answer: Visitor, ConcreteVisitor, Element, ConcreteElement, ObjectStructure** 

**[[⬆]](#toc) return to Table of Contents**

### <a name="jscodeexamples">JS Code Examples:</a>

```js
(function(){
  var a = b = 3;
})();

console.log("a defined? " + (typeof a !== 'undefined'));
console.log("b defined? " + (typeof b !== 'undefined'));

//a defined? false
//b defined? true
//b = 3;
//var a = b;

```


```JS

console.log(mul(2)(3)(4)); // output : 24
console.log(mul(4)(3)(4)); // output : 48
```
Below is code followed by an explanation how it works:

```js
function mul (x) {
  return function (y) { // anonymous function
    return function (z) { // anonymous function
      return x * y * z;
    };
  };
}

```

**[[⬆]](#toc) return to Table of Contents**

### <a name="jsspecific">JS Specific Questions</a>

* Describe two good uses - and pratices - for callback usage.

**[[⬆]](#toc) return to Table of Contents**

### <a name="databasespecific">Database Specific Questions</a>
* What is the use case of noSQL and SQL databases? 
* Have you worked with an in-memory db? What are your common concerns there?
* Have you worked on production deployed MongoDb? 
	* Have you managed a replica set?
	* 
* Do you know PostgreSQL?
	* How do you improve [Resource Consumption](http://www.postgresql.org/docs/current/static/runtime-config-resource.html)?
* SQL Server
	* How would you migrate from SQL Server to PostgreSQL or MySQL?
* Do you know How to 'hack', build a cluster, improve performance, implement cache, pooling or compile those services from source?
* Are you familiar with NoSQL databases?

**[[⬆]](#toc) return to Table of Contents**

### <a name="httpspecific">HTTP Specific Questions</a>

* What happens between the time you enter a URL in your browser until you see the page that you requested?
* How does the 3-way TCP handshake occur when you request a page from a server?
* What are the contents of an HTTP request header? Response header?
* What is the difference between HTTP and HTTPS?
* How would you design a URL shortener similar to bit.ly?

**[[⬆]](#toc) return to Table of Contents**

### <a name="ormspecific">ORM Specific Questions</a>

**[[⬆]](#toc) return to Table of Contents**

### <a name="webservicesespecific">Web Services Specific Questions</a>

* Have you created or managed some web service?
* What web service protocals do you know?

#### <a name="csrcspecific">Common Server Response Codes</a>

Question: Describe server response code 200. **Answer: ("OK") Evertying went ok. The entity-body, if any, is a representation of some resource.**

Question: Describe server response code 201. **Answer: ("Created") A new resource was created at the client's request. The location header should contain a URI to the new resource and the entity-body should contain a representation of the newly created resource.**

Question: Describe server response code 204. **Answer: ("No Content") The server declined to send back any status message or representation**

Question: Describe server response code 301. **Answer: ("Moved Permanently") Client triggered an action on the server that caused the URI of a resource to change.**

Question: Describe server response code 400. **Answer: ("Bad Request") A problem occured on the client side. The entity-body, if any, is a error message.**

Quesiton: Describe server response code 401. **Answer: ("Unauthorized") The client faild to provide proper authentication for the requested resource.**

Question: Descibe server response code 404. **Answer: ("Not Found") Client requested a URI that doesn't map to any resource.**

Question: Describe server response code 409. **Answer: ("Conflict") Client attempted to put the servers resource into a impossable or inconsistant state.**

Question: Descibe server response code 500 **Answer: ("Internal Server Error") A problem occured on the server side. The entity-body, if any, is a error message.**

**[[⬆]](#toc) return to Table of Contents**

### <a name="osespecific">Operating System Specific Questions</a>

* Linux/Unix/MacOS
	* How would you install, configure and handle services such nginx, apache, squid, samba, etc..?
	* What do you know about kernel tuning?
	* What do you know about virtualization?
	* What is the difference between threads and processes?

**[[⬆]](#toc) return to Table of Contents**

### <a name="networkspecific">Network Specific Questions</a>

* What are the 7 layers of the OSI model?
* What are some advantages of CDNs? Disadvantages?
* What is a reverse proxy?
* What ports do the following use?
	* HTTP
	* HTTPS
	* SSH

**[[⬆]](#toc) return to Table of Contents**
