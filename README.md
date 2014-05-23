exedra
======

A fast and simple HMVC framework. Written ground up just to satisfy a simple to complicated application design (hopefully)

Installation :
1. Put exedra files anywhere you would like to, (make sure it's contained within a folder), 
1.1 let say put it under www/exedra, or behind it, or anywhere.
2. On one of your planned site (let us say, www/mysite), add index.php, to serve as the main request handler.
2.1 inside that index.php, just include the Framework.php file, relative or absolutely.
3. Then Installation is done. No configuration required. Because you can use it as soon as you included the main framework file. (Framework.php)

Some sneak peak :
1. running the exedra
apps::run(function($router)
{
	// all routing codes are within this closure.
});

1. adding routes :
1.1 simple
$router
->add("hello",function(){
	echo "hello world";
})
->add("hola",function(){
	echo "hai dunia";
})
->dispatch(); // dispatch the routes on localhost/mysite

1.2 multi-dispatch (or grouped dispatch)
$router->add("world",function(){
return response::json(Array(1,2,3));
})->dispatch("hello"); // dispatch on additional 'hello' on your uri. example localhost/mysite/hello/world will execute this

$router->add("dunia",function(){
return "Hai di sana";
})->dispatch("hai"); // example : localhost/mysite/hai/dunia

1.3 named parameter
$router->add("[:myname]",function($param){
echo "My name is ".$param['myname'];
)->dispatch(); // localhost/mysite/eimihar will repond with "My name is eimihar"

That's All for the sneak peak about exedra's basic routing ;) writing this wall of texts is much harder that writing codes. >,<
Anyway, exedra provides lot of features such as :
- namespaced model design (yes you can still prefix the name. but i might soon deprecated it.)
- multiple application structure.
- independence application.
- restful router
- number of common components : form, input, session, pagination, query-builder (db) and etc.
- and etc (End of Thinking Capacity)

That's all

WARNING
======
- i forgot to turn on all the error reporting mode. so, expect a thousand of errors!

That's All
======
- By Eimihar El-Meruiy ;)
