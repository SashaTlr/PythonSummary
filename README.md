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

### Random things to remember
- use set() to establish uniqueness
- can cast list(set()) to convert to list
- list.append() returns None (list is mutable, append changes list)
