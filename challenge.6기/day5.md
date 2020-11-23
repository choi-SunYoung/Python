* challenge goals:

  Using the boilerplate, make a program that gets a list of countries from a website with their currency codes, then let the user choose a country and display the currency code of that country.

  This is part one of a bigger "country scrapping" project we will complete in the following days.

* 조건:

  1. The website you should get the countries and currencies from is: https://www.iban.com/currency-codes

  2. Save the name of the country and the "Alpha-3 code" in an array.

  3. Some countries don't have currency (No universal currency), don't add them to the list.

  4. Check the user input, only numbers from inside the country list are allowed.

  5. When a country is selected, show the name and currency code.

  - 힌트1: Use try/except when converting strings to numbers. `( int(input()) )`
  - 힌트2: [Index in 'for' loops?](https://stackoverflow.com/questions/522563/accessing-the-index-in-for-loops) 
  - This is how the program should work: [watch the video](https://i.imgur.com/Nh7nkjF.mp4)



```python
//solution

import os
import requests
from bs4 import BeautifulSoup

os.system("clear")


url = "https://www.iban.com/currency-codes"


countries = []

request = requests.get(url)
soup = BeautifulSoup(request.text, "html.parser")

table = soup.find("table")
rows = table.find_all("tr")[1:]

for row in rows:
  items = row.find_all("td")
  name = items[0].text
  code =items[2].text
  if name and code:
    if name != "No universal currency":
      country = {
        'name':name.capitalize(),
        'code': code
      }
      countries.append(country)


def ask():
  try:
    choice = int(input("#: "))
    if choice > len(countries):
      print("Choose a number from the list.")
      ask()
    else:
      country = countries[choice]
      print(f"You chose {country['name']}\nThe currency code is {country['code']}")
  except ValueError:
    print("That wasn't a number.")
    ask()


print("Hello! Please choose select a country by number:")
for index, country in enumerate(countries):
  print(f"#{index} {country['name']}")

ask()
```

