For each of our reusable libraries, we have an index file that exports a default object which contains the entire library. In some cases, the libraries are broken up into smaller sub groupings (Form in ReactLibrary, for instance). These groups within the library should have their own folder with its own index file that exports the contents of that group. The main library should then import and re-export the sub group from its own index. This pattern can be nested an arbitrary amount of times as needed.

For example:

![[Pasted image 20230830105313.png]]

and the top level `index.js` would look something like the following:
```js
import libraryFile from "./libraryFile"
import Subgroup from "./SubGroup"

const Library = {
	libraryFile,
	Subgroup
}

export default Library
```
