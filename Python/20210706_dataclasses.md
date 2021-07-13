# Dataclasses

In python, we have many different types of data structure, `list`, `tuple`, `dictionary`....

If we keep the data in the class, it is type-safe and there is less error.

Before you use `dataclasses` module, you might store data in the class this way,
```python
from datetime import date

class User:
    def __init__(self, id, name, bod, admin):
        self.id = id
        self.name = name
        self.bod = bod
        self.admin = admin

# In order to read this, we need to implement __repr__
    def __repr__(self):
        return(
            self.__class__.__qualname__ + f"(id={self.id!r}, name={self.name!r}, birthday={self.bod!r}, admin={self.admin!r})
        )
```
then, instantiated it
```
>>> user = User(id=777, name='Jay', bod=(2000, 2, 20), admin=True)
>>> user
User(id=777, name='Jay', bod=(2000, 2, 20), admin=True)
```

## But, if you use `dataclasses` ?

```python
from dataclasses import dataclasses
from datetime import date

@dataclass
class User:
    id: int
    name: str
    bod: date
    admin: bool = False
```

`dataclasses` automatically generates `__init__()`, `__repr__()`, `__eq__()` which we had to make manually.

You can also change even after it is declared
```shell
>>> user = User(id=777, name='Jay', bod=(2000, 2, 20), admin=True)
>>> user
User(id=777, name='Jay', bod=(2000, 2, 20), admin=True)
>>> user.admin=False
>>> user
User(id=777, name='Jay', bod=(2000, 2, 20), admin=False)
```
You can also make it immutable,
```python
from dataclasses import dataclasses
from datetime import date

@dataclass(frozen=True)
class User:
    id: int
    name: str
    bod: date
    admin: bool = False
```
If you want to compare big or small, you can pass `order=True` in its parameter.

## What to be cautious when you use `dataclasses`
The most common mistake is when you allocate value into mutable type, like `list`.


```python
from dataclasses import dataclasses
from datetime import date

@dataclass(unsafe_hash=True)
class User:
    id: int
    name: str
    bod: date
    admin: bool = False
    friends: List[int] = []
```
This will throw an error.
In this case you need to add `default_factory` option into field so that it can create new list whenever it creates instance.


```python
from dataclasses import dataclasses
from datetime import date

@dataclass(unsafe_hash=True)
class User:
    id: int
    name: str
    bod: date
    admin: bool = False
    friends: List[int] = field(default_factory=list)
```
