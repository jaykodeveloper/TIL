# @property
It makes `getter` and `setter`.

```python
class Person:
    def __init__(self):
        self.__age = 0

    @property
    def age(self):
        # getter
        return self.__age

    @age.setter
    def age(self, value):
        # setter
        self.__age = value

jay = Person()
jay.age = 20
print(jay.age)
# >> 20
```

Put `@property` decorator on the getter function and `@function.setter` on setter function. Name of two functions are same and we can use function as attribute.