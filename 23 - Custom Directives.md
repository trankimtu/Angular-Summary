Use custom directive to have more control over behavior of DOM element. <br>
For example, controlling input field to modify phone number from 1234567890 to (123)456-7890 or capital name in the field.
We can pass data to the directive using input property. <br>
 
Create new directive by cli: 
```
ng g d input-format
```
It will create 2 files: <br>
	- Unit test file <br>
	- Directive file <br>
The command also modify app.module.ts. Inside declaration, it adds InputFormatDirective<br>
(All components, pipes, and directive must register in Declarations array unless we will have run time error)


# Example 1
Select input box, console will output “on Focus”. Unselect input box, console will output “on Blur”<br>
In decorator function, selector is in ```[ ]```<br>
```focus``` and ```blur``` are 2 DOM events
```@HostListener('')``` need to pass a DOM event in<br>
```@HostListener('focus')``` listen to event focus of the input field. When the input field is on focus, it will raise an event which call method ```onFocus()```<br>
```@HostListener('blur')``` listen to event NOT focus of the input field. When the input field is NOT on focus, it will raise an event which call method ```onBlur()```<br>

```
// File: input-formatCurrency.directive.ts 

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
Add ```appInputFormat``` attribute to the template<br>
It will apply custom directive to the input field

```
<!-- File: app.component.html -->
<input type="text" appInputFormat>
```

# Example 2
Turn all letter inside input field to lower case when click outside of input field.<br>
import ```ElementRef``` to reference DOM element which is used to get and set value of the input field. Declare one in constructor for later using. ```nativeElement``` is built in Angular object allow us to access to DOM object<br>
```@HostListener('blur')``` listen to event NOT focus of the input field. When the input field is NOT on focus, it will raise an event which call method ```onBlur()```<br>
Method ```onBlur()``` does 2 job:
<ol>
	<li>Get value of input field then assign to ```value``` parameter</li>
	<li>Set value of input field equal to ```value.toLowerCase()```</li>
</ol>

```
// File: input-formatCurrency.directive.ts 
import { Directive, HostListener, ElementRef } from '@angular/core';

@Directive({
  selector: '[appInputFormat]'
})

export class InputFormatDirective {
  constructor(private el: ElementRef) { }

  @HostListener('blur') onBlur() {
    let value: string = this.el.nativeElement.value; // Get value of input field then assign to value parameter
    this.el.nativeElement.value = value.toLowerCase(); // Set value of input field equal to value.toLowerCase()
  }
}
```
Add ```appInputFormat``` attribute to the template<br>
It will apply custom directive to the input field
```
<!-- File: app.component.html  -->
<input type="text" appInputFormat>
```

# Example 3 - Multiformat
In case we have multi format, one place is lower case, another place is upper case. <br>
To tell the directive about the target format, we use input property

```
// File: input-formatCurrency.directive.ts 
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
```
<!--  File: app.component.html  -->
<input type="text" appInputFormat [format]="'uppercase'">
<input type="text" appInputFormat [format]="'lowercase'">
```
Input “uppercase” to the leftbox, it will automatically change to “UPPERCASE” when the box is unselected <br>
Input “LOWERCASE” to the right box, result will be “lowercase”

# Use input property for directive
In the code above, we apply directive as attribute. Then use property binding to set the target format
```
<input type="text" appInputFormat [format]="'uppercase'">
```
Since we have only one input property which is uppercase, It would be nicer to set the target format while apply the directive as an attribute<br>
Alias the selector ```appInputFormat``` in ts file
```
// File: input-formatCurrency.directive.ts 
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
Bind it to string ```'uppercase'```
```
<!-- File: app.component.html  -->
<input type="text" [appInputFormat]="'uppercase'">
```

