[⬅️ Back to Table of Contents](README.md)

# Shallow vs Deep Cloning

Shallow cloning copies only the first level of properties. If a property is a reference (like an object or array), only the reference is copied not the actual nested data.

### Shallow copy example

```javascript
const original = {
  name: "Sunil",
  address: { city: "Dubai" },
};

const shallowCopy = { ...original };

shallowCopy.name = "Ali";
shallowCopy.address.city = "Riyadh";

console.log(original.name);       // "Sunil" (✔️ unchanged)
console.log(original.address.city); // "Riyadh" (❗ changed)

```

```javascript
const original = {
  name: "Sunil",
  address: { city: "Dubai" },
};

const deepCopy = structuredClone(original);

deepCopy.address.city = "Riyadh";

console.log(original.address.city); // "Dubai" (✔️ unaffected)

```

| Type    | Copies Nested Objects? | Example Method      |
| ------- | ---------------------- | ------------------- |
| Shallow | ❌                      | `Object.assign()`   |
| Deep    | ✅                      | `structuredClone()` |


### Other Deep Clone Methods:

Using JSON.parse(JSON.stringify(obj))

```
const deep = JSON.parse(JSON.stringify(original));
```