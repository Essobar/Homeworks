### Mediator pattern

The mediator pattern is a design pattern that promotes loose coupling of objects by removing the need for classes to 
communicate with each other directly. Instead, mediator objects are used to encapsulate and centralize the interactions 
between classes.

Sometimes a program is made up of large classes. Problems arise when these classes need to communicate with each other. 
Allowing classes communicate directly, these classes require to know their internal implementations. This could lead the 
program becoming more and more complex. These classes are tightly coupled which is not good from a design point of view and 
in future it could cause problems.

Mediator design pattern solves this problem. In this pattern the communication between objects is encapsulated with a mediator
object. Instead of classes communicating directly, classes send messages to the mediator and the mediator sends these messages
to the other classes.

Let’s imagine you need to create an application which needs to control several aircrafts. Rather than having aircraft to 
aircraft communication, it is better to implement a centralized mechanism which receives messages from all aircrafts, 
processes them, and sends them to the other aircrafts.

Different aircraft type classes inherit the Aircraft abstract base class and acts as colleagues. The RegionalAirTrafficControl 
class is the mediator class and implements the IAirTrafficControl interface. The RegionalAirTrafficControl object holds the
reference to all aircrafts that need to communicate with each other.

Every time the aircraft changes its flight altitude, it sends a message to the mediator (RegionalAirTrafficControl). The 
mediator finds whether any of the aircrafts is in the same flight corridor of the message sender and if yes, it sends to the
aircraft a notification message and the sender is ordered to increase its altitude.

```
public abstract class Aircraft
{
    private readonly IAirTrafficControl _atc;
    private int _altitude;

    public string RegistrationNumber { get; set; }

    public int Altitude
    {
        get { return _altitude; }
        set
        {
            _altitude = value;
            _atc.SendWarningMessage(this);
        }
    }
 
    public Aircraft(string registrationNumber, IAirTrafficControl atc)
    {

        RegistrationNumber = registrationNumber;
        _atc = atc;
        _atc.RegistrerAircraft(this);
    }

    public void Climb(int heightToClimb)
    {
        Altitude += heightToClimb;
    }

    public void ReceiveWarning(Aircraft reportingAircraft)
    {
        Console.WriteLine("ATC: ({0}) - {1} is at your flight altitude!!!",
          this.RegistrationNumber,reportingAircraft.RegistrationNumber);
    }
}

public class Airbus380:Aircraft
{
    public Airbus380(string registrationNumber, IAirTrafficControl atc) : base(registrationNumber, atc)
    {
    }
}

public class Boeing747: Aircraft
{
    public Boeing747(string registrationNumber, IAirTrafficControl atc) : base(registrationNumber, atc)
    {
    }
}

public class LearJet45:Aircraft
{
    public LearJet45(string registrationNumber, IAirTrafficControl atc) : base(registrationNumber, atc)
    {
    }
}

public interface IAirTrafficControl
{
    void RegistrerAircraft(Aircraft aircraft);

    void SendWarningMessage(Aircraft aircraft);
}

public class RegionalAirTrafficControl : IAirTrafficControl
{
    readonly List<Aircraft> _registeredAircrafts = new List<Aircraft>();

    public void RegistrerAircraft(Aircraft aircraft)
    {
        if (!_registeredAircrafts.Contains(aircraft))
        {
            _registeredAircrafts.Add(aircraft);
        }
    }

    public void SendWarningMessage(Aircraft aircraft)
    {
        var list = from a in _registeredAircrafts
                   where a != aircraft &&
                         Math.Abs(a.Altitude - aircraft.Altitude) < 1000
                   select a;
        foreach (var a in list)
        {
            a.ReceiveWarning(aircraft);
            aircraft.Climb(1000);
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        var regionalATC = new RegionalAirTrafficControl();
        var aircraft1 = new Airbus380("AI568", regionalATC);
        var aircraft2 = new Boeing747("BA157", regionalATC);
        var aircraft3 = new Airbus380("LW111", regionalATC);

        aircraft1.Altitude += 100;

        aircraft3.Altitude = 1100;
    }
}
```
