Shadow DOM allows us to apply scoped styles to elements without bleeding out the outer world<br>
# Javascript Example
```
el.innerHTML = `
  <style> h1 { color: red } </style>
  <h1>Hello</h1>
`;
```

This style is leak. Not only the h1 we want to set red but also all h1 get red.<br>
We want the style only value in its scope which is its component. Shadow DOM is used.
```
var el = document.querySelector('favorite');
var root = el.createShadowRoot();
root.innerHTML = `
  <style> h1 { color: red } </style>
  <h1>Hello</h1>
`;
```
# Angular

