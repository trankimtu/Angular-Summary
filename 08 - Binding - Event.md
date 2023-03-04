Use to handle event raise from the DOM such as key stroke, mouse movement, click 

# Event Binding

## Click Event
```
import { Component } from '@angular/core';

@Component ({
  selector: 'courses',
  template: `
    <button (click)="onSave($event)">Save</button>
  `
})

export class CoursesComponent {
  onSave($event: any) {
    console.log("Button was clicked", $event);
  }
}

```
## Key stroke event

```
import { Component } from '@angular/core';

@Component ({
  selector: 'courses',
  template: `
    <input (keyup)="onKeyUp($event)" />
  `
})

export class CoursesComponent {
  onKeyUp($event) {
    if ($event.keyCode === 13) console.log("ENTER was pressed");
  }
}

```

## Event Filtering
```
import { Component } from '@angular/core';

@Component ({
  selector: 'courses',
  template: `
    <input (keyup.enter)="onKeyUp()" />
  `
})

export class CoursesComponent {
  onKeyUp() {
    console.log("ENTER was pressed");
  }
}

```

## Event Bubbling

To stop event bubbling, call stopPropagation
Outer click event won’t be handler

```
import { Component } from '@angular/core';

@Component ({
  selector: 'courses',
  template: `
    <div (click)="onDivClicked()">
      <button (click)="onSave($event)">Save</button>
    </div>
  `
})

export class CoursesComponent {
  onDivClicked() {
    console.log("Div was clicked");
  }

  onSave($event) {
    $event.stopPropagation();
    console.log("Button was clicked", $event);
  }
}

```
