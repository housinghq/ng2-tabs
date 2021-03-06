# ng2-tabs

Simple tabs control for your angular2 applications using bootstrap3. Does not depend of jquery.
If you don't want to use it without bootstrap - simply create proper css classes. 
Please star a project if you liked it, or create an issue if you have problems with it.

## Installation

1. Install npm module:
    
    `npm install ng2-tabs --save`

2. If you are using system.js you may want to add this into `map` and `package` config:
    
    ```json
    {
        "map": {
            "ng2-tabs": "node_modules/ng2-tabs"
        },
        "packages": {
            "ng2-tabs": { "main": "index.js", "defaultExtension": "js" }
        }
    }
    ```

## Usage

Import `TabsModule` in your app and start using a component:

```html
<tabset [pills]="false" (onSelect)="doSomethingOnTabSelect($event)">
    <tab title="Tab title" [disabled]="false">
        <span *tabHeading>
            <b style="color: deepskyblue">Dynamic html</b> <i style="color: deeppink">tab heading</i>
        </span>
        Tab contents.
    </tab>
    ...
</tabset>
```

* `<tabset>` is a container for all tabs
    * `[pills]="true|false"` Specifies if bootstrap pills should be used instead of regular tabs
    * `(onSelect)="doSomethingOnTabSelect($event)"` Callback to be called when tab is being selected
* `<tab>` is a single tab item
    * `title` Simple tab title
    * `[disabled]="true|false` Indicates if current tab is enabled or disabled
    * `<span *tabHeading>...</span>` Allows to specify dynamic html content of the tab title 

## Sample

```typescript
import {Component} from "@angular/core";
import {TabsModule} from "ng2-tabs";

@Component({
    selector: "app",
    template: `
<div class="container">

    <!-- regular tabs -->
    <tabset>
        <tab title="About me">
            Its all about me.
        </tab>
        <tab title="Contacts">
            This is content of the contacts tab
        </tab>
        <tab title="Map" [disabled]="true">
            Content of the Map Tab
        </tab>
    </tabset>
    
    <br/><br/>
    
    <!-- tabs with custom heading templates -->
    <tabset>
        <tab>
            <span *tabHeading>
                <b style="color: deepskyblue">About</b> <i style="color: deeppink">me</i>
            </span>
            Its all about me.
        </tab>
        <tab>
            <span *tabHeading>
                <i style="color: deeppink">My</i> <b style="color: deepskyblue">contacts</b>
            </span>
            This is content of the contacts tab
        </tab>
        <tab title="Map">
            Content of the Map Tab
        </tab>
    </tabset>
    
    <br/><br/>
    
    <!-- pills tabs -->
    <tabset [pills]="true">
        <tab title="About me">
            Its all about me.
        </tab>
        <tab title="Contacts">
            This is content of the contacts tab
        </tab>
        <tab title="Map">
            Content of the Map Tab
        </tab>
    </tabset>

</div>
`
})
export class App {

}

@NgModule({
    imports: [
        // ...
        TabsModule
    ],
    declarations: [
        App
    ],
    bootstrap: [
        App
    ]
})
export class AppModule {

}
```

Take a look on samples in [./sample](https://github.com/pleerock/ng2-tabs/tree/master/sample) for more examples of
usages.
