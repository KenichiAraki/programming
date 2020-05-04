Python 3 vs. Python 2
=====

### zip
python 2: returns 'list', python 3: returns 'iterator'

### python 3  
- dict = ordered collections (3.6)
    dict.has_key() removed use 'key' in disct
- async: asincio/await, e.g. asincio.sleep(delay), asincio.gather()


Language
=====

### loops

``` 
*** multiple lists with zip ***  
letters = ['a', 'b', 'c']
numbers = [0, 1, 2]
for l, n in zip(letters, numbers)
```
``` 
*** list comprehenssion with a condition ***
values = [expression for value in collection if condition]
values = []
for value in collection:
    if condition:
        values.append(expression)
```

### string

##### json string
```
*** double quotes ***
>>> temp = '"firstname":"{0}", ' \
...        '"lastname":"{1}"'
>>> print temp.format('Duke', 'Togo')
"firstname":"Duke", "lastname":"Togo"

*** '{' with .format ***
>>> temp = '{"firstname":"{0}", ' \
...        '"lastname":"{1}"}'
>>> print temp.format('Duke', 'Togo')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: '"firstname"'

>>> temp = '{{"firstname":"{0}", ' \
...        '"lastname":"{1}"}}'
>>> print temp.format('Duke', 'Togo')
{"firstname":"Duke", "lastname":"Togo"}

*** json module ***
>>> import json
>>> temp = dict(firstname='Duke', lastname='Togo')
>>> print json.dumps(temp)
{"lastname": "Togo", "firstname": "Duke"}

*** '-' in attribute name ***
>>> temp = dict(firstname='Duke', lastname='Togo', color-eye='black')
  File "<stdin>", line 1
SyntaxError: keyword can't be an expression

>>> t = Template('{"firstname":$fname, "lastname":$lname, "color-eye":$coleye}')
>>> print json.dumps(t.substitute(fname='Duke', lname='Togo', coleye='black')
... )
"{\"firstname\":Duke, \"lastname\":Togo, \"color-eye\":black}"

>>> temp = '{"firstname":"%s", "lastname":"%s", "color-eye"="%s"}'
>>> print temp % ('Duke', 'Togo', 'black')
{"firstname":"Duke", "lastname":"Togo", "color-eye"="black"}

*** jinja and json data ***
template.j2
    url = '"http://{{ dhcp.http_server }}';

DEFAULT_VARS = '''
{
    "dhcp": {
        "http_server": "135.121.33.251"
    }
}
vars = eval(DEFAULT_VARS)

template_loader = FileSystemLoader("templates")
jinja_env = Environment(loader=template_loader)
template = jinja_env.get_template(template_file)
output = template.render(dhcp=vars['dhcp'])

```

### Arguments
```  
def myfunc(x, y, z):
    print(x, y, z)

tuple_vec = (1, 0, 1)
dict_vec = {'x': 1, 'y': 0, 'z': 1}

>>> myfunc(*tuple_vec)
1, 0, 1

>>> myfunc(**dict_vec)
1, 0, 1
```

### Files

##### with open
```   
with open(file) as f:
  data = f.read()
```  

##### read yaml  
```  
data = yaml.load(f)
```

### Generator
generators return a lazy iterator:
- can loop over a list
  + 'yield' to return the control to a caller
  + 'next' to go back to the generator
- contents are not stored in memory  

``` Reading a large file   
lines = (line for line in open(csv_file))
list_line = (s.rstrip.split(",") for s in lines)
cols = next(list_line)
dicst = (dict(zip(cols, data)) for data in list_line)
```  

``` list vs. generator  
nums_squard_lc = [num**2 for num in range(5)] -> list, entire list is created and stored in memory
nums_squard_lc = (num**2 for num in range(5)) -> generator, next() generates and returns a value
```  

### Tricks

##### dictionary
```  
fields = ['name', 'last_name', 'age', 'job']
values = ['John', 'Smith', '45', 'Python Developer']
a_dict = dict(zip(fileds, values))

new_job = ['Python Consultant']
filed = ['job']
a_dict.update(zip(field, new_job))
```  

##### tuple of tuples  
```  
choices = ((ent, ent),)
choices = ((ent, ent),) + choices
```  

##### one line if  
```  
switch_ip = switch_ips[0] if len(switch_ips) >= 1 else ""
```  
