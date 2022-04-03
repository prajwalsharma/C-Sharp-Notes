## 1. What is React?

1. Open source library created by Facebook to build User Interfaces.
2. It is a library, not a framework.
3. Only focus is on UI.
4. Rich ecosystem of helper libraries for Routing, State Management, Pagination, Network Calls etc.



## 2. Component Based Architecture

1. React uses Component Based Architecture.
2. Application is divided into components, like Header component, Footer Component, Profile Component etc.
3. Components can be reused therefore we can write reusable code in React.



## 3. React is Declarative

1. We tell react what we want and React will generate the actual UI.
2. React will handle efficiently updating & rendering of the components.



## 4. Create React App

It is a CLI tool through which we can create a boilerplate React project.

```powershell
// Download the boilerplate project into the folder
npx create-react-app my-first-app

// Change directory
cd my-first-app

// Run the React app
npm start
```



## 5. npx vs npm

1. npm is a package manager for Node ecosystem.

2. npx command will download & install the create-react-app package locally for each project. Slow but always get the latest project.

   ```
   npx create-react-app hello-world
   ```

   

3. npm command will download & install the CRA project globally, and all new projects will use that package only. Quick but packages can be outdated after some time.

   ```
   npm install create-react-app -g
   
   create-react-app hello-world
   ```



## 6. React Folder Structure

1. **package.json**

   This file contains all the dependecies & scripts required to run the project. 

2. **package-lock.json**

   This file is just like package.json but is if you're using 'yarn' instead of 'npm'.

3. **node_modules**

   All dependencies are installed in this folder only.

4. **public**

   1. This file contains 2 important files
   2. **index.html** - The single html page for a SPA. All React code is injected into this file only. 
   3. **manifest.json** - Used for PWA

5. **src**

   1. All react code is placed in this folder.
   2. **index.js** - The root file where we define the root component and place into index.html.
   3. **App.js** - The root component defined in the index.js.
   4. **App.css** - The css file for App component.
   5. **index.css** - The css file for index.js file.
   6. **serviceWorker.js** - Used for PWA
   7. **App.test.js** - Test file for App component.



## 7. Components

1. It is a part/section of the UI.

2. All components together make a complete UI of the application.

3. In React, App is the root component. We define all other components in App component only.

4. The component is basically a JS file, like HeaderComponent.js

5. Components are of two types:

   1. **Functional** Component

      1. Stateless

      2. Written as a function

      3. We can use Hooks in **React 16** to make functions stateful.

      4. 'this' keyword is not present.

      5. Also called "Stateless/Dumb/Presentation Component"

         ```jsx
         function WelcomeText(){
             return <h1>Hello, World!</h1>
         }
         ```

         

   2. **Class** Components

      1. Statefull

      2. Written as a class

      3. Complex UI logic if state is used

      4. Also called "Stateful/Smart/Container Component"

      5. Contains lifecycle hooks

         ```jsx
         class WelcomeText extends React.Component{
             render(){
                 return <h1>Hello, World!</h1>
             }
         }
         ```



## 8. Functional Component

```jsx
// App.js

import logo from "./logo.svg";
import "./App.css";
import FunctionalDemo from "./components/FunctionalDemo.jsx";

function App() {
  return (
    <div className="App">
      <FunctionalDemo />
    </div>
  );
}

export default App;

```

```jsx
// FunctionalDemo.jsx

function FunctionalDemo(){
    return <h1>
        This is a Functional Component
    </h1>
}

// Or

const FunctionalDemo = () => <h1>Hello World</h1>

export default FunctionalDemo
```



## 9. Class Component

1. We use ES6 classes to represent components.

2. Class components can recieve props from parent component.

3. Class components can have private variables (state).

   ```jsx
   // App.js
   
   import React from "react"
   import logo from "./logo.svg";
   import "./App.css";
   import FunctionalDemo from "./components/FunctionalDemo.jsx";
   import ClassDemo from "./components/ClassDemo.jsx";
   
   function App() {
     return (
       <div className="App">
         <FunctionalDemo />
         <ClassDemo />
       </div>
     );
   }
   
   export default App;
   
   ```

   ```jsx
   import React, { Component } from "react"
   
   class ClassDemo extends Component{
       render(){
           return <h1>This is a Class Component</h1>
       }
   }
   
   export default ClassDemo
   ```



