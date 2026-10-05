## Task 1-Swag Labs
### Program
```
from selenium import webdriver
from selenium.webdriver.common.by import By

driver = webdriver.Chrome()

driver.get("https://www.saucedemo.com/")

username = driver.find_element(By.ID, "user-name")
password = driver.find_element(By.NAME, "password")
login = driver.find_element(By.ID, "login-button")

username.send_keys("standard_user")
password.send_keys("secret_sauce")

print(username.get_attribute("placeholder"))
print(login.is_enabled())
print(username.is_displayed())
input("Press Enter to close the browser...")

driver.quit()
```
### Output
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/b247b489-b299-4985-a1ed-05f498a53867" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/159f965d-450c-4f33-89d5-aca57b9c118c" />
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/e2f6a8d0-0152-4cc1-ba0f-dbc072e33932" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/55e67788-250d-4a3b-96c7-26f93a8c643a" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/67eb4eb9-15ec-4869-9260-cf1d34391de2" />
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/ebd1ca09-d124-4244-b690-176fc5d0a93f" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/c7a8cb39-5086-4e93-8f17-e682407dc62e" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ec7f5a59-c2f1-4c27-850b-8c253e4b4de3" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/ace815f5-be2a-4c62-8ccc-dd9406c8f447" />

## Task 2-Flipkart 
### Program
```
import time
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.common.exceptions import TimeoutException

chrome_options = Options()
chrome_options.add_experimental_option("detach", True)
chrome_options.add_argument("--start-maximized")

driver = webdriver.Chrome(options=chrome_options)

try:
    driver.get("https://www.flipkart.com/account/login")
    wait = WebDriverWait(driver, 15)

    
    input_field = wait.until(
        EC.element_to_be_clickable((By.XPATH, "//input[@type='text']"))
    )
    input_field.clear()
    phone_number = "YOUR_PHONE_NUMBER_OR_EMAIL"
    input_field.send_keys(phone_number)

   
    login_button = wait.until(
        EC.element_to_be_clickable(
            (By.XPATH, "//button[contains(., 'Request OTP') or contains(., 'CONTINUE') or contains(., 'Continue')]")
        )
    )
    driver.execute_script("arguments[0].click();", login_button)
    print("Requested OTP...")

  
    otp_code = input("\nEnter the OTP received via SMS: ").strip()

    
    otp_inputs = driver.find_elements(By.XPATH, "//form//input[contains(@class, 'r4vIwl') or @maxlength='1']")
    if len(otp_inputs) == 6:
        for index, digit in enumerate(otp_code[:6]):
            otp_inputs[index].send_keys(digit)
    else:
        single_otp_box = wait.until(
            EC.element_to_be_clickable((By.XPATH, "//input[@type='text' or @type='number']"))
        )
        single_otp_box.send_keys(otp_code)

  
    verify_button = wait.until(
        EC.element_to_be_clickable(
            (By.XPATH, "//button[contains(., 'Verify') or contains(., 'VERIFY') or contains(., 'Login')]")
        )
    )
    driver.execute_script("arguments[0].click();", verify_button)
    print("\nSMS OTP verified. Moving to Phone Call Verification step...")

    
    post_otp_wait = WebDriverWait(driver, 20)

    call_trigger_xpath = (
        "//button[contains(translate(., 'CALL', 'call'), 'call') or contains(translate(., 'VOICE', 'voice'), 'voice')] | "
        "//a[contains(translate(., 'CALL', 'call'), 'call') or contains(translate(., 'VOICE', 'voice'), 'voice')] | "
        "//span[contains(translate(., 'CALL', 'call'), 'call') or contains(translate(., 'VOICE', 'voice'), 'voice')]"
    )

    try:
        call_btn = post_otp_wait.until(EC.element_to_be_clickable((By.XPATH, call_trigger_xpath)))
        driver.execute_script("arguments[0].click();", call_btn)
        print(">> Triggered 'Call Verification' button on screen.")
    except TimeoutException:
        print(">> No separate call button required (Flipkart is calling automatically or redirecting).")

    print("\n-----------------------------------------------------")
    print("Flipkart is placing the verification call to your phone.")
    print("Answer the call and follow the automated instructions.")
    print("-----------------------------------------------------")
    call_otp_inputs = driver.find_elements(By.XPATH, "//form//input[@type='text' or @type='number']")
    if call_otp_inputs:
        call_code = input("\nIf the call spoke an OTP/code to enter on screen, type it here (otherwise press Enter): ").strip()
        if call_code:
            if len(driver.find_elements(By.XPATH, "//input[@maxlength='1']")) == len(call_code):
                boxes = driver.find_elements(By.XPATH, "//input[@maxlength='1']")
                for i, char in enumerate(call_code):
                    boxes[i].send_keys(char)
            else:
                call_otp_inputs[0].send_keys(call_code)
            try:
                final_btn = driver.find_element(By.XPATH, "//button[contains(., 'Submit') or contains(., 'Verify') or contains(., 'Confirm')]")
                driver.execute_script("arguments[0].click();", final_btn)
            except Exception:
                pass

    print("\nVerification complete! Checking logged-in state...")
    time.sleep(5)

except Exception as e:
    print(f"\n--- ERROR OCCURRED ---\n{e}\n-------------------------\n")

finally:
    input("\nPress Enter in the terminal to close the browser session...")
```
### Output
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/54cd4848-bb14-4372-bcbf-56246b0f29fc" />
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/f678756c-8a1a-4b34-8604-cf01f0955f9d" />
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/426b515b-36f6-4b0a-b6d3-bba78a1f7408" />
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/fec73ed8-11bf-444a-9632-dc486f5bce9b" />

