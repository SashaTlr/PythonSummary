### File IO
Opening file
```
f = open(filename, mode)
```
mode: "r", "w", "a" (append), "wb" (write in binary mode), "rb" (read in binary mode)

Closing file
```
f.close
```
Reading data from the file
`f.readline()` reads next line of file
`f.readlines()` read all the lines as a list of strings in the file

Writing data to file
`f.write("xyz")` writes to file

Looping through file lines (open in read):
```
for line in f:
    print(line)
```

### Working with JSON
`import json`

### Deserialize JSON (i.e. decode) from string or file
Second argument is "w", "r" (write or read) 
```
with open("data_file.json", "r") as read_file:
    data = json.load(read_file) 
```
if data is in a string:
```
data = json.loads(json_data)
```

To read data into a class:
```
class JsonObject(object):
    def __init__(self, data1, data2, *args, **kwargs):
        self.data1 = data1
        self.data2 = data2
```
And then:
```
import json
data = json.loads(json_data)
dataObject = JsonObject(**data)
```
or
```
def as_payload(dct):
    return Payload(dct['data1'], dct['data2'])

payload = json.loads(json_data, object_hook = as_payload)
```

### Serialize JSON (i.e. encode)
`json.dump(data)`

### String interpolation
name = 'Ash'
ages = {'Ash': 20}
```
print(f'{name} is {ages[name]} years old.') # using f-strings
print('%s is %s years old.' %(name, ages[name],)) # %-formatting (not recommended)
print('{} is {} years old'.format(name, ages[name])) # Str.format()
print('{name} is {age} years old.'.format(name = name, age = ages[name])) # Str.format()
```

### Lists
```
list.append(x) 
list.insert(index, obj)
list.remove(obj)
list.sort()
list.pop(i) #returns popped element
list.index(obj) #finds index
list.count(obj)
```
- Check if key exists in list
```
if todo["completed"]:
  try:
      # Increment the existing user's count.
      todos_by_user[todo["userId"]] += 1
  except KeyError:
      # This user has not been seen. Set their count to 1.
      todos_by_user[todo["userId"]] = 1
```

### Dictionaries
- Initialize with {}
- use dict.items() to iterate and get key, value pair
```
for key, value in d.items():
    print("{0} = {1}".format(key, value))
```
- Returns a KeyError if key doesn't exist
``` 
try:
  do something
except KeyError:
  create key
```
- can use get to check if key exists
``` 
age = ages.get(person)
if age:
  do something
else:
  create key
```
- better to use in if trying to check for existence
``` 
if age in ages:
  do something
else:
  create key
```

### Default Dictionaries
Can set a default key so you don't have to check for key existence
``` 
from collections import defaultdict #or call collections.defaultdict(lambda: 'Vanilla')
test = defaultdict(int) #lambda will set default int (which is 0)
test[key] += 1
```
Use lambda if not callable type

### Tuples
- Are immutable
- Once created, cannot add, deleted, replace, or reorder elements

To initialize:
```
t1 = ()
t2 = (1, 2,3) #(1, 2, 3)
t3 = tuple([1,2,3]) #(1, 2, 3)
t4 = tuple("abc") # ('a', 'b', 'c')
```
### List iterations
```
any("e" in word for word in wordList) #wordList.Any(word => word.contains("e"))
all("e" in word for word in wordList) #wordList.All(word => word.contains("e"))
max/min(len(word) for word in wordList)

#using itertools library
from itertools import islice
list(islice(wordList, 2)) #equiv to Take() in LINQ

from itertools import takewhile
list(takewhile(lambda c: len(c) < 5, wordList)

from itertools import dropwhile
list(dropwhile(lambda c: len(c) < 5, wordList)

next() #returns next val, can use to return firstordefault element
next(word for word in wordList if word.startwith("a"), optional = "none")

sum(1 for word in wordList if word.startswith("a")) #wordList.Count(word => word.StartsWith("a"))

list(map(lambda word: word.upper(), wordList)) #Select
list(filter(lambda word: "n" in word, wordList)) #Where

sorted(wordList, key=lambda word:len(word))
groupby(wordList, lambda word: word[0]) #groupby needs to be sorted by data first
```

### Polymorphism and Inheritance
Syntax to create a subclass:
```
class SubClass(SuperClass):
    #call parent constructor e.g.
    def __init__(self, data1, data2, data3):
        super().__init__(data1, data2)
        self.__data3 = data3
        
    #data fields go here
    #instance methods go here e.g.
    def getData(self):
        return self.getData1() + self.getData2() + self.__data3
```
Multiple Inheritance:
```
class Subclass(SuperClass 1, SuperClass2):
```
### Exception Handling
```
try:
    # try something that might throw exception
except <ExceptionType>:
    # Exception handler
else:
finally: #will run every time
```

### Random things to remember
- use set() to establish uniqueness
- can cast list(set()) to convert to list
- list.append() returns None (list is mutable, append changes list)
- create your own iterators using yield:
```
def distinct(sequence):
    seen = set()
    for s in sequence:
        if not s in seen:
            seen.add(s)
            yield s
```

http://mark-dot-net.blogspot.com/2014/03/python-equivalents-of-linq-methods.html
