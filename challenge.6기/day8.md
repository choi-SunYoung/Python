* challenge goals: Using this boilerplate, build a program that:
  - Goes to [http://www.alba.co.kr](http://www.alba.co.kr/) and scrapes the companies on the front page.
  - Then go to the page of each company and scrape each job.
  - Create a .csv file for each company and write the jobs on it.
  - [watch the video](https://i.imgur.com/nZjqUT8.mp4)
  - 새로운 1일 과제입니다! 알바천국을 스크래핑 하세욧!
  - csv 파일이 위의 화면처럼 출력되게끔 코딩하세요.
  - This is the expected output of the repl.it and the .csv
  - ![](C:\Users\chois\Desktop\67fa4daa-efc2-4033-abce-198f1c04b5e9.png)





```python
//solution

import os
import csv
import requests
from bs4 import BeautifulSoup

os.system("clear")


def write_company(company):
    file = open(f"{company['name']}.csv", mode="w")
    writer = csv.writer(file)
    writer.writerow(["place", "title", "time", "pay", "date"])
    for job in company["jobs"]:
      writer.writerow(list(job.values()))


alba_url = "http://www.alba.co.kr"

alba_request = requests.get(alba_url)
alba_soup = BeautifulSoup(alba_request.text, "html.parser")
main = alba_soup.find("div", {"id": "MainSuperBrand"})
brands = main.find_all("li", {"class": "impact"})
for brand in brands:
    link = brand.find("a", {"class": "goodsBox-info"})
    name = brand.find("span", {"class": "company"})
    if link and name:
        link = link["href"]
        name = name.text
        company = {'name': name, 'jobs': []}
        jobs_request = requests.get(link)
        jobs_soup = BeautifulSoup(jobs_request.text, "html.parser")
        tbody = jobs_soup.find("div", {"id": "NormalInfo"}).find("tbody")
        rows = tbody.find_all("tr", {"class": ""})
        for row in rows:
            local = row.find("td", {"class": "local"})
            if local:
                local = local.text.replace(u'\xa0', ' ')
            title = row.find("td", {"class": "title"})
            if title:
                title = title.find("a").find("span", {
                    "class": "company"
                }).text.strip()
                title = title.replace(u'\xa0', ' ')
            time = row.find("td", {"class": "data"})
            if time:
                time = time.text.replace(u'\xa0', ' ')
            pay = row.find("td", {"class": "pay"})
            if pay:
                pay = pay.text.replace(u'\xa0', ' ')
            date = row.find("td", {"class": "regDate"})
            if date:
                date = date.text.replace(u'\xa0', ' ')
            job = {
                "place": local,
                "title": title,
                "time": time,
                "pay": pay,
                "date": date
            }
            company['jobs'].append(job)
        write_company(company)
```

