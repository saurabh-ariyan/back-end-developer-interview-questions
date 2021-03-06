# Full Stack Developer Interview Questions

This is a living and breathing document and generally works as a agenda for my interviews. The updation are intended to be frequent.
Apart from the language section the document is intended to be as language, hence framework, agnositic as possible.

## <a name="toc">Table of Contents</a>

- [General Questions](#general)
- [Design Pattern Questions](#dpspecific)
- [JS Code examples](#jscodeexamples)
- [JS Specific Questions](#jsspecific)
- [Database Specific Questions](#databasespecific)
- [Operating System Specific Questions](#osespecific)
- [Web Services Specific Questions](#webservicesespecific) \* [Common Server Response Codes](#csrcspecific)
- [Network Specific Questions](#networkspecific)

**[[⬆]](#toc) return to Table of Contents**

### <a name="general">General Questions</a>

- What did you learn yesterday/this week? Or most recently?
- How do you go about testing your JS code?
- What are the common libraries or frameworks you use for end to end developemnet? :

      	ideally should include server framework, front end framework, db orm, db manipulations , deployment tech, cache handling, testing, logging and error reporting.

- When do you optimize your code? What kind of process you follow for it? :

      	should include some kind of perf monitorining.

- What's the most recent big problem faced on your current projects and how did you solve it? Should be in last 2 weeks.
- What do you consider one of your failures in your current job?

**[[⬆]](#toc) return to Table of Contents**

### <a name="dpspecific"> System Design Pattern</a>

**[[⬆]](#toc) return to Table of Contents**

### <a name="jscodeexamples">JS Code Examples:</a>

What is the output here? Why?

```var text = 'outside';
function logIt(){
    console.log(text);
    var text = 'inside';
};
logIt();
```

Output will be `undefined`. Variable declarations are hoisted only not the assignemts.

```
<button id="btn-0">Button 1</button>
<button id="btn-1">Button 2</button>
<button id="btn-2">Button 3</button>

<script type="text/javascript">
  const prizes = ['A Unicorn!', 'A Hug!', 'Fresh Laundry!'];
  for (var btnNum = 0; btnNum < prizes.length; btnNum++) {

    // For each of our buttons, when the user clicks it...
    document.getElementById(`btn-${btnNum}`).onclick = () => {

      // Tell her what she's won!
      alert(prizes[btnNum]);
    };
  }
</script>
```

The loop does not stop until btnNum = 3. The inner function gets the value of btnNum 3 always as the btnNumber is not passed to the onClick function. It will always `alert(prize[3])` hence `undefined`

1. What does the code snippet prints?

```js
(function() {
  var a = (b = 3);
})();

console.log("a defined? " + (typeof a !== "undefined"));
console.log("b defined? " + (typeof b !== "undefined"));
```

Output:

```
//a defined? false
//b defined? true
//b = 3;
//var a = b;

```

2. Write the function which prints the following output.

```JS

console.log(mul(2)(3)(4)); // output : 24
console.log(mul(4)(3)(4)); // output : 48
```

Below is code followed by an explanation how it works:

```js
function mul(x) {
  return function(y) {
    // anonymous function
    return function(z) {
      // anonymous function
      return x * y * z;
    };
  };
}
```

3. What is the difference between the following code samples?

```js
var foo = function() {
  // Some code
};
function bar() {
  // Some code
}
```

4. What will the following code output?

```js
const arr = [10, 12, 15, 21];
for (var i = 0; i < arr.length; i++) {
  setTimeout(function() {
    console.log("Index: " + i + ", element: " + arr[i]);
  }, 3000);
}
```

It outputs `Index : 4 , element : undefined`.

5. How would you change the above snippet to make it print logically?

- ES6 way:

```js
const arr = [10, 12, 15, 21];
for (let i = 0; i < arr.length; i++) {
  // using the ES6 let syntax, it creates a new binding
  // every single time the function is called
  // read more here: http://exploringjs.com/es6/ch_variables.html#sec_let-const-loop-heads
  setTimeout(function() {
    console.log("The index of this number is: " + i);
  }, 3000);
}
```

- other way

```js
const arr = [10, 12, 15, 21];
for (var i = 0; i < arr.length; i++) {
  // pass in the variable i so that each function
  // has access to the correct index
  setTimeout(
    (function(i_local) {
      return function() {
        console.log("The index of this number is: " + i_local);
      };
    })(i),
    3000
  );
}
```

6.  Write the function which prints the following output.

```js
var addSix = createBase(6);
addSix(10); // returns 16
addSix(21); // returns 27
```

7. The primitive types are stored as the value themselves, unlike objects, which are stored as a reference. This has implications when performing equality checks.

```
"dog" === "dog"; // true
14 === 14; // true

{} === {}; // false
[] === []; // false
(function () {}) === (function () {}); // false
```

8. A function is a special type of object, with some special properties, such as constructor and call.

```
const foo = function (baz) {};
foo.name; // "foo"
foo.length; // 1
```

And just like a normal objects, you can add new properties to the object:

```
foo.bar = "baz";
foo.bar; // "baz"
```

This makes functions a first-class citizen, because it can be passed around, as arguments into other functions, just like any other objects could.

Methods: A method is a object property that also happens to be a function.

**[[⬆]](#toc) return to Table of Contents**

### <a name="jsspecific">JS Specific Questions</a>

- Describe two good uses - and pratices - for callback usage.
- what is mixin ? : Diamond Problem : make a seperate class for the things that you need in other classes.
- How to defer javascript loading on the frontend?
- What is the default return value of js fuction when no return has been explicitly defined.
- What is `self`? Why we need it seperately from `this`?
- What is annonymous functions and why we need them? (deceration at run time or complie time)

**[[⬆]](#toc) return to Table of Contents**

### <a name="databasespecific">Database Specific Questions</a>

- What is the use case of noSQL and SQL databases?
- Have you worked with an in-memory db? What are your common concerns there?
- Have you worked on production deployed MongoDb?
  _ Have you managed a replica set?
  _
- Do you know PostgreSQL? \* How do you improve [Resource Consumption](http://www.postgresql.org/docs/current/static/runtime-config-resource.html)?
- SQL Server \* How would you migrate from SQL Server to PostgreSQL or MySQL?
- Do you know How to 'hack', build a cluster, improve performance, implement cache, pooling or compile those services from source?
- Are you familiar with NoSQL databases?

**[[⬆]](#toc) return to Table of Contents**

### <a name="httpspecific">HTTP Specific Questions</a>

- What happens between the time you enter a URL in your browser until you see the page that you requested?
- How does the 3-way TCP handshake occur when you request a page from a server?
- What are the contents of an HTTP request header? Response header?
- What is the difference between HTTP and HTTPS?
- How would you design a URL shortener similar to bit.ly?

**[[⬆]](#toc) return to Table of Contents**

### <a name="ormspecific">ORM Specific Questions</a>

**[[⬆]](#toc) return to Table of Contents**

### <a name="webservicesespecific">Web Services Specific Questions</a>

- Have you created or managed some web service?
- What web service protocals do you know?

**[[⬆]](#toc) return to Table of Contents**

### <a name="osespecific">Operating System Specific Questions</a>

- Linux/Unix/MacOS
  _ How would you install, configure and handle services such nginx, apache, squid, samba, etc..?
  _ What do you know about kernel tuning?
  _ What do you know about virtualization?
  _ What is the difference between threads and processes?

**[[⬆]](#toc) return to Table of Contents**

### <a name="networkspecific">Network Specific Questions</a>

- What are the 7 layers of the OSI model?
- What are some advantages of CDNs? Disadvantages?
- What is a reverse proxy?
- What ports do the following use?
  _ HTTP
  _ HTTPS \* SSH

**[[⬆]](#toc) return to Table of Contents**

```
SELECT subQuery.condition, max(subQuery.severity) as severity,
                    json_agg(json_build_object(
                        'vulnerability', subQuery.vulnerability,
                        'asset', subQuery.asset,
                        'severity', subQuery.severity
                        )) AS asset
                    FROM (
                        SELECT author.genre, author.name,
                        books.title, author.title
                        FROM author inner join books
                        on books.if = author.book-id
                        )subQuery
                    GROUP BY subQuery.genre
```

```
author
    genre
    name
    book-id(fk)

books
   id
   title
   author(fk)
```

class Musician(models.Model):
first_name = models.CharField(max_length=50)
last_name = models.CharField(max_length=50)
instrument = models.CharField(max_length=100)

class Album(models.Model):
artist = models.ForeignKey(Musician, on_delete=models.CASCADE)
name = models.CharField(max_length=100)
release_date = models.DateField()
num_stars = models.IntegerField()
