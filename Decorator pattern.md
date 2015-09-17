### Decorator Pattern

Extending an object's functionality can be done at compile time by using inheritance. However it might be necessary to extend
an object's functionality at runtime as an object is used. There decorator patterns can help us.

##### Intent

The intent of this pattern is to add additional responsibilities dynamically to an object.

##### Applicability

The decorator pattern applies when there is a need to dynamically add as well as remove responsibilities to a class, and when
subclassing would be impossible due to the large number of subclasses that could result.

##### Related Patterns

* Adapter Pattern - A decorator is different from an adapter in that a decorator changes object's responsibilities, while an
adapter changes an object interface.
* Composite Pattern - A decorator can be viewed as a degenerate composite with only one component. However, a decorator adds
additional responsibilities.

##### Consequences

Decoration is more convenient for adding functionalities to objects instead of entire classes at runtime. With decoration it 
is also possible to remove the added functionalities dynamically.

Decoration adds functionality to objects at runtime which would make debugging system functionality harder.
