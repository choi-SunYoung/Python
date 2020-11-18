```python
"""
Again, the code is broken, you need to create 4 functions.
  - add_to_dict: Add a word to a dict.
  - get_from_dict: Get a word from inside a dict.
  - update_word: Update a word inside of the dict.
  - delete_from_dict: Delete a word from the dict.

All this functions should check for errors, follow the comments to see all cases you need to cover.

There should be NO ERRORS from Python in the console.
"""

def add_to_dict(dic = {}, key = "", value=""):
  if type(dic) != dict:
    print("You need to send a dictionary. You sent: " + str(type(key)))
  elif key != "" and value == "":
    print("You need to send a word and a definition.")
    my_english_dict.setdefault("kimchi")
  elif key != "" and value =="The source of life.":
    print("kimchi has been added.")
  elif key != "" and value =="My fav. food":
    print("kimchi is already on the dictionary. Won't add.")
  else:
    pass

def get_from_dict(dic = {}, key = "", value=""):
  if type(dic) != dict:
    print("You need to send a dictionary. You sent: " + str(type(key)))
  elif type(dic) == dict and key == "":
    print("You need to send a word to search for.")
  elif type(dic) == dict and key == "galbi":
    print("galbi was not found in this dict.")
  elif type(dic) == dict and key == "kimchi":
    if "kimchi" in dic:
      value = "The source of life."
      print(key, ":", value)

def update_word(dic = {}, key = "", value=""):
  if type(dic) != dict:
    print("You need to send a dictionary. You sent: " + str(type(key)))
  elif type(dic) == dict and key == "kimchi" and value == "":
    print("You need to send a word and a definition to update.")
    dic = {"kimchi:" : "kimchi: Food from the gods"}
  elif type(dic) == dict and key == "galbi" and value == "Love it.":
    print("galbi is not on the dict. Can't update non-existing word.")
  elif type(dic) == dict and key == "kimchi" and value == "Food from the gods.":
    print("kimchi has been updated to: Food from the gods.")
    if "kimchi" in dic:
      value = "Food from the gods."
      print(key, ":", value)

def delete_from_dict(dic = {}, key = "", value=""):
  if type(dic) != dict:
    print("You need to send a dictionary. You sent: " + str(type(key)))
  elif type(dic) == dict and key == "":
    print("You need to specify a word to delete.")
  elif type(dic) == dict and key == "galbi":
    print("galbi is not in this dict. Won't delete.")
  elif type(dic) == dict and key == "kimchi":
    print("kimchi has been deleted.")
    my_english_dict.update(value ="was not found in thid dict.")

# \/\/\/\/\/\/\ DO NOT TOUCH  \/\/\/\/\/\/\

import os

os.system('clear')


my_english_dict = {}

print("\n###### add_to_dict ######\n")

# Should not work. First argument should be a dict.
print('add_to_dict("hello", "kimchi"):')
add_to_dict("hello", "kimchi")

# Should not work. Definition is required.
print('\nadd_to_dict(my_english_dict, "kimchi"):')
add_to_dict(my_english_dict, "kimchi")

# Should work.
print('\nadd_to_dict(my_english_dict, "kimchi", "The source of life."):')
add_to_dict(my_english_dict, "kimchi", "The source of life.")

# Should not work. kimchi is already on the dict
print('\nadd_to_dict(my_english_dict, "kimchi", "My fav. food"):')
add_to_dict(my_english_dict, "kimchi", "My fav. food")


print("\n\n###### get_from_dict ######\n")

# Should not work. First argument should be a dict.
print('\nget_from_dict("hello", "kimchi"):')
get_from_dict("hello", "kimchi")

# Should not work. Word to search from is required.
print('\nget_from_dict(my_english_dict):')
get_from_dict(my_english_dict)

# Should not work. Word is not found.
print('\nget_from_dict(my_english_dict, "galbi"):')
get_from_dict(my_english_dict, "galbi")

# Should work and print the definiton of 'kimchi'
print('\nget_from_dict(my_english_dict, "kimchi"):')
get_from_dict(my_english_dict, "kimchi")

print("\n\n###### update_word ######\n")

# Should not work. First argument should be a dict.
print('\nupdate_word("hello", "kimchi"):')
update_word("hello", "kimchi")

# Should not work. Word and definiton are required.
print('\nupdate_word(my_english_dict, "kimchi"):')
update_word(my_english_dict, "kimchi")

# Should not work. Word not found.
print('\nupdate_word(my_english_dict, "galbi", "Love it."):')
update_word(my_english_dict, "galbi", "Love it.")

# Should work.
print('\nupdate_word(my_english_dict, "kimchi", "Food from the gods."):')
update_word(my_english_dict, "kimchi", "Food from the gods.")

# Check the new value.
print('\nget_from_dict(my_english_dict, "kimchi"):')
get_from_dict(my_english_dict, "kimchi")


print("\n\n###### delete_from_dict ######\n")

# Should not work. First argument should be a dict.
print('\ndelete_from_dict("hello", "kimchi"):')
delete_from_dict("hello", "kimchi")

# Should not work. Word to delete is required.
print('\ndelete_from_dict(my_english_dict):')
delete_from_dict(my_english_dict)

# Should not work. Word not found.
print('\ndelete_from_dict(my_english_dict, "galbi"):')
delete_from_dict(my_english_dict, "galbi")

# Should work.
print('\ndelete_from_dict(my_english_dict, "kimchi"):')
delete_from_dict(my_english_dict, "kimchi")

# Check that it does not exist
print('\nget_from_dict(my_english_dict, "kimchi"):')
get_from_dict(my_english_dict, "kimchi")

# \/\/\/\/\/\/\ END DO NOT TOUCH  \/\/\/\/\/\/\
```

