# Style binding
```
import { Component } from '@angular/core';

@Component ({
  selector: 'courses',
  template: `
    <button [style.backgroundColor]="isActive ? 'blue' : 'lightblue'">Save</button>
  `
})

export class CoursesComponent {
  isActive = true;
}
```



```
// File: app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  canSave = true;
}
```

```
<!-- File: app.component.html -->
<button
  [style.backgroundColor]="canSave ? 'blue' : 'gray'"
  [style.color]="canSave ? 'white' : 'black'"
  [style.fontWeight]="canSave ? 'bold' : 'normal'"
>
  save
</button>
```
# ngStyle
Normally we encapsulate style in css file. Some situations need inline css, we can use this.
Jason with ```key``` represent css style, ```value``` is value
```
<!-- File: app.component.html -->
<button
  [ngStyle]="{
    'backgroundColor': canSave ? 'blue' : 'gray',
    'color' : canSave ? 'white' : 'black',
    'style' : canSave ? 'bold' : 'normal'
  }"
>
  save
</button>
```
