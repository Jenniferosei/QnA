# What is Hoisting?

In programming what we are mainly doing is declaring some variable or class or function or whatever, and then doing something with it. So it makes sense that the "declaration" aspect comes before the "usage". But what happens if you actually use a function or variable or whatever before its declaration? Will the application break?
This is where the concept of hoisting steps in. At runtime, the JS interpreter moves all your declarations to the top of the codes so that they can be used without creating any errors. But the caveat here is that not everything is hoisted.

- Hoisting for functions : Function declarations are hoisted but function expressions aren't.
- Hoisting for classees: Class declarations are hoisted but class expressions are not.
- Hoisting for variables: Variables declared with the **var** keyword are hoisted **and initialized with undefined**, but those declared with **let** or **const** are not initialized.

# What is closure?

Closure is a combination of a function and references to it's surrounding state.

- Anytime you declare a function (lets call our function **sayHello**) , JS creates a "container".
- To that container, the **sayHello** function is added.
- Then we look at all the other variables and functions (ie. surronding state) that **sayHello** makes reference to and add them to the "container".
- Now JS "closes" the "container" and attaches it to the function like a backpack.
- With this done, anytime we are able to call the function **sayHello** somewhere and the variables or functions it uses to carry out its actions are out of scope, sayHello will look it "container", pick whatever it needs from the container and use it to perform the duties of the function.

# What is a pure function?

A function is said to be pure if when given the same input, it will always return the same output **without any side effects**. Things that make a function impure include:

An impure function depends on

- current time
- random numbers generated inside the function
- input/output

Side effects include:

- user output
- network request
- writing to disk
- logging to the console
- mutating state
- querying the DOM

  Example of pure function includes a reducer function,

# Throttling and Debouncing.

Scenario: Assuming we have a button on a website that fetches data from a server on click. What happens if a user rapidly hits this button for a number of times? Should it initialize the database query for each click? It could, but that is not effective and puts too much load on the server.
Throttling and Debouncing are both means of **limiting the rate of function calls**.
And so for our earlier scenario, we can use throttling or debouncing so we don't make a server request anytime a user hits the button (unless some condition is met).

### Debouncing

With Debouncing, we set a time **delay** (lets say 1 second).

- When the button is clicked, we don't call the function yet.
- We only call the function if the user duration from the last click equals the set time delay.
- So if a user makes rapid clicks at an interval shorter than the delay we set, the function never gets called.
  Debouncing is typically used for search input fields

### Throttling

In thottling, we set a time **interval** (again lets say 1 second)

- When the button is clicked for the first time, the function is called.
- But if the user keeps clicking, we drop all the subsequent calls and only call the function again after the interval has been reached.
- If the user keeps clicking, the call will only made once every 1 second( our set interval)

# What is currying?

Currying refers to the transformation of a function that takes multiple arguments into a **series** of functions each of which takes a single argument.
OR
Currying is the process of converting a function of N arity to a function of 1 arity.
OR
Currying can be defined as the process of transforming a function callable as f(a, b, c) into one callable as f(a)(b)(c)

#### Advantages of currying.

- Most useful when you need to use the same call with some of the parameters a lot.
- Makes code easier to refactor and read.
- Helps to create higher-order functions

# What is scaling?

Scaling refers to the ability of a system to remain stable while increasing its functionality and capacity.
There are two types: Vertical and horizontal scaling

## Vertical Scaling

In vertical scaling **(scaling up)**, we increase or upgrade the components of a system. eg increasing RAM, upgrading processor, etc.

### Cons

- Can be quite expensive
- Downtime needed to upgrade hardware
- The machine now is the single source of failure.
- Need to scale down if traffic slows down than expected since resources will be wasted

## Horizontal Scaling

In horizontal scaling **(scaling out)**, we increase the number of processing computers (nodes) so that they all aggregrate their compute power to handle tasks. Thus we add more computers and share the workload across them.

### Cons

- Extra complexity of load balancing.

# Databases

A database is an organized collection of data.
There are several categories but most common of them are Relational and Non-relational databases

#### Relational database

A type of database in which data is organized as set of tables with rows and columns and is such that the data has access points through which they can relate to other sets of data. Examples include MySQL, Microsoft SQL Serer, Oracle database, IBM DB2, etc.

###### Pros

- speed
- security
- simplicity
- accuracy

###### Cons

- Expensive
- Performance suffers with increased number of tables.
- Requires large amount of physical storage.
- Becomes more complex as amount of data increases.
- Fields are limited and can't accommodate more information.
- Requires lots of planning and structuring.
- Do not scale well horizontally.

#### Non-Relational Database

A type of DB that does not use a tabular schema of rows and columns, but uses a storage model that is optimized for the specific requirements of the type of data being stored. eg. MongoDB, Apache, Casandra, Apache HBase, Couchbase, etc.

###### Pros

- Flexible data model.
- Evolving data model.
- Massive dataset organization
- Built for the cloud
- High Performance
- Open-source thus less expensive
- Scales better horizontally
- Can run on low-resource devices

######

- Lack of standardization.
- Lack of consistency
- Poor usability. ie> don not really have useful management tools

