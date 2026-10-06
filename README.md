## Task 1-Web Form
### Program
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select
driver = webdriver.Chrome()
driver.get("https://www.selenium.dev/selenium/web/web-form.html")
text_box = driver.find_element(By.NAME, "my-text")
text_box.send_keys("Python Selenium")
driver.find_element(By.NAME, "my-text").send_keys("John")
driver.find_element(By.NAME, "my-password").send_keys("Password123")
driver.find_element(By.NAME, "my-textarea").send_keys("Learning Selenium")
radio_buttons = driver.find_elements(
    By.CSS_SELECTOR, "input[type='radio']"
)
if not radio_buttons[0].is_selected():
    radio_buttons[0].click()
checkboxes = driver.find_elements(
    By.CSS_SELECTOR, "input[type='checkbox']"
)
for checkbox in checkboxes:
    if not checkbox.is_selected():
        checkbox.click()
country = Select(driver.find_element(By.NAME, "my-select"))
country.select_by_index(1)
for option in country.options:
    print(option.text)
input("Press ENTER in the terminal when you want to close the browser...")
driver.quit()
```
### Output
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4f13e75a-044a-4f38-94ad-09772810a218" />

## Task 2-Demo Site
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
driver = webdriver.Chrome(options=chrome_options)
driver.maximize_window()
print("1. Loading website...")
driver.get("https://vinothqaacademy.com/demo-site/")
wait = WebDriverWait(driver, 25)
wait.until(EC.presence_of_element_located((By.XPATH, "//input[@type='text']")))
time.sleep(2)
print("2. Filling First Name...")
driver.execute_script("""
    var el = document.querySelector("input[name*='vfb-5'], input[id*='vfb-5']") || document.querySelectorAll("input[type='text']")[0];
    if(el) { el.value = 'Vedagiri'; el.dispatchEvent(new Event('input', { bubbles: true })); }
""")
print("3. Filling Last Name...")
driver.execute_script("""
    var el = document.querySelector("input[name*='vfb-7'], input[id*='vfb-7']") || document.querySelectorAll("input[type='text']")[1];
    if(el) { el.value = 'Indu Sree'; el.dispatchEvent(new Event('input', { bubbles: true })); }
""")
print("4. Selecting Female...")
driver.execute_script("""
    var radio = document.querySelector("input[type='radio'][value='Female']") || 
                document.querySelectorAll("input[type='radio']")[1];
    if(radio) { radio.click(); radio.checked = true; radio.dispatchEvent(new Event('change', { bubbles: true })); }
""")
print("5. Selecting Selenium WebDriver...")
driver.execute_script("""
    var chk = document.querySelector("input[type='checkbox'][value*='Selenium']") || 
              document.querySelectorAll("input[type='checkbox']")[0];
    if(chk) { chk.click(); chk.checked = true; chk.dispatchEvent(new Event('change', { bubbles: true })); }
""")
print("6. Filling Street Address...")
driver.execute_script("""
    var el = document.querySelector("input[name*='address'][name*='[address]'], input[id*='address']:not([id*='2'])");
    if(el) { el.value = '123 Automation Lane'; el.dispatchEvent(new Event('input', { bubbles: true })); }
""")
print("7. Filling Apt / Suite...")
driver.execute_script("""
    var el = document.querySelector("input[name*='address-2'], input[id*='address-2']");
    if(el) { el.value = 'Vedagiri vari palli'; el.dispatchEvent(new Event('input', { bubbles: true })); }
""")
print("8. Filling City...")
driver.execute_script("""
    var el = document.querySelector("input[name*='city'], input[id*='city']");
    if(el) { el.value = 'Chittoor'; el.dispatchEvent(new Event('input', { bubbles: true })); }
""")
print("9. Filling State...")
driver.execute_script("""
    var el = document.querySelector("input[name*='state'], input[id*='state']");
    if(el) { el.value = 'Andhra Pradesh'; el.dispatchEvent(new Event('input', { bubbles: true })); }
""")
print("10. Filling Zip Code...")
driver.execute_script("""
    var el = document.querySelector("input[name*='zip'], input[id*='zip']");
    if(el) { el.value = '517152'; el.dispatchEvent(new Event('input', { bubbles: true })); }
""")
print("11. Selecting Country...")
driver.execute_script("""
    var country = document.querySelector("select[name*='country'], select[id*='country']");
    if(country) {
        country.value = "India";
        country.dispatchEvent(new Event('change', { bubbles: true }));
    }
""")
print("12. Filling Email...")
email_input = wait.until(
    EC.presence_of_element_located((
        By.XPATH, 
        "//label[contains(text(), 'Email')]/following::input[1]"
    ))
)
driver.execute_script("arguments[0].scrollIntoView({block: 'center'});", email_input)
email_input.clear()
email_input.send_keys("indusree2023@gmail.com")
print("\n==========================================")
print("SUCCESS: Filled up to Email successfully!")
print("==========================================")
input("\nPress ENTER here in the terminal to close Chrome...")
driver.quit()

```
### Output
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0a99ac9c-2ca8-408b-880d-90af0a88bd30" />

