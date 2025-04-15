# web_scrapping
This is a minimal example of how to use Selenium to perform web scraping in Python.

It can be use in order to extract information from online datasets in an easy and automatizable process

# Selenium Web Scraping Demo

This is a minimal example of how to use Selenium to perform web scraping in Python.

## Requirements

- Python 3.7+
- Google Chrome + ChromeDriver
- Selenium

## Installation

```bash
pip install -r requirements.txt

---

### 📄 `scraper.py` (código simple de ejemplo)

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# Configuración del driver (Chrome)
driver = webdriver.Chrome()

try:
    # Ir a una página de ejemplo (DuckDuckGo)
    driver.get("https://duckduckgo.com/")
    
    # Buscar un input de texto
    search_box = driver.find_element(By.NAME, "q")
    search_box.send_keys("Quantum chemistry")
    search_box.send_keys(Keys.RETURN)

    time.sleep(2)  # Esperar a que cargue la página

    # Extraer resultados
    results = driver.find_elements(By.CLASS_NAME, "result__title")

    for i, result in enumerate(results[:5]):
        print(f"{i+1}. {result.text}")

finally:
    driver.quit()
