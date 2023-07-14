# Adding Validation
- Create a form
- Give focus to "First Name" input field and leave it unfocused with empty value
- Alert show up

### File: app.component.html
  ```
    <contact-form></contact-form>
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

### File: contact-form.component.html
  ```
    <form>
      <div class="form-group">
          <label for="firstName">First Name</label>
          <input
              required
              ngModel 
              name="firstName"
              #firstName="ngModel"
              (change)="log(firstName)"
              id="firstName"
              type="text" 
              class="form-control"
          >
          <div 
              class="alert alert-danger"
              *ngIf=" firstName.touched && !firstName.valid"
          >
              First Name is required
          </div>
      </div>
      <div class="form-group">
          <label for="comment">Comment</label>
          <textarea 
              ngModel
              name="lastName" 
              id="comment" 
              cols="30" 
              rows="5" 
              class="form-group"
          >
          </textarea>
      </div>
      <button class="btn btn-primary">Submit</button>
    </form>

  ```
