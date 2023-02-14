In service.md
```
    let service = new CoursesService();
```
        
Creating an instance of type CoursesService still couple the component and the service.<br>
This can’t test the component individually. <br>
Changing constructor, such as add parameter to it, leads to many changes in application code.<br>
Dependency Injection can fix this problem<br>
<br>

## Step 1: Passing the parameter ```service``` type ```CoursesService``` to constructor
```
// file: CoursesComponent.component.ts

import { Component } from '@angular/core';
import { CoursesService } from './courses.service';

// Decorator Function
@Component({
    selector: 'courses',
    template: `
        <h2> {{ title }}</h2>
        <ul>
        <li *ngFor="let course of courses">
            {{ course }}
        </li>
        </ul>
    `
})            

export class CoursesComponent {
    title = "List of courses";
    courses;

    constructor(service: CoursesService) {
        this.courses = service.getCourses();
    }
}
```

## Step 2: Register dependency injection in provider of app.module.ts
```
import { CoursesService } from './courses.service';
// file: app.module.ts 

import { CoursesComponent } from './courses.component'; // import component class
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { CourseComponent } from './course/course.component';

@NgModule({
  declarations: [
    AppComponent,
    CoursesComponent, //Register new component
    CourseComponent   //CLI register New component
  ],
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  providers: [
    CoursesService
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

Passing the parameter service type CoursesService to constructor, Angular will create an instance type CoursesService and pass to the constructor. This constructor has dependency type CourseService. CousesComponent is dependent on CoursesService.<br>
Angular will automatically create a parameter type CoursesService then pass it around constructor if needed.<br>
Later on, if we change the constructor such as pass a parameter to it, we don’t have to modify all the places where constructor appears. <br>
We need to instruct Angular create an instance type CoursesService and pass it around the constructor. This concept is called Dependency Injection.<br>
Dependency instructor mean providing or injecting the dependency of a class into constructor<br>
Angular has dependency injection framework built in. To register dependent, in app.module.ts, add all dependent in providers.<br>
In this case, we add CoursesService as providers in this model.<br>
If we have hundreds component use CoursesService, the only 1 CoursesService is created. This is singleton<br>
Missing register CoursesService will cause Error
```
ERROR Error: No provider for CourseService!
```

