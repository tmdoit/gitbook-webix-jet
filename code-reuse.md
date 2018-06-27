# Code Reuse for Creating Similar Views

You can define a custom base class and use it instead of JetView for creating new views.

For example, if you need to create a lot of similar datatables, you can define a class like this:

```javascript
// views/basedatatable.js
import {JetView} from "webix-jet";
export default class BaseDatatable extends JetView {
    constructor(app, name, config){
        super(app, name);
        this.config = config;
    }
    config(){
        return { view:"datatable", columns: this.config.columns };
    }
}
```

Next you can create custom datatable views, each time providing a different set of columns:

```javascript
// views/products.js
import {BaseDatatable} from "webix-jet";
import products from "models/products"; //data collection
export default class ProductsView extends BaseDatatable {
    constructor(app, name){
        super(app, name, {
            columns:[
                {id:"id",header:""},
                {id:"product",header:"Product"},
                {id:"stock",header:"In stock"}
            ]
        });
    }
    init(view){
        view.parse(products);
    }
}
```

This technique allows you to store all the common elements (configuration handlers, logic, etc.) in the **BaseDatatable** class. The actual view files can define parameters to the base class and redefine any of its methods when necessary.
