# Module
<ul>
  <li>A container that groups related components. </li>
  <li>All Angular app has App module</li>
  <li>Inside App module there can be many modules, each of them responds to each area of the application such as Courses module, Messaging module, Instructor module, and Admin module</li>
</ul>

### Step 1: Create a module

```
  ng g m <module name>
  or
  ng generate module <module name>
```
A folder ```<module name>``` with the file ```<module name>.module.ts>``` is created
### Step 2: Register ```<module name>``` in ```app.module.ts```
In ```app.module.ts```
```
  import {} from './<module name>/<module name>.module'
  imports[
    <module name>.module,
  ]
```





# Component
Every Angular has a tree component start with Root component (App component)<br>
## 3 steps create component:

### Step 1: Create a component
In src/app<br>
Create courses. component.ts<br>
```
// file: courses.component.ts

import { Component } from '@angular/core';

// Decorator Function
@Component ({
  // Base on CSS
  // "courses"  for <courses>                  
  // ".courses" for <div class="courses"       
  // "#courses" for <div id="courses"          

  selector: 'courses',
  template: '<h2>Courses</h2>' 
})
export class CoursesComponent {

}
```

### Step 2: Register the component in a module
<ul>
  <li>In src/app/app.module.ts, add CourseComponent module.</li>
  <li>Name of import module is the name of the file without extension. This will be added automatically by “auto import” package of vs code. If not, install package “auto import”</li>
  <li>Missing register component cause error: ‘causes’ is not a known element</li>
</ul>

```
// file: app.module.ts 

import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';

import { CoursesComponent } from './courses.component'; // import component class

@NgModule({
  declarations: [
    AppComponent,
    CoursesComponent //Register new component
  ],
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

### Step 3: Add an element in an HTML markup
```
<!-- file: app.component.html -->

<h1>Angular</h1>
<courses></courses>

```