# Difference between var, let and const

These are all **keywords** in javascript for defining variables. The differences between them can be thought of in three ways; scoping, hoisting and variable redeclaration

|                         | var                                        | let                         | const                       |
| ----------------------- | ------------------------------------------ | --------------------------- | --------------------------- |
| Hoisting                | Hoisted and initialized with **undefined** | Hoisted but not initialized | Hoisted but not initialized |
| Variable Re-declaration | Permits re-declaration                     | Not allowed                 | Not allowed                 |
| Scoping                 | Function / global scoped                   | Block scoped                | Block scoped                |

## Scoping

**var** is function/global scoped while **let** and **const** are block scoped.

## Hoisting

Variables declared with the **var** keyword are hoisted **and initialized with undefined**, but those declared with **let** or **const** are hoisted but not initialized.

## Variable Re-declaration

**var** permits variable re-declaration, let and const don't

# Virtualization and containerization

### Scenario

Lets assume you use a MacOS device but then you work in an institution that requires that you use a Windows device . How would you work around this obstacle? The easiest way is the set aside the MacOS device and get a new Windows device. And now you're in sync with your company. Cool.
But while this works, it is quite an expensive solution to the problem.
How about if we can somehow find a way to allow you, while still using the Mac device, simulate and use the Windows OS?
This is the doing of virtualization.

## Virtualization

Virtualization uses software (hypervisor) to create an abstraction layer over computer hardware that allows the hardware elements of a single computer (processor, memory, storage, etc) to be divided into multiple virtual computers, commonly called virtual machines.

#### Hypervisor

A software layer that coordinates virtual machines. It serves as an interface between the virtual machine and the underlying physical hardware, ensuring that each has access to the physical resources it needs to execute. There are 2 types of hypervisors.

- Type 1 or "bare-metal" hypervisors are installed directly on top of the physical computer, interact with the underlying physical resources and replace the traditional OS altogether.
- Type 2 or "hosted" hypervisors are run as an application on an existing OS.

#### Benefits of virtualization

- Resource efficiency: Running different server apps with different OS on the same server.
- Easy management
- Minimal downtime: Multiple VMs can be run alongside each other and fail over between them when problems arise.
- Faster provision: It is easier to make VMs available if the hardware is in place.

## Containerization

A form of OS virtualization where the software code is packaged with just the OS libraries and dependencies required to run the code to create a single lightweight executable, called a container that runs consistently on any infrastructure.

#### Benefits

- Portability
- Agility
- Speed
- Fault isolation
- Efficiency
- Ease of management

# What are the SOLID principles?

They are five principles of Object-Oriented class design. There are a set of rules an best practices to follow whil designing a class structure.
Although the solid principles were originally centered OOP, they are applicable in other aspects of software engineering.

#### Single Responsibility Principle

It states that a class should do one thing and therefore it should have only a single reason to change. A class with more responsibilities increases the probability of bugs, because changing one of the responsibilities risks affecting the others without knowing.

#### Open-Closed Principle

It states that classes should be open for extension but closed to modifications. This means we should be able to add new functionality without touching the existing code for the class. This is achieved with the help of interfaces and abstract classes.

#### Liskov's Substitution Principle

It states that subclasses should be substitutable for their base classes without altering the correctness of the code.
If a class B is a subclass of a class A, then we should be able to pass class B to any method that expects class A.
By this, a child class should be able to perform the same functions as its parent class.

#### Interface Segregation Principle

It states that client-specific interfaces are better that one general purpose interface.
Clients should not be forced to implement functions that they do not need. A class should perform the actions that are needed to fulfil its role.

#### Dependency Inversion.

It states that classes should depend upon interfaces or abstract classes instead of concrete classes or functions. OR
A high level module should not depend on a low level module, but they should both depend on abstractions.


