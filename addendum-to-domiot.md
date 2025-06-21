# Addendum to Document Object Model for IoT - Building IoT Systems with HTML and JavaScript

## Attributes 

In some cases, such as the `locked` attribute (e.g., of a `<door>` element), we don't need complementary attributes like `unlocked` or attribute Boolean values (true/false). We can instead imitate the behavior of an HTML/DOM checkbox and rely solely on the presence or absence of the `locked` attribute. See the following example:

```
<iot-door id="hotelDoor" locked message="Welcome to Hotel Paradise!" binding="lockBinding lcdBinding">
```
In the example above, the presence of the `locked` attribute indicates that the door is locked.

```
<iot-door id="hotelDoor" message="Welcome to Hotel Paradise!" binding="lockBinding lcdBinding">
```
Here, the absence of the `locked` attribute indicates that the door is unlocked.

We can use standard DOM API methods to set or remove such attributes:
```
door.setAttribute('locked',''); // locks the door.

door.removeAttribute('locked'); // unlocks the door.
```

## Bindings

Bindings can be cross-platform or platform-specific (e.g. Linux, Windows).

Bindings have two main components:
- The type of communication they establish with the driver, such as whether the data exchange is input (I), output (O), or bidirectional (IO). Whether it's in binary or textual format; and whether it occurs through commands, data streams, or memory mapping.
- The DOM actor involved: attributes or CSS properties they monitor or modify, and the event(s) they can dispatch.

To ensure clarity, it is advisable to include a reference to both the communication type and the DOM actor involved in the binding name.

Examples:
```
<iot-iobits-lock-binding id="lockBinding" location="/dev/iohubx24-sim0">
```
In the example above, the binding name includes the type of communication with the driver (`iobits` stream of input bits) and the action it performs (`lock/unlock`).

```
<iot-otext-message-binding id="lcdBinding" location="/dev/lcd-sim0">
```
Here, the binding name includes the type of communication with the driver (`otext` output textual data), which indicates it communicates with a driver that accepts text such as an LCD display driver, and the name of the attribute it modifies (`message`).

## Semantic Structure

In interactive IoT systems, a domain-specific semantic HTML document and DOM tree can serve as a textual representation of an object or a 3D space. This structure can enhance comprehension by large language models (LLMs), which already perform well with structured text.


