##JQSelenium
==========
###General Information
This library was inspired by SeleniumJQuery (made by Nthalk for java, https://github.com/Nthalk/SeleniumJQuery). this C# library provides better usage than the jQuery Executor that comes with Selenium WebDriver.

###Installation
You can either download the source from this site OR you can install JQSelenium from nuget using 'install-package jqselenium'.

###Function Summary
The library provides the main manipulation methods in jQuery: </br>
* add
* addClass
* after
* addBack
* append
* appendTo
* attr
* before
* children
* click
* closest
* css
* find
* first
* get
* hasClass
* html
* last
* next
* nextAll
* nextUntil
* parent
* parents
* parentsUntil
* prev
* prevAll
* prevUntil
* remove
* removeClass
* siblings
* text
* val

The functions try to mimic the jQuery usage, so for further reference go to [the jQuery documentation](http://api.jquery.com/category/Manipulation/)

### What do you need?
You only need to have the Selenium WebDriver (you can find it [here](http://seleniumhq.org/projects/webdriver/)), import it into your project: 

```c#
using OpenQA.Selenium.Firefox;
```
and a basic understading of jQuery.


### How to?
The library is based in three structures: 
First you have a <b>jQueryFactory</b>. It recieves the WebDriver and executes the queries: 
```c#
var driver = new FirefoxDriver();
driver.Navigate().GoToUrl("URL-you-want-to-test");
var jqf = new JQueryFactory(driver);
```

Then you can execute queries with the Query method: 
```c#
	jqf.Query("body");
```
The Query method returns a <b>jQuerySelector</b> wich is a list of <b>jQueryTags</b>, from any jQuerySelector or jQueryTag you can execute any of the methods listed above and that way you interact with the DOM.

### Example
```c#
var driver = new FirefoxDriver(); // new webDriver
driver.Navigate().GoToUrl("http://api.jquery.com/find/"); //Navigate to the URL
var jqf = new JQueryFactory(driver); //Create the jQueryFactory
var _testing_selector = jqf.Query("h1"); //Query the element in the DOM you want to access
var _new_text = "Probando";
var _new_tag = "<p id = \"jQ-selenium\">" + _new_text + "</p>"; //new Element in the DOM will be added
_testing_selector.after(_new_tag); //Adds the element after the previously queried element
```

You can see more examples in the JQSelenium.Specs folder.

