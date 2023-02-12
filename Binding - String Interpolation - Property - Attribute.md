# Interpolation
```
// file: courses.component.ts

import { Component } from '@angular/core';

// Decorator Function
@Component({
    selector: 'courses',
    template: '<h2>{{ title }}</h2>' // Data binding

})            

export class CoursesComponent {
    title = "List of courses"; 
}
```

# Property Binding
Angular translate String Interpolation {{ }} into Property Binding [ ] at compile time.<br>
In the code, we bind “textContent” property of “h2” DOM element to title field of "title" component
```
@Component ({

  selector: 'courses',
  template: `
      
      <h2> {{ title }}</h2>      
      <h2 [textContent]="title"></h2>
      
      <img src="{{ imageUrl }}" />
      <img [src]="imageUrl" />
  `
})

export class CoursesComponent {
  title = "List of courses";
  imageUrl = "http://lorempixel.com/400/200";
}

```


# Attribute Binding
DOM (Document Object Model) is a model of object that represent the structure of a document. It’s a tree of object in memory.<br>
HTLM is markup language that is used to represent DOM in text.<br>
When using binding, make sure we bind the property of the DOM object, not attribute of HTML element.<br>
Most of attribute of HTML element has 1 to 1 mapping to property of DOM object.<br>
There’re some exception such that HTML attribute does not have the representation in the DOM (DOM object does not have property “colspan”) and vice versa, property of DOM does not have representation in HTML (property textContent of h1 does not have representation in DOM). <br> 

```
import { Component } from '@angular/core';
@Component ({

  selector: 'courses',
  template: `
    <table>
      <tr>
        <td [colspan]="colSpan"></td>
      </tr>
    </table>
  `
})

export class CoursesComponent {
  imageUrl = "";
  colSpan = 2;
}
```
The code above will come up with error
```
Can't bind to 'colspan' since it isn't a known property of 'td'.
```
In this case, use “attr” to target colSpan attribute of markup:
```
<table>
  <tr>
    <td [attr.colspan]="colSpan"></td>
  </tr>
</table>
```




