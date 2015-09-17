### Adapter Pattern

The adapter pattern is adapting between classes and objects. Like any adapter in the real world it is used to be an interface,
a bridge between two objects. In real world we have adapters for power supplies, adapters for camera memory cards, and so on.
What about software development? It's the same. Can you imagine an situation when you have some class expecting some type of
object and you have an object offering the same features, but exposing a different interface? Of course, you want to use both
of them so you don't to implement again one of them, and you don't want to change existing classes, so why not create an
adapter...

##### Intent

Convert the interface of a class into another interface clients expect.
Adapter lets classes work together, that could not otherwise because of incompatible interfaces.

##### Applicability

The visitor pattern is used when:
* When you have a class(Target) that invokes methods defined in an interface and you have a another class(Adapter) that doesn't
implement the interface but implements the operations that should be invoked from the first class through the interface. You 
can change none of the existing code. The adapter will implement the interface and will be the bridge between the 2 classes.
* When you write a class (Target) for a generic use relying on some general interfaces and you have some implemented classes,
not implementing the interface, that needs to be invoked by the Target class.

Software Examples of Adapter Patterns: Wrappers used to adopt 3rd parties libraries and frameworks - most of the applications
using third party libraries use adapters as a middle layer between the application and the 3rd party library to decouple the
application from the library. If another library has to be used only an adapter for the new library is required without having
to change the application code.

Objects Adapters are the classical example of the adapter pattern. It uses composition, the Adaptee delegates the calls to
Adaptee (opposed to class adapters which extends the Adaptee). This behaviour gives us a few advantages over the class
adapters(however the class adapters can be implemented in languages allowing multiple inheritance). The main advantage is 
that the Adapter adapts not only the Adpatee but all its subclasses. All it's subclasses with one "small" restriction: all
the subclasses which don't add new methods, because the used mechanism is delegation. So for any new method the Adapter must
be changed or extended to expose the new methods as well. The main disadvantage is that it requires to write all the code for 
delegating all the necessary requests tot the Adaptee.

##### How Much the Adapter Should Do?

This question has a really simple response: it should do how much it has to in order to adapt. It's very simple, if the Target
and Adaptee are similar then the adapter has just to delegate the requests from the Target to the Adaptee. If Target and 
Adaptee are not similar, then the adapter might have to convert the data structures between those and to implement the
operations required by the Target but not implemented by the Adaptee.