## 9. Type of Exports

```jsx
// Default Export
export default greet;

import greet from 'greet.jsx' // Correct
import mygreet from 'greet.jsx'	// Correct

// Named Export
export greet;

import {greet} from 'greet.jsx' // Correct
import mygreet from 'greet.jsx' // Error
```



## 10. JSX

1. JSX is "JavaScript XML".

2. We can write XML like code.

3. JSX allows us to write HTML + JS code together.

4. JSX makes writing React code easier, we can still write React code without JSX but it will be complex.

   ```react
   return React.createElement(
       'div', 
       null, 
       React.createElement('h1', null, 'Hello Prajwal'))
   ```

   

5. JSX code will eventually convert to pure JS.



## 11. Props

1. Props are variables/functions/components that can be passed within components.

2. Through props, we can use the same component with different data.

3. We cannot change the value of props.

   ```jsx
   // App.jsx
   function App() {
       return (
           <div className="App">
               <FunctionalDemo name="Prajwal" />
               <ClassDemo name="Sharma" />
           </div>
       );
   }
   
   // FunctionalDemo.jsx
   function FunctionalDemo(props){
       return <h1>
           {props.name}
       </h1>
   }
   
   // ClassDemo.jsx
   class ClassDemo extends Component{
       render(){
           return <h1>
               {this.props.name}
           </h1>
       }
   }
   ```

4. Children Props

   ```jsx
   // App.jsx
   function App() {
       return (
           <div className="App">
               <FunctionalDemo name="Prajwal">
                   <p>This is children prop</p>
               </FunctionalDemo>
               <ClassDemo name="Sharma">
                   <p>This is children prop</p>
               </ClassDemo>
           </div>
       );
   }
   
   // FunctionalDemo.jsx
   function FunctionalDemo(props){
       return <h1>
           {props.name}
           {props.children}
       </h1>
   }
   
   // ClassDemo.jsx
   class ClassDemo extends Component{
       render(){
           return <h1>
               {this.props.name}
               {this.props.children}
           </h1>
       }
   }
   ```



## 12. State

1. State is the collection of variables defined in the component.

2. It is managed within the component.

3. It is mutable.

   ```jsx
   // App.jsx
   function App() {
     return (
       <div className="App">
         <Message />
       </div>
     );
   }
   
   //Message.jsx
   class Message extends Component{
   
       constructor(){
           super();
           this.state = {
               message : "Welcome Visitor"
           }
       }
   
       render(){
           return <h1>
               {this.state.message}
           </h1>
       }
   }
   ```

   



## 13. State vs Props

1. Props are passed to another components, State is managed within the component.
2. Props are function parameters, State are variables declared in the component.
3. Props are immutable, State is mutable and can be changed.
4. Props are used like "props" or "this.props", State is used like "useState Hook" or "this.state" 



## 14. Event Handling

```javascript
import { Component } from "react";

// Class Component
class Message extends Component{

    // Constructor with State
    constructor(){
        super();
        this.state = {
            message : "Welcome Visitor"
        }
    }

    // Method to change Text by changing state
    changeText = () => {
        this.setState({
            message : "Text is changed"
        })
    }

    // Method to change text by changing state
    changeTextDynamic = (msg) => {
        this.setState({
            message : msg
        })
    }

    render(){
        return <div>
            <p>{this.state.message}</p>
            <button onClick={this.changeText}>Subscribe 1</button>
            <button onClick={() => this.changeTextDynamic("Subscribed!")}>Subscribe 2</button>
        </div>
    }
}

export default Message
```

```jsx
// Functional Component

function EventHandlingDemo() {

    const btnClickHandler = () => alert("Button Clicked!")

    const btnClickHandler2 = (msg) => alert(msg)

  return <div>
      <button onClick={btnClickHandler}>Click</button>
      <button onClick={() => btnClickHandler2("Hello")}>Click</button>
  </div>;
}

```



## 15. Perform action after state is updated

