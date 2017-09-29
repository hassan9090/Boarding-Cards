# Boarding-Cards

Description 
----------------------------------------------
Trip class shorts your unordered boarding cards. 
Each ticket must have destination and source. 
vehicle, seat, gate members are not mandatory.

#### Dependencies
- PHP 5.3 or above

#### Extending class
* You can use ArraySort to sort anything, not only boarding cards.
* You can create new type of cards like plane, train, bus or whatever you want. (Default: CommonCard)
* You can able to create a gift class that you can give a track to the your shipping.
* If you would like you can create another kind of sort algorithm by extending SortInterface. 

Files 
----------------------------------------------
    index.php
    src
    ├── bootstrap.php
    └── lib
        └── boardingcards
            ├── assets
            │   ├── CardAbstract.php
            │   ├── CardFactory.php
            │   ├── TransportableAbstract.php
            │   ├── cards
            │   │   └── CommonCard.php
            │   └── transportable
            │       └── Person.php
            ├── modules
            │   └── trip
            │       └── Trip.php
            └── utils
                ├── interfaces
                │   └── SortInterface.php
                └── sorters
                    └── ArraySort.php

Usage 
----------------------------------------------
#### Include bootstrap file.
    require_once 'src/bootstrap.php';

#### Create two tickets
    $tickets = array(
      CardFactory::create(array(
        'source' => 'Metro Station',
        'destination' => 'Dubai Airport',
        'vehicle' => 'metro',
        'seat' => null,
        'gate' => null
      )),
      CardFactory::create(array(
        'source' => 'Marina',
        'destination' => 'Metro Station',
        'vehicle' => 'taxi',
        'seat' => null,
        'gate' => null
      ))
    );

#### Create three passengers
    $passengers = array(
      new Person('hassan'), 
      new Person('ali'),
      new Person('ahmed')
    );

#### Give the correct order to the crowd
    $Trip = new Trip($passengers, $tickets);
    $route = $Trip->sortTickets()->getTickets();
    $passenger = $Trip->getPassengers();
    
$route will be an array of the ordered tickets. If you would like you can also get passengers by calling getPassengers() method like above.

Triggering test 
----------------------------------------------
$ php index.php

