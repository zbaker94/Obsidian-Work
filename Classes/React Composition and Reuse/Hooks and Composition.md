## The role hooks play in component composition
- Separating useful logic that incorporates the [[React Lifecycle]] 
- Hooks can be composed to create reusable logic

```js
import { useState } from "react";

const useJokes = () => {
  const [joke, setJoke] = useState("No joke.");
  const onRequest = () => {
    fetch("https://api.chucknorris.io/jokes/random")
      .then(response => response.json())
      .then(joke => setJoke(joke.value))
      .catch(err => err);
    };
    return { joke, onRequest };
};

export default useJokes;
```

```js
import "useEffect" from "react"

const useEffectOnce = (callback, cleanup = () => {}) => {
	useEffect(() => {
		callback();
		return cleanup() 
	}, [])
}
```

``` js
import {useEffectOnce} from "HooksLibrary"
import useJokes from "./useJokes"

const useJokeOnMount = () => {
	const {joke, onRequest} = useJokes()

	useEffectOnce(() => {
		onRequest();
	})

	return joke;
}

export default useJokeOnMount
```