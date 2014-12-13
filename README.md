jsTool-core
===========

for ensure compatibility with old browsers it's recomended to add this code before scripts
``` html
<!--[if lt IE 9]>
    <script src="//cdnjs.cloudflare.com/ajax/libs/es5-shim/4.0.5/es5-shim.min.js"></script>
<![endif]-->
<!--[if lt IE 12]>
    <script src="//cdnjs.cloudflare.com/ajax/libs/es6-shim/0.21.1/es6-shim.min.js"></script>
<![endif]-->
```

global function 'fn' to sandbox all other definitions

fn.define(moduleName, dependencies?, definition)
------------------------------------------------

``` js
fn.define('moduleName', [ 'dependence_1', 'dependence_2', ..., function ( dependence_1, dependence_1, ...) {
	
	// add necessary stuff

	return definition;
} ]);
```

example
``` js
fn.define('isLargeString', [ '_', function ( _ ) {
	
	function isLargeString (str) {
		return _.isString(str) && str.length > 45;
	}

	return isLargeString;
} ]);
```

fn.require(dependencies, callback)
-----------------------------------

``` js
fn.require(['dependence_1', 'dependence_2'], function ( dependence_1, dependence_1 ) {
	
	// do desired stuff

} ]);
```

fn.run(dependencies || function) or just fn(dependencies || function)
---------------------------------------------------------------------

explicit injection mode
``` js
fn.run(['dependence_1', 'dependence_2', function ( dependence_1, dependence_1 ) {
	
	// do desired stuff

} ]);
```

implicit injection mode (dependencies will be automatically detected -not recomended when uglifying code- )
``` js
fn.run(function ( dependence_1, dependence_1 ) {
	
	// do desired stuff

});
```

fn.defer(function, timeout? (0) )
-----------------------------------

``` js
fn(function () { console.log('test 1'); });
fn.defer(function () { console.log('test 2'); });
fn(function () { console.log('test 3'); });
```

this will output
```
test 1
test 3
test 2
```

fn.defer(function, timeout? (0) )
-----------------------------------

``` js
fn(function () { console.log('test 1'); });
fn.defer(function () { console.log('test 2'); });
fn(function () { console.log('test 3'); });
```

this will output
```
test 1
test 3
test 2
```