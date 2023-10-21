#ngOnInit()

`ngOnInit` is a lifecycle hook in Angular that is implemented as a method within an Angular component. It is one of several lifecycle hooks that Angular provides, and it serves a specific purpose.<br>

The `ngOnInit` hook is called by Angular when the component is initialized and has been constructed. It is typically used for tasks that need to be performed once when the component is created, such as initialization of data, making initial HTTP requests, or setting up subscriptions.<br>

Here's a typical use case for `ngOnInit`:<br>
<ol>
  <li>**Data Initialization**: You might use `ngOnInit` to initialize the component's properties or data. For example, you can set default values, fetch initial data from a service, or prepare the component's state.</li>
  <li>**HTTP Requests**: If your component needs to make HTTP requests to fetch data from an API, `ngOnInit` is a good place to trigger those requests. It ensures that the data fetching occurs when the component is being initialized.</li>
  <li>**Subscriptions**: If your component needs to subscribe to events or observables (e.g., real-time updates), you would typically set up those subscriptions in `ngOnInit`. This is because it's safe to set up subscriptions when the component is being initialized and tear them down in the `ngOnDestroy` lifecycle hook to prevent memory leaks.</li>
</ol>


Here's an example of how `ngOnInit` is used within an Angular component:

```
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-my-component',
  templateUrl: 'my-component.html',
})
export class MyComponent implements OnInit {
  data: any;

  constructor() {
    // Constructor is where you typically inject services and dependencies.
  }

  ngOnInit() {
    // This is where you perform initialization, data fetching, or subscription setup.
    this.data = this.myService.getData(); // Example data initialization
  }
}
```

In this example, when an instance of `MyComponent` is created, the `ngOnInit` method will be called automatically by Angular, allowing you to perform necessary setup and initialization tasks.
