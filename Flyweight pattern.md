### Flyweight Pattern

Some programs require a large number of objects that have some shared state among them. For example a game of war, where there
is a large number of soldier objects; a soldier object maintain the graphical representation of a soldier, soldier behavior
such as motion, and firing weapons, in addition soldier's health and location on the war terrain. Creating a large number of
soldier objects is a necessity however it would mean a huge memory cost. Note that although the representation and behavior
of a soldier is the same their health and location can vary greatly.

##### Intent

The intent of this pattern is to use sharing to support a large number of objects that have part of their internal state in 
common where the other part of state can vary.

##### Applicability

The flyweight pattern applies to a program using a huge number of objects that have part of their internal state in common 
where the other part of state can vary. The pattern is used when the larger part of the object's state can be made external 
to that object.

##### Consequences

Flyweight pattern saves memory by sharing flyweight objects among clients. The amount of memory saved generally depends on 
the number of flyweight categories saved (for example a soldier category and a lieutenant category as discussed earlier).

##### Related Patterns

Factory and Singleton patterns - Flyweights are usually created using a factory and the singleton is applied to that factory
so that for each type or category of flyweights a single instance is returned.
