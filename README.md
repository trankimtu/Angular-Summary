# 01 Installation & Command line
- Angular setup
- VS Code package
- Useful command 

# 02 Module - Component
- Introduce Module and Component
- 3 Steps create a component
- Create component by CLI (See Installation $ Command line)

# 03 Binding - String Interpolation - Property - Attribute
- String Interpolation ``` template: '<h2>{{ title }}</h2>'```
- Property binding
  ```
      <h2> {{ title }}</h2>      
      <h2 [textContent]="title"></h2>
      
      <img src="{{ imageUrl }}" />
      <img [src]="imageUrl" />
  ```
- Attribute binding
  ```
      <table>
        <tr>
          <td [attr.colspan]="colSpan"></td>
        </tr>
      </table>
  ```


# Service
- Decouple element with reusable service
- Normal class, no decorator

# Dependency Injection
- Passing parameter type service to constructor
- Register in ```provider``` of ```app.module.ts```

# Adding bootstrap
- See Installation & Command line.md

# Binding - Class - ngClass

# Binding - Style - ngStyle

# Binding - Event
- Click event
- Key stroke event
- Event Filtering
- Event bubbling

# Binding - 2 way
- Register NgModule in ```imports``` array of ```app.module.ts```
- [( ngModel )]

# 10 - Pipe
- Built in pipe
<ul>
  <li>Uppercase</li>
  <li>Lowercase</li>
  <li>Decimal</li>
  <li>Currency</li>
  <li>Percent</li>
  <li>Date - angular.io </li>
</ul>
- Custom pipe 
- Add parameter to custom pipe

# Exercise Title Case
- Enter a string to input field. The code will turn that string to title format

# Input property
- Pass input or state to component
- import Input
- @Input
- Aliasing

# Output property
- Raise event
- import Output
- @Output
- Passing event data when raise an event
- Aliasing

# Template Properties vs External file template
- 5 lines use properties
- more than 5 lines use external file

# Shadow DOM - View Encapsulation
- Prevent style leak

# ng-content & ng-container

# Exercise 5 Like component - Input property

# 6
# Directive - ngIf & hidden
- ngIf: Add or remove DOM to template
- hidden: Show or hide DOM to template. Hidden DOM still exist and take resource

# Directive - ngSwitchCase
- Example nav bar active

# Directive -ngFor - TrackBy
- ngFor: add loop to template
- Add or remove array item and show them out
- TrackBy: improve performance by not loading same object when the page refresh

# Leading Asterisk
- Explain how the code does behind the scene when using ```*``` such as ```*ngIf```

# Safe Traversal Operator - Null Prevent
- It's not possible to display Null value. Preventing this by traversal Operator

# Custom Directive

# Exercise 6  - Zippy
