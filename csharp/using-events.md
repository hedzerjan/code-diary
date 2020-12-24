# Using events in c#
Sometimes events may solve dependancy problems in your code. They are not a panacee and introduce new problemens though. Some pro's and con's:
Pro:
* Less explicit dependancies between classes.
* Simplification of some parts of your code.
Cons:
* Code flow becomes harder tot read and debug.

Official documentation: (https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/events/)

## The basic way
Allthough MicroSoft advises you to use the EventHandler class, this isn't strictly necessary. I'll be using the Action generic class here. First one class (the publisher of the event, or the source) needs to define the event at the class level:
```csharp
    class Publisher
    {
        public static event Action<string> OnString
```

And then any other class can subscribe:
```csharp
    class Subscriber
    {
        public Subscriber()
        {
            Publisher.OnString += GetTheName;   
        }
```

The function that actually processes the message has to adhere to the event definition, in this case it has to have a parameter of type string:
```csharp
        private void GetTheName(string obj)
        {
            Console.WriteLine(obj);
        }
```

## The MicroSoft way
This requires you to do a couple of things; your event properties need to inherit EventArgs, your event needs to adhere to a naming convention. The advantadge is that you get the sender when you receive an event.

First for the custom properties (still using the example of a string, but it could be anything):
```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }
```

Then the publisher needs to define the event:
```csharp
    class MSPublisher
    {
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
```

And this is where the naming convention is used, the delegate that handles the event must be named OnXXX where XXX 9s the event name, in this case `RaiseCustomEvent`. This results in de delegatee being called `OnRaiseCustomEvent` in this case:
```csharp
        protected virtual void OnRaiseCustomEvent(CustomEventArgs e)
        {
            EventHandler<CustomEventArgs> raiseEvent = RaiseCustomEvent;

            if (raiseEvent != null)
            {
                e.Message += $" at {DateTime.Now}";
                raiseEvent(this, e);
            }
        }
```

And the publisher can broadcast like this:
```csharp
        public void DoSomething()
        {
            OnRaiseCustomEvent(new CustomEventArgs("Event triggered"));
        }
```