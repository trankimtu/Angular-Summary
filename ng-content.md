# ng-content
Using ng-content to fill out template dynamically<br>
Content under class “heading” in File: ```app.component.html``` will replace the code ```<ng-content select=".heading"></ng-content>``` in File: ```bootstrap-panel.component.html```<br>
Content under class “ body” in File: ```app.component.html``` will replace the code ```<ng-content select=".body"></ng-content> in File: bootstrap-panel.component.html```


In component template, use ```ng-content select``` to set what need to fill in
```
<!-- File: bootstrap-panel.component.html  -->

<div class="panel panel-default">
    <div class="panel-heading">
        <ng-content select=".heading"></ng-content> 
    </div>
    <div class="panel-body">
        <ng-content select=".body"></ng-content>
    </div>
</div>
```

Using component in ```app.component.html``` and define the filled in content
```
<!-- File: app.component.html  -->
<bootstrap-panel>
  <div class="heading">Heading</div>
  <div class="body">
    <h2>Body</h2>
    <p>Some Content here</p>
  </div>
</bootstrap-panel>
```