1. setState() method is asynchronous, so the next line of codes will execute even before the state is updated.

2. We need to use another way to use setState if we want to perform some action after state changes

   ```jsx
   changeState = () => console.log("State changed");
   
   this.setState({
       count: this.state.count + 1
   }, this.changeState);
   ```

   

## 16. Safely fetch prev state value in setState

```jsx
this.setState((prevState) => ({
    count: prevState.count + 1
}))
```



## 17. Destructuring Props & state

```jsx
// Class Component
export class DestructureDemo extends Component {
    render() {
        const {name, age} = this.props
        const {name, age} = this.state
        
        return <div>Hello, {name}, Age: {age}</div>;
    }
}

// Function Component
const Greet = props => {
    const {name, age} = props;
    return (
        <div>
            <p>{name}</p>
            <p>{age}</p>
        </div>
    )
}
```



## 18. Pass methods as props

```jsx
// Parent Component
class MethodAsProps extends Component {

    constructor(props) {
      super(props)
    
      this.state = {
         message: "Hello"
      }
    }

    printMessage = () => alert(this.state.message)
    
    printMessageFromChild = (msg) => alert(msg);
    

  render() {
    return <MethodAsPropsChild 
               funProp={this.printMessage}
               funProp2={this.printMessageFromChild}
               />
    }
}


// Child Component
function MethodAsPropsChild(props) {
  return <div>
    	<button onClick={props.funProp}>Click Parent</button>;
        <button onClick={() => props.printMessageFromChild("Message from Child")}>Click Parent</button>;
    </div>
}

// Example of Closures in JS
```



## 19. Conditional Rendering

1. Use **if-else** conditions

   ```jsx
   const Greet = (props) => {
   
       const {name} = props;
   
       if(name === "Batman"){
           return <Batman/>
       }
   
       return <NotASuperHero/>
   }
   ```

   

2. Use **element variables**

   ```jsx
   const Greet = (props) => {
   
       const {name} = props;
       
       const messageComponent;
   
       if(name === "Batman"){
           messageComponent = <Batman/>
       }
       else{
           messageComponent = <NotASuperHero/>
       }
   
       return messageComponent;
   }
   ```

   

3. Use **ternary Operator**

   ```jsx
   const Greet = (props) => {
   
       const {name} = props;
       
       return name === "Batman" ? <Batman/> : <NotASuperHero/>
   }
   ```

   

4. Use **short-circuit** operator

   ```jsx
   const Greet = (props) => {
   
       const {name} = props;
       
       return name === "Batman" && <Batman/>
   }
   ```

   

## 20. List Rendering

```jsx
// Class Component
class Products extends Component{
    constructor(){
        super();
        this.state = {
            products = ["Shoe", "Shirts", "Bat"]
    }

    render(){
        return <div>
            {
                this.state.products.map(item => <p>{item}</p>)
            }
        </div>
    }
}

// Function Component
const products = () => {
    const names = ["Bruce", "Clark", "Diana"];
    const namesList = names.map((name,index) => <p key={index}>{name}</p>)
    return <div>{namesList}</div>
}

// Using array index as 'key' is a known anti-pattern which is not recommended
```



## 21. Styling

1. **Regular CSS**

   ```jsx
   // styles.css
   .orange{
       color: orange;
   }
   
   // StyleSheet.jsx
   import './styles.css'
   
   function StyleSheet(props){
   
       let conditionalClassName = props.color === "orange" ? 'orange' : 'black';
   
       return (
           <div>
               <p className="orange">Hello World</p>
               <p className={conditionalClassName}>Hello World</p>
           </div>
       )
   }
   
   // Problem with inline styling - If we have imported multiple css with same class names then issues might occur
   ```

   

2. **Inline Styling**

   ```jsx
   // StyleSheet.jsx
   function StyleSheet(props){
   
       let headerStyle = {
           fontSize: '65px',
           color: 'blue'
       }
   
       return (
           <div>
               <p className={headerStyle}>Hello World</p>
           </div>
       )
   }
   
   // Problem with inline styling - We cannot reuse in other components
   ```

   

