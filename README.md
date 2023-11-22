# CodeVenture
A repository for various coding adventures.
import requests
from bs4 import BeautifulSoup

def scrape_byggeli():
    url = 'https://byggeli.dk'  # Replace with the actual URL
    response = requests.get(url)
    
    if response.status_code == 200:
        soup = BeautifulSoup(response.content, 'html.parser')
        articles = soup.find_all('article')  # Assuming articles are wrapped in <article> tags
        
        for article in articles:
            title = article.find('h2').text.strip()  # Assuming titles are in <h2> tags
            summary = article.find('p').text.strip()  # Assuming summaries are in <p> tags
            link = url + article.find('a')['href']  # Assuming links are in <a> tags
            
            # Print or process the retrieved data
            print(f"Title: {title}\nSummary: {summary}\nLink: {link}\n")
    else:
        print('Failed to retrieve data from Byggeli.dk')

scrape_byggeli()
