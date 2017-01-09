__Creational Design Patterns__

___Abstract Factory___  
*  Intent
  *  Provide an interface for creating families of related or dependent objects without specifying their concrete classes.
  *  A hierarchy that encapsulates: many possible "platforms", and the construction of a suite of "products".
  *  The new operator considered harmful.  
*  Problem  
  *  If an application is to be portable, it needs to encapsulate platform dependencies. These "platforms" might include: windowing system, operating system, database, etc. Too often, this encapsulatation is not engineered in advance, and lots of #ifdef case statements with options for all currently supported platforms begin to procreate like rabbits throughout the code.


___Builder___  
Separates object construction from its representation  

___Factory Method___  
Creates an instance of several derived classes  

___Object Pool___  
Avoid expensive acquisition and release of resources by recycling objects that are no longer in use  

___Prototype___  
A fully initialized instance to be copied or cloned  

___Singleton___  
A class of which only a single instance can exist  
