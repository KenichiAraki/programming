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

### Tricks

##### tuple of tuples  
```  
choices = ((ent, ent),)
choices = ((ent, ent),) + choices
```  

##### one line if  
```  
switch_ip = switch_ips[0] if len(switch_ips) >= 1 else ""
```  
