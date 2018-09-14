# About collections

```
In [1]: from collections import *

In [2]: person = namedtuple("Person", ("name","age","gender"))

In [3]: Bob = person("Bob", 23, "Male")

In [4]: Bob.name
Out[4]: 'Bob'

In [5]: Bob.age
Out[5]: 23

In [6]: person._fields
Out[6]: ('name', 'age', 'gender')

In [7]: items = deque((1,2,3), maxlen=5) 

In [8]: items[0]
Out[8]: 1

In [9]: items.append(4)

In [10]: items
Out[10]: deque([1, 2, 3, 4])

In [11]: items.appendleft(0)

In [12]: items
Out[12]: deque([0, 1, 2, 3, 4])

In [13]: items.extend([5, 6])

In [14]: items
Out[14]: deque([2, 3, 4, 5, 6])

In [15]: items.extendleft([0, 1])

In [16]: items
Out[16]: deque([1, 0, 2, 3, 4])

In [17]: items.pop()
Out[17]: 4

In [18]: items.popleft()
Out[18]: 1

In [19]: items
Out[19]: deque([0, 2, 3])

In [20]: items.remove(2)

In [21]: items
Out[21]: deque([0, 3])

In [22]: items.reverse()

In [23]: items
Out[23]: deque([3, 0])

In [24]: items.count(0)
Out[24]: 1

In [25]: items.count(3)
Out[25]: 1

In [26]: items
Out[26]: deque([3, 0])

In [27]: items.rotate(1)

In [28]: items
Out[28]: deque([0, 3])

In [29]: # rotate(n): Rotate the deque n times to the right.

In [30]: items.clear()

In [31]: items
Out[31]: deque([])

In [32]: items.maxlen
Out[32]: 5

In [33]: d1 = {'name':'bob', 'age': 33} 

In [34]: d2 = {'gender':'Woman', 'name':'Alisa'}

In [35]: m = ChainMap(d1,d2)

In [36]: m
Out[36]: ChainMap({'age': 33, 'name': 'bob'}, {'gender': 'Woman', 'name': 'Alisa'})

In [37]: m.keys()
Out[37]: KeysView(ChainMap({'age': 33, 'name': 'bob'}, {'gender': 'Woman', 'name': 'Alisa'}))

In [38]: tuple(m.keys())
Out[38]: ('age', 'name', 'gender')

In [39]: tuple(m.items())
Out[39]: (('age', 33), ('name', 'bob'), ('gender', 'Woman'))

In [40]: tuple(m.values())
Out[40]: (33, 'bob', 'Woman')

In [41]: m['name']
Out[41]: 'bob'

In [42]: m.maps
Out[42]: [{'age': 33, 'name': 'bob'}, {'gender': 'Woman', 'name': 'Alisa'}]

In [43]: m.new_child({'age':22})
Out[43]: ChainMap({'age': 22}, {'age': 33, 'name': 'bob'}, {'gender': 'Woman', 'name': 'Alisa'})

In [44]: n = m.new_child({'age':22})

In [45]: m.parents
Out[45]: ChainMap({'gender': 'Woman', 'name': 'Alisa'})

In [46]: n.parents
Out[46]: ChainMap({'age': 33, 'name': 'bob'}, {'gender': 'Woman', 'name': 'Alisa'})

In [47]: c = Counter()

In [48]: c['a'] = 1

In [49]: c
Out[49]: Counter({'a': 1})

In [50]: c = Counter('xxxxxxyyyyyyyyzzzzzz')

In [51]: c['x']
Out[51]: 6

In [52]: c
Out[52]: Counter({'x': 6, 'y': 8, 'z': 6})

In [53]: c = Counter(x=2, z=5, y=3)

In [54]: c['y']
Out[54]: 3

In [55]: c
Out[55]: Counter({'x': 2, 'y': 3, 'z': 5})

In [56]: tuple(c.elements())
Out[56]: ('x', 'x', 'y', 'y', 'y', 'z', 'z', 'z', 'z', 'z')

In [57]: c.most_common(2)
Out[57]: [('z', 5), ('y', 3)]

In [58]: # most_common(n) : Returns a sequence of the n most frequently encounte
    ...: red values and total counts of this values.

In [59]: c
Out[59]: Counter({'x': 2, 'y': 3, 'z': 5})

In [60]: c.update('abcccccaa')

In [61]: c
Out[61]: Counter({'a': 3, 'b': 1, 'c': 5, 'x': 2, 'y': 3, 'z': 5})

In [62]: c.subtract("kllmmkml")

In [63]: c
Out[63]: 
Counter({'a': 3,
         'b': 1,
         'c': 5,
         'k': -2,
         'l': -3,
         'm': -3,
         'x': 2,
         'y': 3,
         'z': 5})

In [64]: # subtract(x) : Substracts values from given iterable / mapping.

In [65]: b = Counter(a=4, b=3)

In [66]: c + b
Out[66]: Counter({'a': 7, 'b': 4, 'c': 5, 'x': 2, 'y': 3, 'z': 5})

In [67]: c & b
Out[67]: Counter({'a': 3, 'b': 1})

In [68]: # __and__(x) (&) : Intersection of 2 Counter objects.

In [69]: c | b
Out[69]: Counter({'a': 4, 'b': 3, 'c': 5, 'x': 2, 'y': 3, 'z': 5})

In [70]: c
Out[70]: 
Counter({'a': 3,
         'b': 1,
         'c': 5,
         'k': -2,
         'l': -3,
         'm': -3,
         'x': 2,
         'y': 3,
         'z': 5})

In [71]: b
Out[71]: Counter({'a': 4, 'b': 3})

In [72]: # __or__(x) (|) : Union of 2 Counter objects.

In [73]: o = OrderedDict(name="bob", position="some", age=23)

In [74]: o['name']
Out[74]: 'bob'

In [75]: o
Out[75]: OrderedDict([('age', 23), ('name', 'bob'), ('position', 'some')])

In [76]: o.popitem()
Out[76]: ('position', 'some')

In [77]: o
Out[77]: OrderedDict([('age', 23), ('name', 'bob')])

In [78]: o = o.fromkeys("abc")

In [79]: o
Out[79]: OrderedDict([('a', None), ('b', None), ('c', None)])

In [80]: o.move_to_end('a')

In [81]: o
Out[81]: OrderedDict([('b', None), ('c', None), ('a', None)])

In [82]: def factory() -> str:
    ...:     return 'unknown'
    ...: 
    ...: 

In [83]: d = defaultdict(factory, red="ff0000", blue="0000ff")

In [84]: d
Out[84]: 
defaultdict(<function __main__.factory() -> str>,
            {'blue': '0000ff', 'red': 'ff0000'})

In [85]: d['red']
Out[85]: 'ff0000'

In [86]: d['green']
Out[86]: 'unknown'

In [87]: """defaultdict is a dict subclass with default values for non-exist ent
    ...: ries. It takes a factory for initalizing. Factory helps it with generat
    ...: ing values for non-exist entries. Also you can regular dict API with it
    ...: ."""
Out[87]: 'defaultdict is a dict subclass with default values for non-exist entries. It takes a factory for initalizing. Factory helps it with generating values for non-exist entries. Also you can regular dict API with it.'
```
###### [About collections.UserDict , collections.UserList , and collections.UserString](https://medium.com/bynder-tech/using-collections-in-python-36129737b5a1)
```
In [16]: class Event(dict):
    ...:     def __getitem__(self, key):
    ...:         value = super().__getitem__(key)
    ...:         return f"[{self.__class__.__name__}]: {value}"
    ...:     

In [17]: event = Event(user="user", event_type="login", date="2017-07-11")

In [18]: for key, value in event.items():
    ...:     print(f"{key} = {value}")
    ...: 
    ...:     
user = user
event_type = login
date = 2017-07-11

In [19]: class Event(collections.UserDict):
    ...:     def __getitem__(self, key):
    ...:         value = super().__getitem__(key)
    ...:         return f"[{self.__class__.__name__}]: {value}"
    ...:     

In [20]: event = Event(user="user", event_type="login", date="2017-07-11")

In [21]: for key, value in event.items():
    ...:     print(f"{key} = {value}")
    ...: 
    ...:     
user = [Event]: user
event_type = [Event]: login
date = [Event]: 2017-07-11
```
