# What's New

## Version 2.0 - November 22, 2018

- [getUrl()](part-ii-webix-jet-in-details/jetview-api.md#this-geturl) and [getUrlString()](part-ii-webix-jet-in-details/jetview-api.md#this-geturlstring) for [app](part-ii-webix-jet-in-details/jetapp-api.md#app-geturl) and view, url related tests and fixes
- removeView() of Webix widgets triggers destroy() of the Jet views inside them
- getSubView() and contains() can be called for JetApp
- refresh() of JetView and JetApp return promises
- view.refresh now work for views with sub-elements:

	There were 2 major issues in the previous solution

	a)
	rendering url was not calculated for top level views
	it was expected that for top level views user will call app.refresh
	but real usage is different

	b)
	The subviews were not destroyed but recreated during refresh.
	As result old subviews were kept in memory and complex side-effects were possible.

	As part of update app.refresh logic changed as well, not it triggers refresh
	of the top view, instead of using its own custom logic.

- app.refresh works when an app is inside a Webix Jet view
- [fix] destroy sub-app when root view of sub app is destroyed
- [update] order of destroy and init events

	Update changes the order of events.
	Now, when view A replaces view B, events will go like next

	- B.destroy()
	- A.init()

	To do so, we remove direct destructor() calls from the rendering callback
	and place the same call just after rendering new UI
	( after this point we don't need old view anymore )
- [add] subrouter to use with sub-modules
- [update] option to configure polyglot in the Locale plugin

## Version 1.6 - June 26, 2018

* new [WJET utility](part-iii-practical-tasks/wjet-utility-for-faster-prototyping.md) for faster prototyping
* JetView has the [refresh\(\) method](part-ii-webix-jet-in-details/jetview-api.md#this-refresh)
* better support for ES6 modules: [app.views](part-ii-webix-jet-in-details/app-config.md#code-splitting) can return a promise of an ES6 module, which can be used for code-splitting

## Version 1.5 - April 24, 2018

* the ability to compile a Jet app into a standalone bundle and [use it in other apps or as is](part-iii-practical-tasks/big-app-development.md#modules-and-large-app-development)
* the ability to compile a Jet app as a component and [use it as a Webix widget](part-iii-practical-tasks/big-app-development.md#using-jet-app-as-a-widget)
* [**this.$$\(\)**](part-ii-webix-jet-in-details/jetview-api.md#this-usdusd) returns [widgets from the current Jet view only](part-ii-webix-jet-in-details/referencing-views.md#5-referencing-webix-widgets)

## Version 1.4 - April 11, 2018

* JetView class instances can be created [in **config\(\)**](part-ii-webix-jet-in-details/views-and-subviews.md#jetview-constructor)

## Version 1.3 - January 11, 2018

* [TypeScript support](part-iii-practical-tasks/using-typescript.md)
* new API:
  * [getParam](part-ii-webix-jet-in-details/jetview-api.md#this-getparam) and [setParam](part-ii-webix-jet-in-details/jetview-api.md#this-setparam) methods to get/set URL parameters
  * [getUrl](part-ii-webix-jet-in-details/jetview-api.md#this-geturl)
* [_UrlParam_](part-ii-webix-jet-in-details/plugins.md#urlparam-plugin) plugin
* ability to set optional path for the [Locale plugin](part-ii-webix-jet-in-details/plugins.md#locale-plugin)
* ["app:user:login"](part-ii-webix-jet-in-details/inner-events-and-error-handling.md#app-user-login) and ["app:user:logout"](part-ii-webix-jet-in-details/inner-events-and-error-handling.md#app-user-logout) events

## Version 1.2 - December 12, 2017

* [_show_](part-ii-webix-jet-in-details/jetview-api.md#this-show) and [_getSubView_](part-ii-webix-jet-in-details/jetview-api.md#this-getsubview) APIs updated
* _this.ui_ updated
  * allows to define [custom HTML parent](part-ii-webix-jet-in-details/jetview-api.md#optional-container-parameter)
  * can be used with [JetView classes](part-ii-webix-jet-in-details/popups-and-windows.md#windows-as-jet-view-classes)
* ability to [remove _"!"_ from the hash URL](part-ii-webix-jet-in-details/routers.md#hiding-the-in-the-url)
* ability to [return a promise from the _config_ method of a view](part-ii-webix-jet-in-details/asynchronous-views.md#a-promise-returned-by-config-of-a-class-view)
* HashRouter supports [_config.routes_](part-ii-webix-jet-in-details/app-config.md#beautifying-the-url)
* views can define [string-to-string mapping](part-ii-webix-jet-in-details/app-config.md#changing-view-creation-logic)

## Webix Jet 1.0 - September 26, 2017

Major update after version 0.5:

* [views](part-i-basic-usage/creating-views.md) and [app modules](part-i-basic-usage/creating-apps.md) as ES6 classes
* using [Webpack]() as a module bundler
* ability to choose among [4 routers](part-ii-webix-jet-in-details/routers.md)
* ability to use [6 plugins](part-ii-webix-jet-in-details/plugins.md) for common tasks

