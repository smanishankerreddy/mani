import requests
from bs4 import BeautifulSoup

url = "https://www.olx.in/items/q-car-cover"
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
}

response = requests.get(url, headers=headers)

if response.status_code == 200:
    soup = BeautifulSoup(response.content, 'html.parser')
    items = soup.find_all("li", class_="EIR5N")

    with open("car_cover_results.txt", "w", encoding="utf-8") as f:
        for item in items:
            title = item.find("span")
            link_tag = item.find("a", href=True)
            
            if title and link_tag:
                title_text = title.get_text(strip=True)
                link = "https://www.olx.in" + link_tag['href']
                f.write(f"{title_text}\n{link}\n\n")
    
    print("Search results saved in 'car_cover_results.txt'")
else:
    print("Failed to fetch data. Status code:", response.status_code)
