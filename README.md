from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
import time

# Set up headless Chrome
options = Options()
options.add_argument("--headless")
driver = webdriver.Chrome(options=options)

# Example search parameters
departure_port = "Miami"
travel_month = "2025-01"  # January 2025
suite_type = "Junior Suite"

# Navigate to Royal Caribbean search page
driver.get("https://www.royalcaribbean.com/cruises")

# Allow time for page to load
time.sleep(5)

# TODO: Interact with the site to select filters for port/month/suite
# This part requires locating the correct input fields and using driver.find_element...

# Extract suite prices from search results
cruise_cards = driver.find_elements(By.CLASS_NAME, "cruise-card")
for card in cruise_cards:
    try:
        cruise_name = card.find_element(By.CLASS_NAME, "cruise-name").text
        price = card.find_element(By.CLASS_NAME, "suite-price").text
        print(f"{cruise_name}: {price}")
    except:
        continue

driver.quit()
