PDOMongo
========

PDOMongo or PDO Mongo. PDO (PHP Data Object) for MongoDB. 
* <strong>Help me improve this small piece of software! Every help will be great and welcome.</strong>

Why use it?
========

PDOMongo is a small and straightforward piece of software. It encapsulates the Mongo connection, collection and database (CCD) and gives you a CRUD for your application. PDOMongo is also usefull because you can get any of the CCD at any time you want, to perform special actions that PDOMongo by itself doesn't supports.

How it works
========

PDOMongo is simple and straightforward as you can see below:

	<?php
		use PDOMongo;
		/*
		 * If you aren't using namespaces:
		 * require_once(__DIR__.'\PDOMongo.php');
		 */

		// Create a PDOMongo with default values
		$pdomongo = new PDOMongo(); 
		// Set the database
		$pdomongo->setDatabase('test');
		// Set the collection
		$pdomongo->setCollection('things');
	?>

Another example is shown below. For understand how to use another options, please, open the PDOMongo.php file and read the construction function.

	<?php
		use PDOMongo;
		/*
		 * If you aren't using namespaces, use:
		 * require_once(__DIR__.'\PDOMongo.php');
		 */

		$host = 'www.myDatabase.myHost.com';
		$database = 'mongoDatabase';
		// Create PDOMongo with custom values;
		$pdomongo = new PDOMongo($host,$database);
		// Set Collection
		$pdomongo->setCollection('things');
	?>

PDOMongo getters and setters
========

	<?php
		// PDOMongo created with defaults values;
		$pdo = PDOMongo();
		
		//Setters
		$pdo->setDatabase('myDatabase');
		$pdo->setCollection('myCollection');
		
		$returnConnection = $pdo->getConnection();
		$returnDatabase   = $pdo->getDatabase();
		$returnCollection = $pdo->getCollection();
	?>

Manipulation Database Objects
========

	<?php
		// PDOMongo created with custom values;
		$pdo = PDOMongo("https://myMongoDB.myHost.com","myDatabase","Admin","Password");
		$pdo->setCollection("myCollection");
		
		$element = array(
				'name' => 'PDOMongo',
				'detail' => 'Its a PDO to manipulate MongoDB for lazy people',
				'author' => 'pablohenrique'
			);
		
		$pdo->insert($element);
		
		$newElement = $element;
		$newElement['author'] = 'PabloHenrique';
		$pdo->update($element, $newElement);
		
		
		$returnObjects = $pdo->get('name', 'PDOMongo');
		
		// use '_id_' only if the id was generated by mongo.
		$returnObject = $pdo->get('_id_', 'd1827dsa9d8a67qwe8q09ueq817'); 
		
		// example of the use of 'id' when it wasn't generated by mongo
		$returnObject = $pdo->get('_id', '1'); 
		
		// use an array when multiples values are needed to find a specific record.
		$returnObject = $pdo->get(array(
				'name' => 'PDOMongo', 
				'detail' => 'Its a PDO to manipulate MongoDB for lazy people'
				));
				
		// use getAll to get all the elements from a collection
		$returnObjects = $pdo->getAll();
		
		//the delete method can thrown an exception.
		$pdo->delete('id', 'd1827dsa9d8a67qwe8q09ueq817', TRUE); //if TRUE, remove JustOne.
	?>

Thanks
========

Thanks for the PHP developers who created the Mongo classes for PHP.

[![endorse](https://api.coderwall.com/pablohenrique/endorsecount.png)](https://coderwall.com/pablohenrique)
