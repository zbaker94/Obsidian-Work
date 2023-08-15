# Variables
### Booleans
Boolean variable names should be appended by the word `flag`
```js
const loadingFlag = true; ✔️
const isLoadingFlag = true; ❌

const previouslySelectedDefendantFlag = false; ✔️
const defendantWasPreviouslySelectedFlag = false; ❌
```

Notice that there is not an `is` or `has` or any other similar prepended word. `isLoggedInFlag` is redundant. Don't do it.

### Arrays
Array names should be appended with the word `list`. The noun that precedes the word `list` should be singular.

```js
const defendantList = []; ✔️
const defendantsList = []; ❌

const pendingUpdateList = [] ✔️
const pendingUpdates = [] ❌
```

### Components
[[Functional Components]] can be assigned to variables just like any other value (they're just functions). When doing so, it is important to PascalCase the name no matter what.

```jsx
const Component = <></>; ✔️
const component = <></>; ❌

const ComponentToRender = <></>; ✔️
const componentToRender = <></>; ❌
```

# File Structure
### Folders
Folders should generally contain an index.js or index.jsx file and be named the same as the variable that their index exports. To this end, index files should almost always only export a single value or object. 

#### For Components 
The index file should export a component that accepts any props and calls any hooks needed to perform the business logic the component requires. This Renderer component should then render 😲 another component that handles the layout and actual display (see [[Best practices for balancing customization with configuration and ensuring reusability#Renderers and Components|Renderers and Components (Container and Layout components)]]).  