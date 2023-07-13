# 1 - Introduction
Each input field of the form is class FormControl
FormGroup present a group of control of the form

# 2 - Template-driven forms vs Reactive forms
### Template-driven forms
Apply directive from the template. Angular will create the control object for us  
<ul>
  <li>Good for simple forms</li>
  <li>Simple validation</li>
  <li>Easier to create</li>
  <li>Less code</li>
  <li>Lest control over the validation of the form</li>
</ul>

### Reactive forms
We write code to create new instance of the control group and control objects
<ul>
  <li>More control over validation logic</li>
  <li>Good for complex forms</li>
  <li>Unit testable</li>
</ul>
