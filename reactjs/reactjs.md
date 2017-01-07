Imperative - HOW to do (very literal code)
Declarative - WHAT to do (abstractions). Minimizes mutability, code is more readable, less bugs.

Have to use `setState` to change state. 

React Router -> URLs map different components to be active
Webpack -> code bundler (takes code, transforms, then outputs)
Babel -> Code transformation (JSX -> JavaScript)
Axios -> Makes HTTP requests

Webpack -> Can tell it everything you need to transform (Sass/LESS, CoffeeScript/JSX, etc => CSS, JS, HTML).

Webpack needs to know:
* Your root JS file
* Which transformations to make
* Where to save the transformations

modules: https://medium.freecodecamp.com/javascript-modules-a-beginner-s-guide-783f7d7a5fcc#.3j310ye8r
https://medium.freecodecamp.com/javascript-modules-part-2-module-bundling-5020383cf306#.6ubbw8b00

“dirty checking” 

js anonymous encaps’d functions: http://stackoverflow.com/questions/1634268/explain-javascripts-encapsulated-anonymous-function-syntax

CLOSURES: http://javascriptissexy.com/understand-javascript-closures-with-ease/
https://medium.freecodecamp.com/lets-learn-javascript-closures-66feb44f6a44#.elbwuz1uc

function declaration VS function expression: https://javascriptweblog.wordpress.com/2010/07/06/function-declarations-vs-function-expressions/
anonymous functions: https://en.wikibooks.org/wiki/JavaScript/Anonymous_functions
function expressions: http://benalman.com/news/2010/11/immediately-invoked-function-expression/


Module Pattern: http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html

 `—save-dev` (use in development, not production) vs `—save` (production)


React-dom vs react-native

CALLBACK FUNCTIONS

f(d) = V, a function [in react] takes some data and returns a view.

#### Pure functions:
* Always return the same result given the same arguments.
* Execution doesn’t depend on the state of the application.
* Don’t modify variables outside of their scope.
* No side effects (mutations, async reqs)

React’s render needs to be a pure function, which provides pure function benefits to UI

#### React components should be:
* Focused
* Independent
* Reusable
* Small
* Testable

React Router: https://github.com/reactjs/react-router-tutorial/tree/master/lessons

https://tylermcginnis.com/functional-components-vs-stateless-functional-components-vs-stateless-components-630fdfd90c9c

`This.props.children`

PropTypes -> Type-matching in React. Similar to strong params in rails? `size: PropTypes.number.isRequired,`
Also serves as a way to document objects (what it needs to accept in order to render properly)

Use stateless functions for presenters that have no state. Call proptypes as method for that function.

Container -> Logic
Component -> UI

Route to a new path inside a function: `this.context.router.push()` (can add pathnames & queries)

`<Link to ‘’ />` (from ReactRouter.Link) is syntax for changing routes

Routing inside a container -> needs `contextTypes`

Lifecycle methods are special methods each component can have that allow us to hook into the views when specific conditions happen (i.e. when the component first renders or when the component gets updated with new data, etc).

#### React's Life Cycle Methods fall into two categories:
1. When a component gets mounted (added) to the DOM and unmounted (which only happen once within the life cycle of a component):
  * Establish default props (getDefaultProps)
  * Set initial state (getInitialState)
  * Make an Ajax request to fetch some data needed (componentDidMount)
  * Set up any listeners (ie Websockets or Firebase listeners) (componentDidMount)
  * Remove any listeners you initially set up on unmount (componentWillUnmount)
2. When a component receives new data from parent component:
  * Execute code when given new props (componentWillReceiveProps)
  * Control rerendering (shouldComponentUpdate)

#### `this` rules:
1. Implicit binding (“left of the dot at call time”) hey.thisFunctionUsesThis(); (this defined by what var the function is called on.)
2. Explicit binding (uses methods “call, apply, bind”) - explicitly define this

Every function has the call method. `this` is what’s being passed in. The first argument it takes is always context. If you define params, context is not included (but is in call. So…. call(stacey, potatoes, carrots, celery) would be sayName(veg1, veg2, veg3). 
What is doing this called? (When you’re using a function that requires call/context)
`.apply` is like call but you can pass it an array. So call(stacey, vegetables) [where vegetables is [potatoes, carrots, celery] and sayName has the same params as in previous example (veg1, veg2, veg3)
`.bind` makes a new function given the same args as .call
`.call` & `.apply` IMMEDIATELY invoke function. `.bind` makes a function to call later.
3. New binding: New binds the this keyword to the new object being constructed. So for zebra, `this.color = ‘black and white’`
4. Window binding: If you call a function that uses this but you do not define it (by 1,2, or 3 methods), JS will use whatever the window value is (`window.whatever == this.whatever`)
Strict mode, this will remain undefined. To figure out the `this` keyword, ask yourself “where is the function invoked?” NOT “when was it defined?”

A capitalized var name means they are constructors and should be called with the new keyword. e.g. `var Chance = function (){}`

**Axios:** HTTP client for JS (like Faraday for Ruby)

**Promises:** the eventual result of an asynchronous operation. It is a placeholder into which the successful result value or reason for failure will materialize. > https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

`Axios.get` returns a promise. `Axios.all`, when given an array of promises, after they are all done resolving, the `.then` function will run with the information. Add `.catch` methods to end of your promise chains to handle errors.

`.bind` to set the context for `this` (for instance, trying to use `this` nested inside another function).

`Array.reduce`, `Array.map`, & `Array.filter`
