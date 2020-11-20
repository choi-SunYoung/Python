* challenge goals: 

  Using the boilerplate, make a program that **gets urls as an input** and checks if they are **online or not**.

  - The program should accept any number of URLs separated by comma, with or without 'http', with or without **spaces, uppercase or lowercase**. You need to handle all the cases.
  - You need to check if the URL is legit or not.
  - The user can restart the program after it's finished.

* boilerplate상단에 

  Welcome to IsItDown.py!

  Please write a URL or URLs you want to check.(seperated by comma) 고정

* input으로 넣은 url이 온라인에 있는지 없는지 확인하는 프로그램 만들기




```python
#solution

import os
import requests

def restart():
  answer = str(input("Do you want to start over? y/n ")).lower()
  if answer == "y" or answer =="n":
    if answer == "n":
        print("k. bye!")
        return
    elif answer == "y":
      main()
  else:
    print("That's not a valid answer")
    restart()


def main():
  os.system('clear')
  print("Welcome to IsItDown.py!\nPlease write a URL or URLs you want to check. (separated by comma)")
  urls = str(input()).lower().split(",")
  for url in urls:
    url = url.strip()
    if "." not in url:
      print(url, "is not a valid URL.")
    else:
      if "http" not in url:
        url = f"http://{url}"
      try:
        request = requests.get(url)
        if request.status_code == 200:
          print(url,"is up!")
        else:
          print(url, "is down!")
      except:
          print(url, "is down!")
  restart()


main()
```


