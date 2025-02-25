Airport Challenge
=================

====================================================================

User Story 1

As an air traffic controller
So I can get passengers to a destination
I want to instruct the airport to land a plane

Objects |  Properties                   | Methods(messages) | Outputs 
--------|-------------------------------|-------------------|----------
Plane   |  id @String                   | getId()           |@String
Airport |  airportPlanes @Array[@Plane] | landPlane(@Plane) |@Void

Initial thoughts for Test:
1. Need an Airport
2. Need to be able to land a Plane at the Airport
3. Need airportPlanes list length to increase by 1 when a Plane is landed (added).

Tests
1. airportPlanes length increases when landPlane is called.
2. landPlane should only add Plane instances to the airportPlanes list.
3. Edge case: Falsy values (null, undefined, zero, false) should not be added to the airportPlanes list.

---------

User Story 2

As the system designer
So that the software can be used for many different airports
I would like a default airport capacity that can be overridden as appropriate

Objects  | Properties                   | Methods(messages)            |Outputs 
---------|------------------------------|------------------------------|---------
Plane    | id @String                   | getId()                      |@String
Airport  | airportPlanes @Array[@Plane] | landPlane(@Plane)            |@Void
x        | airportCapacity @Integer     | increaseCapacityTo(@Integer) |@Void
                                        

Initial thoughts:
1. Need to set capacity
2. Need to make sure capacity can't be exceeded (i.e. no additional Planes can land when capacity is reached)
3. Need to make sure capacity can be overridden

Tests
4. Default capacity is set on Airport.
5. Additional Planes cannot land (i.e. be added to airportPlanes list) once capacity is reached.
6. Default capacity can be overridden.

---------

User Story 3

As an air traffic controller
To ensure safety
I want to prevent landing when the airport is full

Objects  | Properties                   | Methods(messages)           | Outputs 
---------|------------------------------|-----------------------------|-----------
Plane    | id @String                   | getId()                     | @String
Airport  | airportPlanes @Array[@Plane] | isAirportFull()             | @Boolean
x        | x                            | landPlane(@Plane)           | @Void
x        | airportCapacity @Integer     | increaseCapacityTo(@Integer)| @Void


Thoughts:
1. I've tested for this already (got ahead of myself):

Test
5. Additional Planes cannot land (i.e. be added to airportPlanes list) once capacity is reached.

---------

User Story 4

As an air traffic controller
So I can get passengers on the way to their destination
I want to instruct the airport to let a plane take off and confirm that it is no longer in the airport

Objects  | Properties                   | Methods(messages)           | Outputs
---------|------------------------------|-----------------------------|--------- 
Plane    | id @String                   | getId()                     | @String
Airport  | airportPlanes @Array[@Plane] | landPlane(@Plane)           | @Void
x        | x                            | takeOffPlane(@Plane)        | @Void
x        | airportCapacity @Integer     | increaseCapacityTo(@Integer)| @Void


Thoughts:
1. Need to identify Plane IDs in the airportPlanes array
2. Need to remove specified ID(s) from the array (takeOffPlane(@Plane))
3. Need to confirm that the Plane has left the airport

Tests
7. takeOffPlane removes Plane from airportPlanes list.

---------

User Story 5

As an air traffic controller
To avoid confusion
I want to prevent asking the airport to let planes take-off which are not at the airport, or land a plane that's already landed

Objects  | Properties                   | Methods(messages)           | Outputs 
---------|------------------------------|-----------------------------|-----------
Plane    | id @String                   | getId()                     | @String
x        | x                            | atAirport()                 | @Boolean
Airport  | airportPlanes @Array[@Plane] | landPlane(@Plane)           | @Void
x        | x                            | takeOffPlane(@Plane)        | @Void
x        | airportCapacity @Integer     | increaseCapacityTo(@Integer)| @Void


Thoughts:
1. Check airportPlanes array for Plane ID
2. If PlaneID does not exist in the airportPlanes array when takeOffPlane(@Plane) is called, do nothing
3. If PlaneID exists in the airportPlanes array when landPlane(@Plane) is called, do nothing

Tests
8. Planes which are not at the airport (i.e. in the airportPlanes list) cannot take off.
9. Planes which are already at the airport cannot land.

---------

Optional additional criteria (I have started thinking about this but not coded... would like to revisit once my wobbly existing code is improved and corrected following feedback, and hopefully approach it with a bit more confidence):

User Story A

As an air traffic controller
To ensure safety
I want to prevent takeOff when weather is stormy

Objects  | Properties                  |  Methods(messages)     | Outputs 
---------|-----------------------------|------------------------|----------
Weather  | x                           |  isSunny()             | @Boolean               

