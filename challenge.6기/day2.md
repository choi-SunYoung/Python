```python
"""
As you can see, the code is broken.
Create the missing functions, use default arguments.
Sometimes you have to use 'return' and sometimes you dont.
Start by creating the functions
"""
days = ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]

def is_on_list(x, y):
  if y in x:
    return(True)
def get_x(x, y):
  return(x[y])
def add_x(x, y):
  x.append(y)
  return(x)
def remove_x(x, y):
  x.remove(y)
  return(x)

print("Is Wed on 'days' list?", is_on_list(days, "Wed"))  #Is Wed on 'days' list? True
print("The fourth item in 'days' is:", get_x(days, 3))    #The fourth item in 'days' is: Thu
add_x(days, "Sat")
print(days)		#['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun', 'Sat']
remove_x(days, "Mon")
print(days)		#['Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
```

`return()` 함수를 통해 함수를 호출할 수 있다.

리스트에 element를 순서에따라 호출하거나 더하거나(append) 제거(remove)할 수 있다.

```python
//solution

def is_on_list(a_list=[], word=""):
  return word in a_list

def get_x(a_list=[], index=0):
  return a_list[index]

def add_x(a_list=[], word=""):
  a_list.append(word)

def remove_x(a_list=[], word=""):
  a_list.remove(word)
```

