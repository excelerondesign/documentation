A debounced function is run after a defined delay.

The function below has two parameters:

-   passedFunction: the function normally given to eventListeners to run.
    -   Can be an anonymous function e.g. function() {...}
-   delay: amount of time to wait before firing function
    -   Defaults to 200ms

```js
function debounced(passedFunction, delay = 200) {
	let timerId;

	//return function with arguments from passed function
	return function(...args) {
		//if timerid exists, clear it and start a new one
		if (timerId) {
			clearTimeout(timerId);
		}

		//since timerId is always unset, we must set it
		timerId = setTimeout(() => {
			//run passedFunction with ...args
			passedFunction(...args);

			//unset timerId
			timerId = null;

			//wait this long before you fire this function
		}, delay);
	};
}
```

Based off of [this article](https://codeburst.io/throttling-and-debouncing-in-javascript-646d076d0a44)
