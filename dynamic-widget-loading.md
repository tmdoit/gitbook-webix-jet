# Dynamic Widget Loading

If you create custom Webix widgets and want to load their code on demand, you can split your code and import the bundles with widget code in **config()** of a Jet view.

```javascript
// views/about.js
import {JetView} from "webix-jet";
export default class AboutView extends JetView{
	config(){
		var widgets = import(/* webpackChunkName: "widgets" */ "modules/customGrid");
		return widgets.then(() => {

			return { rows:[
				{ type:"header", template:"Sales 2018" },
				{ view:"customGrid", autoConfig:true }
			]};

		});
	}
}
```

where **customGrid** is a file with a custom datatable, created with [webix.protoUI()](https://docs.webix.com/desktop__custom_component.html).

[Check out the demo >>](https://github.com/webix-hub/jet-demos/blob/master/sources/bundles.js)