[The Single Responsibility Principle states that a class should do one thing and therefore it should have only a single reason to change.

To state this principle more technically: Only one potential change (database logic, logging logic, and so on.) in the software’s specification should be able to affect the specification of the class.

This means that if a class is a data container, like a Book class or a Student class, and it has some fields regarding that entity, it should change only when we change the data model.

Following the Single Responsibility Principle is important. First of all, because many different teams can work on the same project and edit the same class for different reasons, this could lead to incompatible modules.

Second, it makes version control easier. For example, say we have a persistence class that handles database operations, and we see a change in that file in the GitHub commits. By following the SRP, we will know that it is related to storage or database-related stuff.

Merge conflicts are another example. They appear when different teams change the same file. But if the SRP is followed, fewer conflicts will appear – files will have a single reason to change, and conflicts that do exist will be easier to resolve.

Open-Closed Principle
The Open-Closed Principle requires that classes should be open for extension and closed to modification.

Modification means changing the code of an existing class, and extension means adding new functionality.

So what this principle wants to say is: We should be able to add new functionality without touching the existing code for the class. This is because whenever we modify the existing code, we are taking the risk of creating potential bugs. So we should avoid touching the tested and reliable (mostly) production code if possible.

But how are we going to add new functionality without touching the class, you may ask. It is usually done with the help of interfaces and abstract classes.

Now that we have covered the basics of the principle, let's apply it to our Invoice application.

Let's say our boss came to us and said that they want invoices to be saved to a database so that we can search them easily. We think okay, this is easy peasy boss, just give me a second!

Liskov Substitution Principle
The Liskov Substitution Principle states that subclasses should be substitutable for their base classes.

This means that, given that class B is a subclass of class A, we should be able to pass an object of class B to any method that expects an object of class A and the method should not give any weird output in that case.

This is the expected behavior, because when we use inheritance we assume that the child class inherits everything that the superclass has. The child class extends the behavior but never narrows it down.

Therefore, when a class does not obey this principle, it leads to some nasty bugs that are hard to detect.

Liskov's principle is easy to understand but hard to detect in code. So let's look at an example.

Interface Segregation Principle
Segregation means keeping things separated, and the Interface Segregation Principle is about separating the interfaces.

The principle states that many client-specific interfaces are better than one general-purpose interface. Clients should not be forced to implement a function they do no need.

Dependency Inversion Principle
The Dependency Inversion principle states that our classes should depend upon interfaces or abstract classes instead of concrete classes and functions.

In his article (2000), Uncle Bob summarizes this principle as follows:

"If the OCP states the goal of OO architecture, the DIP states the primary mechanism".
These two principles are indeed related and we have applied this pattern before while we were discussing the Open-Closed Principle.

We want our classes to be open to extension, so we have reorganized our dependencies to depend on interfaces instead of concrete classes. Our PersistenceManager class depends on InvoicePersistence instead of the classes that implement that interface.]

# Session management

