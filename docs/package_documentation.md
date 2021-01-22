## Settings
You can set settings by using a dict on the init of the class. In the settings
you can set a lot of things like port or communication method.

For the settings you have the following options:

|Option|Description|Default|
|------|-----------|-------|
|host|This option sets the host where the data send to or received from.|127.0.0.1 (localhost)|
|port|The port where the connection happens.|19321|
|connect_type|The connection type. Currently there is TCP/UDP.|TCP|

See the example:
````python
mc_signal = MCSignal({
    "host": "your_ip",
    "port": "another_port",
    "connect_type": "TCP",   
})
````

## Events
You can define events, there are called when another file or your file call this event
by using `trigger()`. The event has two arguments:

|Argument|Desription|
|--------|----------|
|name|This argument contains the name of the event. The name is used in the `trigger()` method to identify the event.
|call_function|This argument contains a pointer to a function. The function you pointed will call when the event is called.

To define an argument use `MCEvent()` the event can be added to the signal by using
`addEvent()`. See the example:

````python
mc_signal = MCSignal()

my_event = MCEvent(name="hello_world", call_function=my_function)
mc_signal.addEvent(my_event)
````

To call an event you have to use `trigger()`. It has an argument `name` which is the name
of the event. You also have to specify the filename by using `__file__`. It is for intern processes.
See the example:
````python
mc_signal = MCSignal()

mc_signal.trigger("hello_world", __file__)
````
