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
