Use custom directive to have more control over behavior of DOM element. We can pass data to the directive using input property. <br>
 
Create new directive by cli: 
```
ng g d input-format
```
It will create 2 files: <br>
	- Unit test file <br>
	- Directive file <br>
The command also modify app.module.ts. Inside declaration, it adds InputFormatDirective

# Select input box, console will output “on Focus”. Unselect input box, console will output “on Blur”

## File: input-formatCurrency.directive.ts 
```
import { formatCurrency } from '@angular/common';
import { Directive, HostListener } from '@angular/core';

@Directive({
  selector: '[appInputFormat]'
})
export class InputFormatDirective {
  @HostListener('focus') onFocus() {
    console.log("on Focus");
  }
  @HostListener('blur') onBlur() {
    console.log("on Blur");
  }
  constructor() { }
}
```
## File: app.component.html
```
<input type="text" appInputFormat>
```

# Turn all letter inside input box to lower case when the input box is not selected.
## File: input-formatCurrency.directive.ts 
```
import { Directive, HostListener, ElementRef } from '@angular/core';

@Directive({
  selector: '[appInputFormat]'
})

export class InputFormatDirective {
  constructor(private el: ElementRef) { }

  @HostListener('blur') onBlur() {
    let value: string = this.el.nativeElement.value;
    this.el.nativeElement.value = value.toLowerCase();
  }
}
```
## File: app.component.html 
```
<input type="text" appInputFormat>
```

# Multiformat
In case we have multi format, one place is lower case, another place is upper case. <br>
To tell the directive about the target format, we use input property

## File: input-formatCurrency.directive.ts 
```
import { Directive, HostListener, ElementRef, Input } from '@angular/core';

@Directive({
  selector: '[appInputFormat]'
})

export class InputFormatDirective {
  
  @Input('format') format: string | undefined;

  constructor(private el: ElementRef) { }

  @HostListener('blur') onBlur() {
    let value: string = this.el.nativeElement.value;
    if (this.format == 'lowercase')
      this.el.nativeElement.value = value.toLowerCase();
    else
      this.el.nativeElement.value = value.toUpperCase();
  }
}
```
## File: app.component.html 
```
<input type="text" appInputFormat [format]="'uppercase'">
<input type="text" appInputFormat [format]="'lowercase'">
```
Input “uppercase” to the leftbox, it will automatically change to “UPPERCASE” when the box is unselected <br>
Input “LOWERCASE” to the right box, result will be “lowercase”

# Use input property for directive when there's only 1 format
When we have only one input property which is uppercase, we will set the format to apply to the directive
## File: input-formatCurrency.directive.ts 
```
import { Directive, HostListener, ElementRef, Input } from '@angular/core';

@Directive({
  selector: '[appInputFormat]'
})

export class InputFormatDirective {
  
  @Input('appInputFormat') format: string | undefined;

  constructor(private el: ElementRef) { }

  @HostListener('blur') onBlur() {
    let value: string = this.el.nativeElement.value;
    if (this.format == 'lowercase')
      this.el.nativeElement.value = value.toLowerCase();
    else
      this.el.nativeElement.value = value.toUpperCase();
  }
}
```
## File: app.component.html 
```
<input type="text" [appInputFormat]="'uppercase'">
```