3. **CSS Modules**

   ```jsx
   // styles.module.css
   .orange{
       color: orange;
   }
   
   // StyleSheet.jsx
   import styles from './styles.css'
   
   function StyleSheet(props){
   
       let conditionalClassName = props.color === "orange" ? 'orange' : 'black';
   
       return (
           <div>
               <p className={styles.orange}>Hello World</p>
           </div>
       )
   }
   
   // Best way to apply styling
   ```

   

4. **CSS in JS Libraries** (Styled Components)





## 22. Form Handling

```jsx
class Form extends Component{

    constructor(){
        super();
        this.state = {
            username: null,
            password: null
        }
    }

    handleUsernameChange = (event) => {
        const usernameText = event.target.value;
        this.setState({
            username: usernameText
        })
    }

    handlePasswordChange = (event) => {
        const passwordText = event.target.value;
        this.setState({
            username: passwordText
        })
    }

    handleFormSubmit = event => {
        event.preventDefault();
        const payload = {
            username: this.state.username,
            password: this.state.password
        }
        alert(payload);
    }

    render(){
        return (
            <div>
                <form onSubmit={this.handleFormSubmit}>
                    <div>
                        <label>Username: </label>
                        <input onChange={this.handleUsernameChange} value={this.state.username}/>
                    </div>
                    <div>
                        <label>Password: </label>
                        <input onChange={this.handlePasswordChange} value={this.state.password}/>
                    </div>
                    <button type="submit">Submit</button>
                </form>
            </div>
        )
    }
}
```





## 23. Lifecycle Method - Class Components

These are of 4 types

1. **Mounting** - Called when an instance of a component is being created and inserted into the DOM
   1. **constructor**
   2. static **getDerivedStateFromProps**
   3. **render**
   4. **componentDidMount**
2. **Updating** - Called when a component is re-rendered as a result of change in props/state.
   1. static **getDerivedStateFromProps**
   2. **shouldComponentUpdate**
   3. **render**
   4. **getSnapshotBeforeUpdate**
   5. **componentDidUpdate**
3. **Unmounting** - Called when a component is removed from the DOM
   1. **componentWillUnmount**
4. **Error** **Handling **- Called when there is an error during rendering, in lifecycle method, constructor of child component.
   1. static **getDerivedStateFromError**
   2. **componentDidCatch**



## 24. Mounting Lifecycle Method

1. **constructor**
   1. A special function called when a new component is ncreated
   2. Used for initializing state in class component
   3. Do Not call network calls here
2. static **getDerivedStateFromProps**
   1. Rarely used method
   2. Do Not call network calls here
3. **render**
   1. Used to render UI code in JSX.
   2. Do Not call network calls here
4. **componentDidMount**
   1. Called only once when the component is fully loaded.
   2. We can make network calls here.

```jsx
class Greet extends Component{
    constructor(){
        super()
        this.state = {}
    }

    componentDidMount(){
        console.log("Component Loaded...")
    }

    render(){
        return <div>Hello World</div>
    }
}
```



## 25. Updating Lifecycle Methods

1. static **getDerivedStateFromProps**
   1. Method is called every time a component is re-rendered
   2. We can set the state here
   3. Do not make network calls here
2. **shouldComponentUpdate**
   1. Check if the component should re-render
   2. This is used for performance optimization
   3. Do  not make networl calls here.
3. **render**
4. **getSnapshotBeforeUpdate**
   1. Called right before the changes from the virtual DOM are to be moved in the DOM
   2. Capture some information from mthe DOM
5. **componentDidMount**
   1. Called after the render is finished after re-render cycles
   2. We can make network calls by comparing prev state & new state



## 26. Fragments

1. By default we cannot return multiple HTML tags from a component.

2. Fragment can make that happen without using any div.

3. Used specifically in styling tables where we cannot add 'div'

   ```jsx
   const greet = () => {
       return <>
       <p>Hello</p>
       <p>World</p>
       </>
   }
   
   const greet = () => {
       return <React.Fragment>
           <p>Hello</p>
           <p>World</p>
       </React.Fragment>
   }
   ```

   

## 27. Pure Components

1. It automatically checks & compare state before re-rendering the component

   ```jsx
   class Greet extends PureComponent{
       
   }
   ```

   