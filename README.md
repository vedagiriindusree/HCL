## Amazon 
### Program
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
chrome_options.add_argument("--disable-blink-features=AutomationControlled")
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
wait = WebDriverWait(driver, 20)
product_asin = "B071Z8M4KX"  # Standard Amazon ASIN
product_url = f"https://www.amazon.in/dp/{product_asin}"
print("Step 1: Opening Product Page in Tab 1...")
driver.get(product_url)
tab_product = driver.current_window_handle
time.sleep(2)
print("Step 2: Opening a new tab to add item to Cart...")
driver.switch_to.new_window('tab')
tab_cart = driver.current_window_handle
add_to_cart_url = f"https://www.amazon.in/gp/aws/cart/add.html?ASIN.1={product_asin}&Quantity.1=1"
driver.get(add_to_cart_url)
time.sleep(2)
print("Step 3: Loading full Cart page...")
driver.get("https://www.amazon.in/gp/cart/view.html")
time.sleep(2)
print("Step 4: Opening a new tab for Wishlist...")
driver.switch_to.new_window('tab')
tab_wishlist = driver.current_window_handle
driver.get("https://www.amazon.in/hz/wishlist/intro")
time.sleep(2)
print("\n=======================================================")
print("ALL 3 PAGES LOADED:")
print(" - Tab 1: Product Page (boAt Earphones)")
print(" - Tab 2: Cart Page (Item Added)")
print(" - Tab 3: Wishlist Page")
print("=======================================================")
input("\nPress ENTER here in the terminal when you want to close Chrome...")
driver.quit()
```
### Output
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8e60d1ba-9494-4791-ae72-b48a074f0be6" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/285abdbe-872a-44f9-b616-5e05703c0a3a" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/15c2b84a-f222-4a51-819c-2b1a9ad76889" />

