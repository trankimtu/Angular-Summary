# ngModel's control object

### File: app.module.ts
```
imports: [
  BrowserModule,
  AppRoutingModule,
  FormsModule
],
```

### File: app.component.html
```
<contact-form></contact-form>
```
### File: contact-form.component.html
<ul>
  Missing the name attribute will cause the error: 
 <li>If ngModel is used within a form tag, either the name attribute must be set or the form control must be defined as 'standalone' in ngModelOptions</li>
  <li>It happens because it needs a way to distinguish these control objects when we have more than 1 input using ngModel</li>
</ul>

We will show the control object of ngModel in the console. To do that, we make a template parameter```#firstName``` and set it to ```ngModel``` value then raise an event to pass it to the log method <br>

```
<form>
    <div class="form-group">
        <label for="firstName">First Name</label>
        <input
            ngModel 
            name="firstName"
            #firstName="ngModel"
            (change)="log(firstName)"
            id="firstName"
            type="text" 
            class="form-control"
        >
    </div>
    <div class="form-group">
        <label for="comment">Comment</label>
        <textarea 

            id="comment" 
            cols="30" 
            rows="10" 
            class="form-control"
        >
        </textarea>
    </div>
    <button class="btn btn-primary">Submit</button>
</form>

```

### File: contact-form.component.ts 
```
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'contact-form',
  templateUrl: './contact-form.component.html',
  styleUrls: ['./contact-form.component.css']
})
export class ContactFormComponent {

  log(x : any) {
    console.log(x);
  }
}

```