[Read more here](https://medium.com/@prashantramnyc/difference-between-session-cookies-vs-jwt-json-web-tokens-for-session-management-4be67d2f066e)
[and here](https://www.packetlabs.net/posts/session-management/)
When a website successfully authenticates a user, the browser and the server open a **session**.
A session is an HTTP conversation in which the browser sends a series of HTTP requests corresponding to user actions and the web server recognizes them as coming from the same authenticated user without requiring the user to login for each request.
**Session Management** refers to the process of securely handling multiple requests to a web-based application or service from a single user or entity.
Web servers and browsers communicate over HTTP, but HTTP is a **stateless protocol**, i.e. every request is independent and does not relate to the prior request. It is through sessions that the server is able to remember distinct information about the client.

## Session or Cookies based approach

When a user successfully authenticates, the server generates some information about the user

## JWT based approach

JSON Web Token is an open industry standard used to share information between two entities, usually a client (like your app’s frontend) and a server (your app’s backend).They securely represent *claims* between two parties.

### Token

A token is a string that contains some information that can be verified securely.

### JWT Structure

A JWT contains three parts:

- **Header**: Consists of two parts:
  - The signing algorithm that’s being used.
  - The type of token, which, in this case, is mostly “JWT”.
- **Payload**: The payload contains the claims or the JSON object.
- **Signature**: A string that is generated via a cryptographic algorithm that can be used to verify the integrity of the JSON payload.

# Security Vulnerabilities

## SQL Injection Attack

In SQL injection, attackers target a website that uses an SQL database and construct **queries** to the database in an insecure manner. If website is vulnerable to SQL injection, an attacker can often run arbitrary SQL statements against your database, allowing them to bypass authentication; read, download, and delete data at will; or even inject malicious JavaScript into the pages rendered to your users.

#### Mitigation

1.  Use parameterized statements.
2.  Use object-relational mapping.

## Cross-site Scripting Attack (XSS)

Browsers are built such that anytime they encounter JS code as they parse HTML, they should run the JS code. And so any code written inside a <script> tag will be executed immediately. Attackers can take advantage of this and embed some malicious code into the database, usually through SQL injection or legitimate means like the comment section, and when the browser fetches this data and renders it, the malicious code gets executed.

#### Mitigation

1. Escape HTML characters
2. Implement a Content Security Policy: Content Security Policy basically tells the browser not to execute any inline JS in <script> tags.

## Cross-site Request Forgery(CSRF / XSRF)

Here, an attacker can trick a user into clicking a malicious link that triggers undesirable or unexpected side effects. Attackers usually launch CSRF attacks by exploiting websites that implement GET requests that change the state of a web server. A GET request is triggered when a victim clicks a link, allowing the attacker to craft misleading links into the target site that perform unexpected actions.

#### Mitigation

1. Follow REST principles: Ensure GET requests do not make any changes on the server.
2. Implement Anti-CSRF cookies.
3. Use the SameSite Cookie Attribute.
4. Require re-authentication for sensitive actions. (eg. payments).

## Server-Side Request Forgery (SSRF)

Hackers making malicious HTTP requests often seek to disguise where those requests are launched from. If your web server makes outgoing HTTP requests,and a hacker gets access to control which URLs those requests are sent to, a hacker can use your server to send malicious requests. The misleading thing here is that the victim of the attack will now see the attack as though you were the perpetrator. It is thus import to ensure that outgoing network request from your server are carried out securely

#### Mitigation

1. Audit any parts of your code that make outbound HTTP requests.
2. Whitelist the individual domains that you need access to in your firewall, and ban all others.
3. Employing penetration testing to detect SSRF vulnerabilities in your code.

## Session Hijacking

What is a session?
When a website successfully authenticates a user, the browser and the server open a session. A session is an HTTP conversation in which the browser sends a series of HTTP requests corresponding to user actions, and the web server recognizes them as coming from the same authenticated user without requiring the user to log back in for each request. Thus once the session is established, you have the freedom to carry out any actions as a user (unless some measures are put in place).
Attackers seek to get hold of the session information and thus be able to carry out activities in the stead of the actual user. ie. **hijacking a users session**.

## Denial of Service Attack (DOS)

Unlike other attacks that seek to compromise a system or website, a DOS attack basically seeks to make a service or website unavailable to its users. This is achieved by flooding the system with an unnaturally high amount of traffic so that its resources are exhausted and thus cannot process any other requests.

## Distributed Denial of Service Attack (DDOS)

A regular DOS attack may be launched from a single source but a DDOS is a type of DOS attack in which the traffic emerges from multiple co-operating sources and thus appears like a genuine increase in site visits.

#### Mitigation

1. Throttle incoming requests
[What does it mean to throttle requests?
API throttling is the process of limiting the number of API requests a user can make in a certain period. An application programming interface (API) functions as a gateway between a user and a software application.]  
2. Build for scale

## Social Engineering Attack

# Multi-factor Authentication

The layering of multiple factors to confirm the identity of a user during the authentication (sign in) process. For instance some sites require you to enter your username and password, and as a next step, you need to provide some extra information about you; maybe your phone number so they send you an OTP, your your biometric data, etc

# Encoding, Encryption, Hashing

#### Encoding

The process of transforming data from one format to another so that it can be understood be different systems. Encoding is **reversible** and not used to protect or secure data. Examples include:

- Unicode
- Base64
- URL encoding

#### Encryption

The process of securely encoding data in suh a way that only authorized users with a key or password can decrypt the data to reveal the original. There are two types of encryption algorithms

- Symmetric-key algorithms
- Asymmetric-key algorithms
[What is symmetric and asymmetric algorithm?
Asymmetric-key algorithms work in a similar manner to symmetric-key algorithms, where plaintext is combined with a key, input to an algorithm, and outputs ciphertext. The major difference is the keys used for the encryption and decryption portions are different, thus the asymmetry of the algorithm.]

Encryption is **reversible only by authorized users**

#### Hashing

A technique to generate a unique fixed-length string (hash) strictly depending on the specific input data. If the input data changes, the resulting hash changes.
Hashing allows us to verify if a piece of data has been altered. ie. it ensures data integrity.
Hashing is **not reversible**.

# Local Storage vs Session Storage vs Cookies

| Local Storage                                                    | Session Storage                                             | Cookies                                                                                   |
| ---------------------------------------------------------------- | ----------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| It allows 10mb.                                                  | Allows 5mb                                                  | Limited to 4kb                                                                            |
| The stored data is not deleted when browser is closed.           | Data is stored only for the duration of the session.        | The data can be set to expire.                                                            |
| Data is stored on the browser and system                         | Data is stored on the browser only                          | Data is stored on the browser only.                                                       |
| Data is not sent with the request from the client to the server  | Data is not sent with the request from the client to server | Data is sent with the request to the server                                               |
| Useful for storing data that the user will need to access later. | Useful for improving the performance of your web app        | Useful for storing data that should not be persisted for a long time, such as session IDs |

# What is an API?
What API means?
Application Programming Interface
API stands for Application Programming Interface. In the context of APIs, the word Application refers to any software with a distinct function. Interface can be thought of as a contract of service between two applications.

# What is REST?
[What is REST used for?
REST is a logical choice for building APIs that allow users to connect to, manage and interact with cloud services flexibly in a distributed environment. RESTful APIs are used by such sites as Amazon, Google, LinkedIn and Twitter.]

# What is AJAX?
[What is AJAX JavaScript used for?
AJAX allows web pages to be updated asynchronously by exchanging data with a web server behind the scenes. This means that it is possible to update parts of a web page, without reloading the whole page.]
# What is CORS?
[What do CORS mean?
Cross-Origin Resource Sharing
Cross-Origin Resource Sharing (CORS) is an HTTP-header based mechanism that allows a server to indicate any origins (domain, scheme, or port) other than its own from which a browser should permit loading resources]  

# Differences between Types and Interfaces
[One major difference between type aliases vs interfaces are that interfaces are open and type aliases are closed. This means you can extend an interface by declaring it a second time. // In the other case a type cannot be changed outside of its declaration.]
# Testing

Software testing is a method to check whether a software product matches the expected requirements gathered from users and system specifications.

## Unit Testing

Unit testing tests individual units of code, usually with zero or minimal external dependencies, to validate that each unit of the software behaves as expected. A unit may be an individual function, method, procedure, module or object.
  
[What are dependencies in React?
Image result for external dependencies in react
A dependency is just a package that your project uses. Very few javascript projects are entirely self-contained. When your project needs code from other projects in order to do its thing, those other projects are “dependencies”; your project depends on them to run]  

### Test Doubles

Test doubles are used in unit tests are used as replacements for external dependencies.

#### Mocks

Mocks are used to replace external interfaces. For instance you could write a custom function to replace one that makes an HTTP request. Mocks don't check the returned value of the function call, but check if the function is called or not, how many times it gets called, and what parameters are passed when it was called.

#### Stubs

Stubs generate predefined outputs. They are similar to mocks, but the returned value is of interest. A stub thus returns a success, a failure or an exception. Stubs check the output of a function call against the passed parameters.

## Integration Testing

This involves testing units of a software as a group to determine how they interact with each other as well as testing how they interact with external dependencies. The units in an integration test must have been tested.

## End-to-End Testing

This is a software testing method that validates the entire software from start to end along with it's integration with external dependencies. It tests from the end user's experience by simulating real user scenarios.

## toBe vs toEqual

toBe() is used for primitive values (strings, number, boolean,) while toEqual() is used for reference values (objects).

# Bug, Fix and Feature

When building an application, stuff may break. When go through the code base and figure out what caused the break, you have found the **bug**.
When you write code to solve the problem, you have written a **fix**.
When you write code to introduce a new functionality into an application, you have built a new **feature**.

# Application Lifecycle
  
There are 7 main stages in the application life cycle.
1. Version control stage 
This first stage involves building the right team necessary to work on developing the project/application and setting up all the necessary version control tools to effectively deliver on the project. Such version control activities include creating the repository needed and adding the necessary team members who will be pushing their code.
2. Build stage 
With the team assembled and responsibilities shared, each team member completes their tasks as quickly as possible and proceeds to the next stage of testing their code
3. Unit test
The completed code is subjected to unit testing to ensure it works as expected and is free of bugs
4. Deploy
After a successful unit test, the code is committed to a branch of the main repo for further evaluation and testing
5. Autotest
The different codes are reviewed and merged into the main branch. Different automated tests such as unit testing, integrated testing, etc are conducted to reveal any vulnerabilities and bugs in the code. 
6. Deploy to production
When the tested code has been greenlighted the final code is pushed to a website or app store for customers and users to interact with the product.
7. Measure and validate
Feedback about the user's experience and any insights they share about the product are collected and analysed by the team. Necessary Improvements/features are made by assigning new responsibilities and beginning the app life cycle at stage 2 (Build).

## CI/CD- Continuous Integration Continuous Development
This is simply the continuous improvement and continuous development pipeline where the feedback received is changed into a fix/improvement by cycling through stage 2 through to stage 7 quickly and efficiently to deliver on agreed timelines and maintain user satisfaction. 
The autotest stage is not seen as being implemented in all organisations during their CI/CD pipeline. However, as part of CI/CD, there is a QA (quality assurance) team that will stress test the improvement/fix to ensure that it is satisfactory and can be added to the repo in stage 4 (Deploy).

  
  
# React Basics

  ## What react is….
React is a JavaScript library developed by Facebook which, among other things, was used to build Instagram.com. Its aim is to allow developers to easily create fast user interfaces for websites and applications alike. The main concept of React.js is virtual DOM (Document Object Model represents the web page as a tree structure). It is a tree based on JavaScript components created with React that mimics a DOM tree. It does the least amount of DOM manipulation possible to keep your React components up to date.
Being a part of the JavaScript language, using React spawns lots of advantages. Products built with React are:
a.	Simple to scale
b.	 A single language used on the server/client/mobile side of things grants outstanding productivity.
c.	There are workflow patterns for convenient teamwork
d.	UI code is readable and maintainable, and more.
World-leading companies have used React and other JS technologies in some of the top market-defining products out there (Instagram, Reddit, and Facebook being the most vivid examples).
One of the major reasons to use React.js for web development is the library’s ultimately optimized development interface and coding language. Thus, lightweight React’s API is reinforced with fast performance capacities to achieve a hassle-free, rapid development workflow. React components and concepts are simple to figure out so there is not much learning curve here.
As opposed to other popular frameworks, like Vue and Angular, there is no barrage of extra HTML attributes (created when JavaScript is “crammed” into HTML - a standard practice for traditional frameworks and JS library solutions). In the long run, by putting JSX into JavaScript (literally going the other way round), React grants a much cleaner, better readable, more comprehensive code.


# State vs Props

## State

The state is a built-in React object that is used to contain data or information about the component. The state in a component can change over time, and whenever it changes, the component re-renders.
The change in state can happen as a response to user action or system-generated events. It determines the behaviour of the component and how it will render.

##Props
  
Props are short for Properties. It is a React built-in object that stores the value of attributes of a tag and works similarly to HTML attributes.
 [HTML attributes are a modifier of an HTML element type. An attribute either modifies the default functionality of an element type or provides functionality to certain element types unable to function correctly without them. In HTML syntax, an attribute is added to an HTML start tag]
Props provide a way to pass data from one component to another component. Props are passed to the component in the same way as arguments are passed in a function.

State can also be passed as props to child components

Differences

- State is mutable. Props are immutable.
- Props are read-only.	State changes can be asynchronous.
- Props make components reusable.	State cannot make components reusable.
- Props can be accessed by the child component.	State cannot be accessed by child components.

# Prop Drilling
  
is a situation where data is passed from one component through multiple interdependent components until you get to the component where the data is needed.
Passing data through multiple components is not a good way of writing clean, reusable, and DRY code.

The React context API is a fast way of avoiding prop drilling and ensuring your data is managed globally without using a huge third-party state management app like Redux. React context is a built-in API that uses the useContext hook to share data across components.

Imagine passing the data of an authenticated user from a parent component to a deep nested child component. This will be cumbersome if you need to pass the data through a lot of intermediate components.
A better approach to doing this is using React context to handle the data. useContext is a built-in hook in React.


# React Hooks
  
  React follows the principle of component-based architecture. A component in React is an isolated and reusable piece of code. The components can be of two types – class components and functional components.
Before React version 16.8, developers could handle state and other React features only using class components. But with version 16.8, React introduced a new pattern called Hooks.
Hooks are simple JavaScript functions that we can use to isolate the reusable part from a functional component. With React Hooks, we can use state, and other React features, without having to write classes. It empowers devs. to do functional programming in React.

•	 useState:
It is the most important and often used hook. The purpose of this hook to handle reactive data, any data that changes in the application is called state, when any of the data changes, React re-renders the UI.
e.g., const [count, setCount] = React.useState(0);
•	useEffect :
It allows us to implement all the lifecycle hooks from within a single function API.
e.g., // this will run when the component mounts and anytime the stateful data changes
React.useEffect(() => {
    alert ('Hey, Nads here!');
});
•	useContext:
This hook allows us to work with React's Context API, which itself a mechanism to allow us to share data within its component tree without passing through props. It basically removes prop-drilling.
e.g. 
function RightAns () {
    // it consumes value from the nearest parent provider.
    const ans = React.useContext(AnsContext);
    return <p>{ans}</p>
    // previously we were required to wrap up inside the AnsContext.Consumer
    // but this useContext hook, get rids that.
}
•	useMemo:
This hook will help you to optimise computational cost or improve performance. It mostly used when we're needed to make expensive calculations. Works great for memoizing returned values, but in other CSSNamespaceRule, we want to memoize the whole function, in that case we can use this hook ↓
function useMemo() {

    const [count, setCount] = React.useState(60);

    const expensiveCount = useMemo(() => {
        return count**2;
    }, [count]) // recompute when count changes.
}

Standard built-in hooks simplified: 
•	useState: To manage states. Returns a stateful value and an updater function to update it.

•	useEffect: To manage side-effects like API calls, subscriptions, timers, mutations, and more.
  [What is useEffect for?
What does useEffect do? By using this Hook, you tell React that your component needs to do something after render. React will remember the function you passed (we'll refer to it as our “effect”), and call it later after performing the DOM updates.]

•	useContext: To return the current value for a context.

•	useReducer: A useState alternative to help with complex state management.

•	useCallback: It returns a memorized version of a callback to help a child component not re-render unnecessarily. useCallback function keeps the function identity same in each render. useCallback function has two arguments.

-	1.The function we want to prevent from keep duplicating on each render
-	2.Dependency array: function is only rerendered when any of the value in dependency array changes.
[What is render in React JS?
In React, Render is the technique that can redirect a page with the help of function render(). Most importantly, render a function we can use to define the HTML code within the HTML element. It helps to display certain views in the UI using certain logic defined in the render function and returns the output]
•	useMemo: Memoization is an optimization technique that makes applications more efficient and hence faster. It does this by storing computation results in cache and retrieving that same information from the cache the next time it's needed instead of computing it again.This is used for expensive functions and computing expensive calculations.

## NB. useCallback and useMemo both expect a function and an array of dependencies. The difference is that useCallback returns its function when the dependencies change while useMemo calls its function and returns the result.

•	useRef: It returns a ref object with a. current property. The ref object is mutable. It is mainly used to access a child component imperatively.
[What is a ref object?
Unlike state, ref is a plain JavaScript object with the current property that you can read and modify]
•	useLayoutEffect: It fires at the end of all DOM mutations(changes). It's best to use useEffect as much as possible over this one as the useLayoutEffect fires synchronously.

•	useDebugValue: Helps to display a label in React DevTools for custom hooks.
[What is Devtools in React?
Image result for react devtools
React Developer Tools is a Chrome DevTools extension for the open-source React JavaScript library. It allows you to inspect the React component hierarchies in the Chrome Developer Tools. You will get two new tabs in your Chrome DevTools: "⚛️ Components" and "⚛️ Profiler"]
# Events

An event is an action that a user or system may trigger, such as pressing a key, a mouse clicks, etc.

•	React events are named using camelCase, rather than lowercase in HTML.
•	With JSX, you pass a function as the event handler, rather than a string in HTML.
<Button onPress={lightItUp} />
[n programming, an event handler is a callback routine that operates asynchronously once an event takes place. It dictates the action that follows the event. The programmer writes a code for this action to take place. An event is an action that takes place when a user interacts with a program.]
  
[What is asynchronous programming?
Asynchronous programming is a technique that enables your program to start a potentially long-running task and still be able to be responsive to other events while that task runs, rather than having to wait until that task has finished. Once that task has finished, your program is presented with the result.]  
## Native Events

Native events are fired directly by the browser - events like clicks, mouseovers, keypresses, etc. To receive those events on a Widget, you have to specifically sink the events. The generic events are, well, more generic.  

[Widgets are small applications that add aesthetic appeal to your home screen while also displaying data at a glance and providing useful features.]
  
## Synthetic Events

React has its own event handling system which is very similar to handling events on DOM elements. The react event handling system is known as Synthetic Events.

 DOM stands for 'Document Object Model'. In simple terms, it is a structured representation of the HTML elements that are present in a webpage or web-app. DOM represents the entire UI of your application. The DOM is represented as a tree data structure.

-	Synthetic events are a wrapper over the browser's native event.
-	They are cross-browser compatible, meaning they are supported in all the browsers; are not browser specific.

E.g’s of synthetic events:
- onClick()
- onBlur()
- onChange().

# State Management
  
React state management is a process for managing the data that React components need in order to render themselves. This data is typically stored in the component's state object. When the state object changes, the component will re-render itself. React state management is basically half of a React app.

React's useState is the best option for local state management. If you need a global state solution, the most popular ones are Redux, MobX, and the built-in Context API. Your choice will depend on the size of your project, your needs, and your engineers' expertise.


# Redux

The most important piece of any website is the application state. It's the application state that decides what users will see.
Redux is an open-source, JavaScript library used to manage the application state. React uses Redux to build the user interface. It is a predictable state container for JavaScript applications and is used for the entire application’s state management.

 # What are the components of Redux?

## Store 

Holds the state of the application. The global state of an application is stored in an object tree within a single store.
The Redux store is the main, central bucket which stores all the states of an application. It should be considered and maintained as a single source of truth for the state of the application.

## Action

The source information for the store. The only way to change the state is to emit an action, which is an object describing what happened. If anyone wants to change the state of the application, then they'll need to express their intention of doing so by emitting or dispatching an action. Every action must have at least a type associated with it. Any other detail that needs to be passed is optional and will depend on the type of action we dispatch.

For example, the above code snippet dispatches the following action:

// Action that got created by the action creator addItemToCart()

{
    type: "ADD_ITEM_TO_CART" // Note: Every action must have a type key
    payload: {
        bookName: "Harry Potter and the Goblet of Fire",
        noOfItem: 1,
    }
}

## Reducer

Specifies how the application's state changes in response to actions sent to the store. Reducers are basically pure JS functions which take in the previous state and an action and return the newly updated state.
There can either be one reducer if it is a simple app or multiple reducers taking care of different parts or slices of the global state in a bigger application.
For e.g., there can be a reducer handling the state of the cart in a shopping application, then there can be a reducer handling the user details part of the application, and so on.

Whenever an action is dispatched, all the reducers are activated. Each reducer filters out the action using a switch statement switching on the action type. Whenever the switch statement matches with the action passed, the corresponding reducers take the necessary action to make the update and return a fresh new instance of the global state.

Note that the state parameter is a default parameter which accepts an initial state. This is to handle the scenario when the reducer is called for the first time when the state value is undefined.

Also note that every reducer should handle the default case where, if none of the switch cases match with the passed action, then the reducer should return state as it is or perform any required logic on it before passing the state.
Whenever we dispatch an action with a certain type, we need to make sure to have appropriate reducers to handle that action. example, on clicking the button, we had dispatched an action with an action creator called addItemToCart(). This action creator has dispatched an action with the type ADD_ITEM_TO_CART.

Next, we have created a reducer called cartReducer which takes the state (with the default initial state) and the action as parameters. It switches on the action type, and then whichever case matches with the dispatched action type, it makes the necessary update and returns the fresh new version of the updated state.

To specify how the state tree is transformed by actions, we write pure reducers.
Reducers, as the name suggests, take in two things: previous state and an action.
Then they reduce it (read it return) to one entity: the new updated instance of state.

## Difference b/n useContext and Redux

The main difference between these two libraries is that Redux deals with changes of the state in a centralized manner. 
  
On the other hand, Context deals with them as they happen on the component level.
  
useContext: useContext is a hook that provides a way to pass data through the component tree without manually passing props down through each nested component.  
Redux: Redux is a state managing library used in JavaScript apps. It is very popular for React and React-Native. It simply manages the state and data of your application.
  
[In React, Render is the technique that can redirect a page with the help of function render(). Most importantly, render a function we can use to define the HTML code within the HTML element. It helps to display certain views in the UI using certain logic defined in the render function and returns the output.]
## Advantages of Redux

-	It is Highly Maintainable. ...
-	It Prevents Re-renders. ...
-	Redux Optimizes Performance. ...
-	Makes Debugging Easier. ...
-	Useful in Server-Side Rendering. ...

## Advantages of Context API

-	It's less complex than Redux. The workflow is much simpler than Redux. ...
-	It has a lower implementation cost. ...

# What is production in React?

The production build creates minified bundles(Bundling combines multiple files into a single file. Minification performs a variety of different code optimizations to scripts and CSS, which results in smaller payloads), lighter-weight source maps(Source maps are just JSON files that essentially rebuild what the bundlers and transpilers changed. Their main purpose is to help debug your built, optimized code. It makes sense that if you have a bug and view the stack trace, you want to see your code and not the gibberish that webpack and babel spit out.[Webpack and Babel are tools for developers that optimize JavaScript applications.

Webpack is a module bundler we can use to minify multiple files in a JavaScript project and increase the overall efficiency. A module bundler takes in all the assets and comes up with a single output file. This artefact can be imported into our HTML, making it a more lightweight project.

As for Babel, it is a syntax converter and a transpiler. There may be times you want your code to be compatible with all browsers and environments, including the older ones. In such instances, a great option to try out is Babel]), and optimized assets. This improves the load time. React recommends using production mode while deploying the react app. We now know that production build helps in optimizing performance.

# REACT Testing


## Unit Testing

Unit Testing is a testing method that tests an individual unit of software in isolation. Unit testing for React Apps means testing an individual React Component.

## Integration Testing

Integration testing is the phase in software testing in which individual software modules are combined and tested as a group. Integration testing is conducted to evaluate the compliance of a system or component with specified functional requirements. It occurs after unit testing.

## End to End Testing

is a software testing method that involves testing an application's workflow from beginning to end. This method aims to replicate real user scenarios to validate the system for integration and data integrity.

## 401 Unauthorized
 A 401 message means the server received an unauthenticated request.In this error, a message announces that the page couldn’t load because of invalid credentials for whatever reason

How to fix it?
It could be possible the login URL has changed, or the URL you entered is incorrect. However, if that’s not the case, try clearing the browser cache and cookies.


## 404 Not Found
This HTTP response is generated when a page the user is looking for cannot be found on the server. There could be multiple reasons behind 404 occurrences. Perhaps because the webmaster has deleted the page or the URL you have entered is incorrect (since it’s a client-side error).
  
How to fix it?
Fixing a broken link (or, more specifically, a 404) is still an essential maintenance task. A more natural way to do this is by installing the Redirection plugin from the WordPress directory. You can then redirect it to any webpage on the site.
  
## 500 Internal Server Error
A 500 Internal Server Error is a generic error that displays when something is wrong with your server. Because it’s a generic error message, there are a number of different causes including issues with WordPress plugins, PHP issues, database problems, and more.

How to fix it?
Fixing the 500 Internal Server Error is a bit onerous as more than one reason is to blame for its occurrence. You’ll probably want to read the full guide for this one.
  
## 502 Bad Gateway
Unlike other HTTP error codes, 502 is different. A bad gateway occurs when one server on the internet receives an invalid response from another server. A 502 HTTP status code will be tacked on a screen when the server takes longer than expected to complete a request.

How to fix it?
Most of the time this can be fixed by simply refreshing the browser, or clearing the browser cache. If you have just migrated to the site, try waiting for 24 to 48 hours. You can even reach out to the hosting provider to check with them. Sometimes, a third-party CDN service or WordPress plugin could be the reason behind your 502 response. Try switching the WordPress theme to another if the fixes mentioned above don’t work.
  
## 301 Moved Permanently
An HTTP 301 is when a specific webpage is permanently moved to a different URL. It’s not an error per se, but it does communicate important information.

It can be on a page-level where you get pointed on another similar post (or even homepage for that matter) or a domain level.

How to fix it?
To make sure the redirection is flawless, check the redirect setup. If you have used a WordPress plugin, try switching it with Redirection. If you used the .htaccess file to perform the redirection, verify that you did it correctly. Here’s how to do that. Keep the domain level redirection for a few months, so Google knows the resource is moved permanently.

## 302 Found
This HTTP status code is similar to the 301, but it is used for a temporary redirect. This response tells Google that the page is moved temporarily and will be back to the original URL at some point. If done correctly, it will redirect the user to another URL in a couple of seconds.

How to fix it?
The easiest way to set up a 302 redirect is by using a WordPress plugin. You can install and use Rank Math from the WordPress directory.

## 410 Gone
This 410 Gone error is similar to the 404 response. Think of this as a permanent 404. When a webmaster decides to remove a post or page forever or republish it on another site, they can use this code.

A 410 response tells Google the requested resource is permanently removed from the internet and will not reappear. This makes it easier to get the page de-crawled or de-indexed from Google.

How to fix it?
There are multiple reasons behind a 410 gone error. First, check the input URL and make sure it’s correct. Next, try debugging the update on the WordPress website. Uninstall the WordPress plugins or other third-party extensions. If none of this works, then it’s a problem from the server end. Find the .htaccess file. Next, locate the word “RewriteXXX” in the .htaccess text editor and enter the following code:

RewriteEngine on
RewriteRule ^(.*)$ http://yourwebsitename.con/expired_page $1 [R=410,L] 
  When entering the code, replace [http://yourwebsitename.con/expired_page] with the URL that is expired, or where you’d like to add 410 responses.

 
  
  
  
  
  
  
  
  
  
  

# Component Documentation
