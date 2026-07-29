# Not Gate
## Built With Transistor

- The lesson here is not really about transistors but Logisim-Evolution:

**It's not really physics, it's more logic!**

- The reason why we have to use a pull up resistor is because, from a
logical perspective, it means a *weak 1*, which is defeated by the
*strong 0*: ground. If we would have used some sort of input pin
with a 1 signal, then the main wire would have to support a *strong 1*
and a *strong 0*, but it can't.

- It even makes more sense for why LEDs are on even if there is no closed
circuit, we care about the logic perspective.

*Some help from Claude Opus 4.8:*

```
Strong = Power, Ground, driven pins. Weak = Pull Resistor.
Red only happens with two strong drivers disagreeing.
A weak driver never causes red — it just loses.
```

