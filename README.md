Routerlith
========================

[Github](https://github.com/merry-goblin/routerlith)

### Purpose

The main purpose of Routerlith is to handle your routes in order to call controller's methods.

### Description

- Standalone
- Inspired by [dannyvankooten/PHP-Router](https://github.com/dannyvankooten/PHP-Router)
- Simple

### Sample

```
<?php

require_once(__DIR__."/../vendor/autoload.php");

$routing = array(
	'base_path' => '/',
	'routes'    => array(
		'home'      => array(
			'path'      => '',
			'action'    => 'Monolith\Acme\Controllers\HomeController.getAction',
			'methods'   => 'GET',
			'roles'     => 'anonymous',
		),
		'category'      => array(
			'path'      => 'cat/{id}',
			'action'    => 'Monolith\Acme\Controllers\CategoryController.getAction',
			'methods'   => 'GET',
			'roles'     => 'anonymous',
			'filters'   => array(
				'id'       => '([0-9]+)',
			),
		),
		'item'      => array(
			'path'      => 'cat/{catId}/item/{itemId}',
			'action'    => 'Monolith\Acme\Controllers\ItemController.getAction',
			'methods'   => 'GET',
			'roles'     => 'anonymous',
			'filters'   => array(
				'catId'     => '([0-9]+)',
			),
		),
	),
);

$routerlith = new \Monolith\Routerlith\Routerlith($routing);

$route      = $routerlith->getCurrentRoute();
$response   = $routerlith->dispatch($route, array());

//	try me :
//	http://www.mydomainname.com/
//	http://www.mydomainname.com/cat/1
//	http://www.mydomainname.com/cat/1/item/blue-chair

```

### Methods available

#### Monolith\Routerlith\Routerlith

- **constructor(routing) :**                      builds routing
- **addRouteModels(routing) :**                   completes routing
- **getRoute($requestUrl, $requestMethod) :**     gets an instance of Monolith\Routerlith\Route or null from an url and a http method (GET, POST ...)
- **getCurrentRoute() :**                         gets an instance of Monolith\Routerlith\Route or null from the current url
- **getRouteByName() :**                          builds a route from a model and parameters
- **generate() :**                                generates a relative path from a route
- **dispatch() :**                                calls the action of a route. An action is a method of a controller

--------------------------

author : [alexandre keller](https://github.com/merry-goblin)
