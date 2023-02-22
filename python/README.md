# Pythonic code

## Getters

Do not write getters and setters. This is what the `property` built-in is for.

DON'T do this:

```python
class C:
    def __init__(self):
        self._x = None

    def getx(self):
        return self._x

    def setx(self, value):
        self._x = value

    def delx(self):
        del self._x


c = C()
c.setx(5)
print(c.getx())
```

DO this:

```python
class C:
    def __init__(self):
        self._x = None

    @property
    def x(self):
        return self._x

    @x.setter
    def x(self, value):
        self._x = value

    @x.deleter
    def x(self):
        del self._x

c = C()
c.x = 5
print(c.x)
```

## References

1. [Python is not Java](https://dirtsimple.org/2004/12/python-is-not-java.html)
2. [Python3 Built-in Functions](https://docs.python.org/3/library/functions.html#property)
3. [Python Property](https://realpython.com/python-property/)
