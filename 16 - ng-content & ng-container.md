# ng-content
Using ng-content to fill out template dynamically<br>
Content under class “heading” including ```div``` tag in File: ```app.component.html``` will replace the code ```<ng-content select=".heading"></ng-content>``` in File: ```bootstrap-panel.component.html```<br>
Content under class “ body” including ```div``` tag in File: ```app.component.html``` will replace the code ```<ng-content select=".body"></ng-content> in File: bootstrap-panel.component.html```


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

The code will be the same with:
```
<!-- File: bootstrap-panel.component.html  -->
<div class="panel panel-default">
    <div class="panel-heading">
        <div class="heading">Heading</div> 
    </div>
    <div class="panel-body">
        <div class="body">
            <h2>Body</h2>
            <p>Some Content here</p>
        </div>
    </div>
</div>
```

<!-- ============================================================================ -->
<!-- ============================================================================ -->
<!-- ============================================================================ -->

# ng-container
Similar to ```ng-content```, but ```ng-container``` just take the value ```Heading``` inside the tag ```<div class="heading">Heading</div>``` Without taking ```<div>``` tag <br>
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

Using component in ```app.component.html``` and define the filled in content with ```ng-container```
```
<!-- File: app.component.html  -->
<bootstrap-panel>
  <ng-container class="heading">Heading</ng-container>
  <div class="body">
    <h2>Body</h2>
    <p>Some Content here</p>
  </div>
</bootstrap-panel>
```

The code will be the same with:
```
<!-- File: bootstrap-panel.component.html  -->
<div class="panel panel-default">
    <div class="panel-heading">
        Heading <<< NO DIV 
    </div>
    <div class="panel-body">
        <div class="body">
            <h2>Body</h2>
            <p>Some Content here</p>
        </div>
    </div>
</div>
```
