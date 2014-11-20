Exédra
======
This version is no longer maintained. Please continue with Exedra2 at http://github.com/rosengate/exedra.
Thank you.

A fast and simple HMVC framework. Written ground up just to satisfy a simple to complicated application design (hopefully)

# Installation
1. Put exedra files anywhere you would like to, (make sure it's contained within a folder). 
	- 1.1 let say put it under www/exedra, or behind it, or anywhere.
2. On one of your planned site (let us say, www/mysite), add index.php, to serve as the main request handler.
	- inside that index.php, just include the Framework.php file, relative or absolutely.
3. Then Installation is done. No configuration required. Because you can use it as soon as you included the main framework file. (Framework.php)

# Some sneak peak
##### Scenario :
set up some re-write rule like this in your .htaccess :
```
RewriteRule ^/? index.php [L]
```
so, all the uri after your folder name will be interpreted by exedra, without including index.php.
fot the following example, let say, you put your application folder within www/mysite

### 1. Running the exedra
	apps::run(function($router)
	{
		// all routing codes are within this closure.
	});

### 2. Adding routes
##### 2.1 Simple
	$router->add("hello",function(){
		echo "hello world";
	})
	->add("hola",function(){
		echo "hai dunia";
	})
	->dispatch(); // dispatch the routes on localhost/mysite

##### 2.2 Multi-dispatch (or grouped dispatch)
	$router->add("world",function(){
	return response::json(Array(1,2,3));
	})->dispatch("hello"); // dispatch on additional 'hello' on your uri. example localhost/mysite/hello/world will execute this
	
	$router->add("dunia",function(){
	return "Hai di sana";
	})->dispatch("hai"); // example : localhost/mysite/hai/dunia

##### 2.3 Named parameter
	$router->add("[:myname]",function($param){
	echo "My name is ".$param['myname'];
	)->dispatch(); // localhost/mysite/eimihar will repond with "My name is eimihar"
	
##### 2.4 Mapping other application
	// dispatch the application inside apps_other folder.
	$router->add("apps_other:super")->dispatch("superapps");
	
	// dispatch the application from elsewhere.
	$router->add("apps_other:path=../some/path/myapps")->dispatch("faraway")
	
	// p/s : the specific routes will follow.
### 3. Application structure
```
apps
	_model
	_structure
	sub_apps1
		_template
		_controller
		_view
	sub_apps2
		_template
		_controller
		_view
apps_other
	appsname
		(follow the apps folder structure)
	appstwo
	(and the list go on..)
```

That's all for the little sneak peak about exedra ;) writing this wall of texts is much harder that writing codes.
Other than what has been mentioned, exedra also provides a lot of core feature such as :
- namespaced model design (yes you can still prefix the name. but i might soon deprecated it.)
- multiple application structure.
- independence application.
	- you map simply map other application onto your desired uri, the specific routes for the application follow after that.
- restful router
- number of common components : form, input, session, pagination, query-builder (db) and etc.
- and etc (End of Thinking Capacity)

That's all.

# WARNING
- i forgot to turn on all the error reporting mode, while development. so, expect thousands of errors!

# That's All
- By Eimihar El-Meruiy ;) you can contact me through newrehmi@gmail.com
