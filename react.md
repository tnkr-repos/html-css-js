## WHY USE FRONTEND FRAMEWORKS

- In 2010s, all websites were rendered on the server -> websites are assembled on a web server based on data and templates. The resulting HTML, CSS and JavaScript code is sent to the client side (the web browser) that requested the page. The browser then takes this code and prints (renders) it on the screen. For eg. websites built with WordPress. JavaScript was used just for small dynamics (simple animations, hover effects, etc.) with the help of a library called jQuery (since it used to make JavaScript work the exact same way on all the browsers)
- As JavaScript usage in websites increased, development of web applications started, which then led to the rise of single-page applications (SPAs). These are webpages that are rendered on the client and not on the web server (Client-side rendering). The data which the web application needs comes from the backend in form of API, and the application consumes this data and renders a screen for each view of the application. These SPAs feel like we are using a native desktop or phone application. So you can click on links, or submit forms without the page ever reloading
- Server-side rendering is gaining popularity again driver by frameworks built on top of modern client-side rendering frameworks. For e.g. NextJS, Remix, etc. 
- [Modern Frontend](./images/modern_frontend.png)
- Front-end web applications are about dealing with data and displaying it in a nice UI. So it receives the data, changes the data as the user uses the application, and it always displays the current data on the screen. So the main job of any application (specially SPA) in to keep the UI in sync with the data (make sure that the UI always displays the current state of the data)
- In the real world each piece of data is called a piece of state
- Problems with JavaScript:
  - Requires lots of direct DOM manipulation and traversing (imperative)
  - State (such as simple text or numbers) are simply stored right in the DOM (in the HTML rather than in a central place in the application)
- Advantages of Frameworks:
  - Solve the problem of keeping data and UI in sync (Different frameworks have different ways of solving this problem, but the end goal remains the same for all)
  - Enforcing a correct way of structuring and writing code, thus solving the problem of spaghetti code

## WHAT IS REACT

- React is a JavaScript library for building UI
- Components are building blocks of UI in React. We build complex UIs by building and combining multiple components
- To describe each component we use a declarative syntax called JSX. We tell React how a component (and basically the entire UI) is based on the current data (state)
- React is an abstraction away from the DOM and we don't have to manipulate it directly. We tell React what changes are necessary depending on the current state using JSX, but we don't tell React how to do it (how to manipulate the DOM to get these changes reflected on the UI)
- How does React update the UI if we never touch the DOM -> Based on our initial state, React will render a UI using the components that we wrote using JSX. Based on some event (like a button click) the state might change. Whenever the state changes, we manually update the state in the app, and React will automatically re-render the UI to reflect the latest state. So "React reacts to state changes by re-rendering the UI"
- React is a library because it is only the "view" layer. So to build a complete real world application we need to choose multiple external libraries to add to our project (For e.g. for routing, or data fetching). To address this there are multiple frameworks built on top of React (which contains features that React is missing out-of-the-box such as NextJS or Remix)

## HOW TO USE PURE REACT?
- Create an `index.html` file in the root project directory with the `react` and `react-dom` libraries added as scripts to the `head` section (as mentioned in React documentation)
- `body` should contain a `div` element with a class of `root` (as per standard React practice)
- The `react` library contains the core React stuff, like state, components, etc. So it is the interface of how to interact with React
- The `react-dom` library is the rendering layer which can render React components into the DOM. Since we want to render components into the browser, so we use this. React can be used for building other things as well (such as native desktop applications using React Native) and in those cases, `react-dom` library won't be necessary (we might have to use a different library)
- Create a component (a JavaScript function whose name starts with an uppercase letter and returns some HTML code - This HTML will determine our UI). We can't use JSX as we don't have the tooling to convert JSX back to JavaScript
```javascript
function App() {
  return React.createElement("header"); // React object comes from the React core library included in our HTML
  // Use the createElement property to create an element
}
```
- To render this component on the webpage we need to use `ReactDOM` library features. We will choose the `div` with the `class` of `root` as our root element (meaning everything will be created inside of that `div`), and then create a new element using the `App` component
```javascript
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(React.createElement(App));
```
- This will create a `header` inside of the `div`, but since there is no content, nothing shows up on the browser. To add content, we can add more parameters to the `createElement()` function -> It accepts a second argument called `props` and a third argument called `children`, where we can pass a string which will then become the content of the element
```javascript
function App() {
  return React.createElement("header", null, "Hello React");
}
```
- We can use normal JavaScript code to show values in the browser (For e.g. the current time)
```javascript
function App() {
  const time = new Date().toLocaleTimeString();

  return React.createElement(`header`, null, `Hello React! It's {time}`)
}
```
- We can also use the concept of `state` to get React to manually update the DOM upon a trigger
```javascript
function App() {
  const [time, setTime] = React.useState(new Date().toLocalTimeString());

  React.useEffect(function() {
    setInterval(function() {
      setTime(new Date().toLocalTimeString())
    }, 1000);
  }, []);
}
```

## HOW TO SETUP A NEW REACT PROJECT?

- Most common solutions include:
  - `create-react-app` tool:
    - Complete starter kit for React applications
    - All common development tools are preconfigured out-of-the-box specifically for React such as development server, Webpack (for module bundling), linter (ESLint), code formatter (Prettier), testing library (Jest), Fable (for enabling latest JavaScript features)
    - Developed a long time ago, and so uses a slow and outdated technology (such as WebPack bundler)
    - Not to be used for real world applications (but is fine for tutorials) due to its slow refresh times
    - Command - `npx create-react-app <project_name>`
      - Follow any subcommand necessary for vulnerability management - `npm audit fix --force`
      - This creates a similar folder structure as we would have achieved using `npm init`. All JavaScript projects have a build tool associated with them
      - `package.json` file contains meta data about the project
      - `node_modules/` directory contains all the installed npm packages
      - `src/` folder will contain all the source code will go
      - `public/` folder will contain all the assets (such as images, favicon, and `index.html` file)
      - Causes a lot of breaking changes and prefer to use `vite` always
  - `vite` build tool:
    - To be used for modern real-world apps
    - Modern build tool (like WebPack) that contains a template for setting up React applications
    - Manual setup of developer tools (such as ESLint, Prettier, Jest, etc) is required
    - Provides Hot Module Reloading (changes made in code show up instantly without having to manually reload the page) and fast bundling
  - Use `NextJS` or `Remix` (React frameworks)
    - As per advice from React team in React Documentation
    - React framework contains things like routing, data fetching, and server-side rendering (things which React does not provide out-of-the-box)
    - A framework built on top of the React library which makes it easier to create real world application than just vanilla React
    - Only makes sense for building actual products

## 