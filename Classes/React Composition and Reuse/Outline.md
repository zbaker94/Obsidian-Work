---
tags: clayton, class, react/reuse/composition
---
* **Reuse and Composition Introduction**
	- [[Why is reuse and composition important in software development]]
	- [[Reusable vs Useful]]
* **React Components and Composition**
	-  React component basics review
		*  [[Functional Components]]
		-  [[React Lifecycle]]
		*  [[Hooks]] 
	*  **Practical composition in React components**
		-  [[Coding/React/Principles/Encapsulation|Encapsulation]]
		-  [[Coding/React/Principles/Immutability|Immutability]]
		-  [[Coding/React/Principles/Separation of Concerns|Separation of Concerns]]
	*  **Building simple components and composing them to create complex UI elements.**
		- [[Consistent Patterns and Coding Standards]]
		- [[Form Example.excalidraw|Example form]]
	* **Creating configurable reusable components**
		- [[Best practices for balancing customization with configuration and ensuring reusability]]
* [[Hooks and Composition]]
* [[Layered Architecture|Layered architecture / incremental abstractions]]
* [[Example of Abstraction and Coding For Usability]]
* [[Communication]]
* **Benefits of shared component libraries**
	- Shared libraries to create consistent UX
	- Shared libraries to create consistent DX
	- Shared libraries to reduce refactoring time
	- Separation of concerns
* **Pitfalls of shared component libraries**
	- Unnecessary props
	- Perception of complexity
	- Scalability <- maintainability <- reusability
		- The more forms your component can take, the less reusable and readable it is
		- The less reusable a component is, the harder it is to maintain your components
		- The harder it is to maintain your components, the harder it is to scale your capability
* Building and maintaining a shared component library
	- Architecture
	- Standards for predictability
	- Separation of concerns
	- Composition and reuse
	- Component Usage and Extension
	- Customization / styling
	- Versioning and updates
	- Maintainability
		- This goes hand in hand with _reusability._ At the beginning when the application and the components are very lightweight, they're easy to maintain. But once the requirements start growing, components tend to become very complex and therefore less maintainable.
		- [https://www.freecodecamp.org/news/best-practices-for-react/](https://www.freecodecamp.org/news/best-practices-for-react/)
* Testing
	* General practices 
		- Positive and negative cases
		- TDD
	- Manual test cases
		- Closer to integration testing
		- Test new / repaired functionality and related areas
	* Automated unit testing for shared code
		- Test individual components in isolation
		- Test both the state and the props of a component 
		- Keep your tests fast
		- Avoid unnecessary set-up and tear-down operations, and avoid hitting external services or APIs (Mocking).
		- Architecting components properly and utilizing composition reduces the number of tests
		- Test edge cases
		- Stubs
	- The above standards are made possible and better by writing isolated, composable, reusable components.
	- "Separating state management from rendering logic improves the testability of our codebase"
		- https://medium.com/@johnmcdowell0801/an-incremental-approach-to-clean-react-redux-development-b122bc8124cc
* Advanced composition in React
	- Composition patterns
	- Composition anti-patterns
	- Guidelines for choosing a composition strategy
* CCSD Reusable libraries
	- React Library
		- Structure
		- Control
		- Form / FormControl
		- Layout
		- Stylewrapper
- Hooks
	- Structure
	- Usestate
	- useEffect
	- useMemo
	- Deep Compare Variants
	- API calls / React Query
		- Data fetching and caching
		- useMagistrateCourtAPI
		- Data providers
- Group project (?)