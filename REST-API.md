# ## Things I want to know more about

* Classes:

Classes are a template for creating objects. They encapsulate data with code to work on that data.

* Defining classes:

It has two components:
 
1) class expressions 
2) class declarations.

Class declarations: To declare a class, you use the class keyword with the name of the class 
Like "Rectangle"
---
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}
---
* Hoisting:
difference between function declarations and class declarations is that while functions can be called in code that appears before they are defined,
 classes must be defined before they can be constructed.

Class expressions: Class expressions can be named or unnamed.
The name given to a named class expression is local to the class's body.
Like :
---
// unnamed
let Rectangle = class {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
console.log(Rectangle.name);
// output: "Rectangle"

// named
let Rectangle = class Rectangle2 {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
};
console.log(Rectangle.name);
// output: "Rectangle2"
---

Note: Class expressions must be declared before they can be used 
(they are subject to the same hoisting restrictions as described in the class declarations section).

A constructor can use the super keyword to call the constructor of the super class.

Prototype methods:
---
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
  // Getter
  get area() {
    return this.calcArea();
  }
  // Method
  calcArea() {
    return this.height * this.width;
  }
}

const square = new Rectangle(10, 10);

console.log(square.area); // 100
---

Sub classing with extends: The extends keyword is used in class declarations or class expressions to create a class as a child of another class.
Like:
---
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name); // call the super class constructor and pass in the name parameter
  }

  speak() {
    console.log(`${this.name} barks.`);
  }
}

let d = new Dog('Mitzie');
d.speak(); // Mitzie barks.
---
If there is a constructor present in the subclass, it needs to first call super() before using "this"	

Super class calls with super: The super keyword is used to call corresponding methods of super class. 


* Routing:
 Routing refers to how an application’s endpoints (URIs) respond to client requests.
or example, app.get() to handle GET requests and app.post to handle POST requests. 
You can also use app.all() to handle all HTTP methods and app.use() to specify middleware as the callback function
Like: 
---
app.all('*', requireAuthentication)
app.all('*', loadUser)
---

* Route methods:
---
// GET method route
app.get('/', (req, res) => {
  res.send('GET request to the homepage')
})

// POST method route
app.post('/', (req, res) => {
  res.send('POST request to the homepage')
})
---
and we have this Route (GET, POST, PUT, DELETE)

* Route paths: 
Route paths can be strings, string patterns, or regular expressions.
If you need to use the dollar character ($) in a path string, enclose it escaped within ([ and ]).
 For example, the path string for requests at “/data/$book”, would be “/data/([\$])book”.

More than one callback function can handle a route (make sure you specify the next object).
 For example:
---
app.get('/example/b', (req, res, next) => {
  console.log('the response will be sent by the next function ...')
  next()
}, (req, res) => {
  res.send('Hello from B!')
})
---

A combination of independent functions and arrays of functions can handle a route. For example:
---
const cb0 = function (req, res, next) {
  console.log('CB0')
  next()
}

const cb1 = function (req, res, next) {
  console.log('CB1')
  next()
}

app.get('/example/d', [cb0, cb1], (req, res, next) => {
  console.log('the response will be sent by the next function ...')
  next()
}, (req, res) => {
  res.send('Hello from D!')
})
---
* app.route():

---
app.route('/book')
  .get((req, res) => {
    res.send('Get a random book')
  })
  .post((req, res) => {
    res.send('Add a book')
  })
  .put((req, res) => {
    res.send('Update the book')
  })
---

* express.Router:

---
const express = require('express')
const router = express.Router()

// middleware that is specific to this router
router.use((req, res, next) => {
  console.log('Time: ', Date.now())
  next()
})
// define the home page route
router.get('/', (req, res) => {
  res.send('Birds home page')
})
// define the about route
router.get('/about', (req, res) => {
  res.send('About birds')
})

module.exports = router
----

* ExpressJS 4.0 :
Application Structure

 - package.json  // set up our node packages
    - server.js     // set up our app and build routes
---
npm install
---

We will need our package.json file to define our dependencies.
---
 {
        "name": "express-router-experiments",
        "main": "server.js",
        "dependencies": {
            "express": "~4.0.0"
        }
    }
---


we defined server.js as the main file in package.json.

/ BASE SETUP
    // ==============================================

    var express = require('express');
    var app     = express();
    var port    =   process.env.PORT || 8080;

    // ROUTES
    // ==============================================

    // sample route with a route the way we're used to seeing it
    app.get('/sample', function(req, res) {
        res.send('this is a sample!');
    });

    // we'll create our routes here

    // START THE SERVER
    // ==============================================
    app.listen(port);
    console.log('Magic happens on port ' + port);
---



* Too more informaion:

[Express Routing](https://www.digitalocean.com/community/tutorials/learn-to-use-the-new-router-in-expressjs-4) <br/>

[Review: ES6 Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)<br/>

[Express Routing](https://expressjs.com/en/guide/routing.html)