Thoughts:

1. Weather object needed (random number generator for weather outcomes?)
2. Need to restrict plane activity (i.e. do nothing) if takeOffPlane is called when weather is stormy.

Test 1a - Do nothing (return) if isSunny() === false when takeOffPlane is called.

User Story B

As an air traffic controller
To ensure safety
I want to prevent landing when weather is stormy

Objects  | Properties                  |  Methods(messages)     | Outputs 
---------|-----------------------------|------------------------|----------
Weather  | x                           |  isSunny()             | @Boolean               

Thoughts:

1. Need to restrict plane activity (i.e. do nothing) if landPlane is called when weather is stormy.

Test 1b - Do nothing (return) if isSunny() === false when landPlane is called.

User Story C

As an air traffic controller
To count planes easily
Planes that have landed must be at an airport

Objects  | Properties                   | Methods(messages)            | Outputs
---------|------------------------------|------------------------------|---------
Weather  | x                            | isSunny()                    | @Boolean 
Plane    | id @String                   | getId()                      | @String
x        | x                            | atAirport()                  | @Boolean
Airport  | airportPlanes @Array[@Plane] | landPlane(@Plane)            | @Void
x        | x                            | takeOffPlane(@Plane)         | @Void
x        | airportCapacity @Integer     | increaseCapacityTo(@Integer) | @Void


Thoughts: 

1. 
*****************************************





Resources used:
https://www.youtube.com/watch?v=IASaK1239y4
https://www.youtube.com/watch?v=0DFvcZwqbDQ
testing-framework.js file from Bob's bagels
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/constructor
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes

=====================================================================



```
         ______
        __\____\___
=  = ==(____DFA____)
           \_____\__________________,-~~~~~~~`-.._
          /     o o o o o o o o o o o o o o o o  |\_
          `~-.__       __..----..__                  )
                `---~~\___________/------------`````
                =  ===(_________)

```

Instructions
---------

* Feel free to use google, your notes, books, etc. but work on your own.
* Keep it SIMPLE - it's not nearly as complicated as it first may look.
* You must [submit your challenge](https://airtable.com/shrUGm2T8TYCFAmjN) by the deadline, wherever you get to.
* Use your own test framework and evidence your test-driven development by committing on passing tests.
* Please write your own README detailing how to install your project, how to run the tests, how you approached the problem and provide screenshots of interacting with your program.
* If you refer to the solution of another coach or student, please put a link to that in your README.
* Please create separate files for every class, module, and spec.

Steps
-------

1. Fork this repo, and clone to your local machine
2. `npm install` to install project dependencies
3. Convert stories into a representative domain model and test-drive your work.
4. Run your tests using `npm test` or `node specRunner.js`
5. OPTIONAL: [Lint](https://eslint.org/docs/user-guide/getting-started) your source code using `npx eslint src`.


Task
-----

We have a request from a client to write the software to control the flow of planes at an airport. The planes can land and take off provided that the weather is sunny. Occasionally it may be stormy, in which case no planes can land or take off.  Here are the user stories that we worked out in collaboration with the client:

#### Acceptance Criteria
```
As an air traffic controller
So I can get passengers to a destination
I want to instruct the airport to land a plane

As the system designer
So that the software can be used for many different airports
I would like a default airport capacity that can be overridden as appropriate

As an air traffic controller
To ensure safety
I want to prevent landing when the airport is full

As an air traffic controller
So I can get passengers on the way to their destination
I want to instruct the airport to let a plane take off and confirm that it is no longer in the airport

As an air traffic controller
To avoid confusion
I want to prevent asking the airport to let planes take-off which are not at the airport, or land a plane that's already landed

```

#### Extended Acceptance Criteria
```
As an air traffic controller
To ensure safety
I want to prevent takeOff when weather is stormy

As an air traffic controller
To ensure safety
I want to prevent landing when weather is stormy

As an air traffic controller
To count planes easily
Planes that have landed must be at an airport
```

Your task is to test drive the creation of a set of classes/objects to satisfy all the above user stories. You will need to use a random number generator to set the weather (it is normally sunny but on rare occasions it may be stormy). In your tests, you'll need to stub random behaviour to ensure consistent test behaviour.

Your code should defend against [edge cases](http://programmers.stackexchange.com/questions/125587/what-are-the-difference-between-an-edge-case-a-corner-case-a-base-case-and-a-b) such as inconsistent states of the system ensuring that planes can only take off from airports they are in; planes that are already flying cannot take off and/or be in an airport; planes that are landed cannot land again and must be in an airport, etc.
