## TC01
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
print("Executing TC01: Open online shopping website...")
driver.get("https://www.saucedemo.com/")
time.sleep(2)
assert "Swag Labs" in driver.title
print("TC01 Result: Shopping website opened successfully.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b5186d23-7b51-44fe-a38b-221b49477dbb" />

## TC02
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
wait = WebDriverWait(driver, 10)
print("Executing TC02: Confirm product removal (accept)...")
driver.get("https://the-internet.herokuapp.com/javascript_alerts")
driver.find_element(By.XPATH, "//button[text()='Click for JS Confirm']").click()
alert = wait.until(EC.alert_is_present())
print("Alert displayed:", alert.text)
time.sleep(1)
alert.accept()
result = driver.find_element(By.ID, "result").text
assert "You clicked: Ok" in result
print("TC02 Result: Product deletion is confirmed successfully.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/27da1234-ebf9-417d-8004-aa771f7b95f2" />

## TC03
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
wait = WebDriverWait(driver, 10)
print("Executing TC03: Cancel product removal (dismiss)...")
driver.get("https://the-internet.herokuapp.com/javascript_alerts")
driver.find_element(By.XPATH, "//button[text()='Click for JS Confirm']").click()
alert = wait.until(EC.alert_is_present())
print("Alert displayed:", alert.text)
time.sleep(1)
alert.dismiss()
result = driver.find_element(By.ID, "result").text
assert "You clicked: Cancel" in result
print("TC03 Result: Product remains in the cart.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/17ac774c-e0ed-4102-af83-7308622d19bd" />

## TC04
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
wait = WebDriverWait(driver, 10)
print("Executing TC04: Submit coupon/details in prompt popup...")
driver.get("https://the-internet.herokuapp.com/javascript_alerts")
driver.find_element(By.XPATH, "//button[text()='Click for JS Prompt']").click()
prompt = wait.until(EC.alert_is_present())
coupon = "DISCOUNT2026"
time.sleep(1)
prompt.send_keys(coupon)
prompt.accept()
result = driver.find_element(By.ID, "result").text
assert coupon in result
print(f"TC04 Result: Entered information '{coupon}' is submitted successfully.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/40326df6-c86d-4945-aecb-b3fd6487eda4" />

## TC05
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
actions = ActionChains(driver)
wait = WebDriverWait(driver, 10)
print("Executing TC05: Mouse hover over category/product...")
driver.get("https://the-internet.herokuapp.com/hovers")
figure = driver.find_elements(By.CLASS_NAME, "figure")[0]
actions.move_to_element(figure).perform()
time.sleep(1)
caption = wait.until(EC.visibility_of_element_located((By.XPATH, "//div[@class='figure'][1]//h5")))
assert caption.is_displayed()
print(f"TC05 Result: Product categories/submenu are displayed: '{caption.text}'.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/652e21a4-35c0-4558-80a1-3561abe3c942" />

## TC06
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
actions = ActionChains(driver)
wait = WebDriverWait(driver, 10)
print("Executing TC06: Double-clicking product item...")
driver.get("https://api.jquery.com/dblclick/")
driver.switch_to.frame(driver.find_element(By.TAG_NAME, "iframe"))
box = wait.until(EC.presence_of_element_located((By.TAG_NAME, "div")))
actions.double_click(box).perform()
time.sleep(1)
driver.switch_to.default_content()
print("TC06 Result: Product details/action triggered via double click.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/710928ec-a069-4f64-acf3-1e5ad3998c02" />
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/0ababa35-a03b-4475-a7ea-41be69cbe7c3" />

## TC07
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
actions = ActionChains(driver)
wait = WebDriverWait(driver, 10)
print("Executing TC07: Drag and drop product into cart...")
driver.get("https://the-internet.herokuapp.com/drag_and_drop")
source_item = wait.until(EC.presence_of_element_located((By.ID, "column-a")))
target_cart = driver.find_element(By.ID, "column-b")
actions.drag_and_drop(source_item, target_cart).perform()
time.sleep(1)
print("TC07 Result: Product is moved to the cart.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/62416c93-cc15-4f69-82ee-bd24ad3dcf96" />

## TC08
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
wait = WebDriverWait(driver, 10)
print("Executing TC08: Searching and waiting for product to load...")
driver.get("https://the-internet.herokuapp.com/dynamic_loading/2")
driver.find_element(By.CSS_SELECTOR, "#start button").click()
result_element = wait.until(EC.visibility_of_element_located((By.ID, "finish")))
time.sleep(1)
print(f"TC08 Result: Product is displayed successfully: '{result_element.text}'.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/05f8e7d7-9df5-4eb5-87c8-545d8f5931d4" />

## TC09
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
wait = WebDriverWait(driver, 10)
print("Executing TC09: Wait until Place Order button is clickable...")
driver.get("https://www.saucedemo.com/")
wait.until(EC.visibility_of_element_located((By.ID, "user-name"))).send_keys("standard_user")
driver.find_element(By.ID, "password").send_keys("secret_sauce")
driver.find_element(By.ID, "login-button").click()
wait.until(EC.element_to_be_clickable((By.ID, "add-to-cart-sauce-labs-backpack"))).click()
driver.find_element(By.CLASS_NAME, "shopping_cart_link").click()
wait.until(EC.element_to_be_clickable((By.ID, "checkout"))).click()
wait.until(EC.visibility_of_element_located((By.ID, "first-name"))).send_keys("Alex")
driver.find_element(By.ID, "last-name").send_keys("Morgan")
driver.find_element(By.ID, "postal-code").send_keys("600001")
driver.find_element(By.ID, "continue").click()
finish_btn = wait.until(EC.element_to_be_clickable((By.ID, "finish")))
time.sleep(1)
finish_btn.click()
print("TC09 Result: Order is submitted successfully.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/efd7aec5-d90a-4554-826f-b427f98d4ed4" />

## TC010
### Code
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
wait = WebDriverWait(driver, 10)
print("Executing TC10: Waiting for order confirmation alert popup...")
driver.get("https://the-internet.herokuapp.com/javascript_alerts")
driver.find_element(By.XPATH, "//button[text()='Click for JS Alert']").click()
confirmation_alert = wait.until(EC.alert_is_present())
print("Confirmation alert received:", confirmation_alert.text)
time.sleep(1)
confirmation_alert.accept()
print("TC10 Result: Confirmation alert is handled successfully.")
input("Press Enter to close browser...")
driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/c0e3e825-5448-4e92-9479-5594bdff05a7" />
