# Memoize JS function

Firstly create a JS memoize function:

```
memoize = (fn, map = new Map()) => {
  return (...args) => {
    const key = JSON.stringify(args);

    if (!map.has(key)) {
      map.set(key, fn(...args));
    }

    return map.get(key);
  };
};
```

Now we can call the memoize in the following way:

Sum function:
------------
```
const sum = function (a, b) {
  return a + b;
}
```

Memoize function declaration:
----------------------------

```
const memoizedFunction = memoize(sum);
```

Here is how it will work:

```
memoizedFunction(1, 3); // output is 4
memoizedFunction(2, 3); // output is 5
```

Here `memoizedFunction` is called `2` times.

Now again I call the function with the same parameter, 

```
memoizedFunction(1, 3);
```

It will now prevent calling the same function, `memoizedFunction` is called `2` times again instead.



