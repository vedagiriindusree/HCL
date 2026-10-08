# Xpath
### CODE
```
import time
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select, WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

driver = webdriver.Chrome()
driver.maximize_window()
wait = WebDriverWait(driver, 10)

try:
    try:
        print("Executing TC01...")
        driver.get("https://demoqa.com/automation-practice-form")
        assert "DEMOQA" in driver.title
        print("TC01 Passed: Registration page opened successfully.\n")
    except Exception as e:
        print(f"TC01 Failed: {e}\n")

    try:
        print("Executing TC02...")
        username_field = driver.find_element(By.XPATH, "//input[@id='firstName']")
        username_field.clear()
        username_field.send_keys("John")
        print("TC02 Passed: Username field located using attribute XPath.\n")
    except Exception as e:
        print(f"TC02 Failed: {e}\n")

    try:
        print("Executing TC03...")
        email_field = driver.find_element(By.XPATH, "//input[@id='userEmail']")
        email_field.clear()
        email_field.send_keys("john.doe@example.com")
        print("TC03 Passed: Password/Email field entered using attribute XPath.\n")
    except Exception as e:
        print(f"TC03 Failed: {e}\n")


    try:
        print("Executing TC04...")
        submit_btn = driver.find_element(By.XPATH, "//button[text()='Submit']")
        assert submit_btn.is_displayed()
        print("TC04 Passed: Submit button located using text().\n")
    except Exception as e:
        print(f"TC04 Failed: {e}\n")

    try:
        print("Executing TC05...")
        dynamic_textbox = driver.find_element(By.XPATH, "//input[contains(@placeholder, 'First')]")
        assert dynamic_textbox.is_displayed()
        print("TC05 Passed: Dynamic textbox located using contains().\n")
    except Exception as e:
        print(f"TC05 Failed: {e}\n")

    try:
        print("Executing TC06...")
        mobile_field = driver.find_element(By.XPATH, "//input[starts-with(@id, 'userN')]")
        mobile_field.clear()
        mobile_field.send_keys("9876543210")
        print("TC06 Passed: Element located using starts-with().\n")
    except Exception as e:
        print(f"TC06 Failed: {e}\n")

    try:
        print("Executing TC07...")
        input_two_attr = driver.find_element(By.XPATH, "//input[@type='text' and @id='firstName']")
        assert input_two_attr.is_displayed()
        print("TC07 Passed: Input located using 'and' operator.\n")
    except Exception as e:
        print(f"TC07 Failed: {e}\n")

    try:
        print("Executing TC08...")
        input_or_attr = driver.find_element(By.XPATH, "//input[@id='lastName' or @id='invalidID']")
        assert input_or_attr.is_displayed()
        print("TC08 Passed: Element located using 'or' operator.\n")
    except Exception as e:
        print(f"TC08 Failed: {e}\n")

    try:
        print("Executing TC09...")
        parent_div = driver.find_element(By.XPATH, "//input[@id='firstName']/parent::div")
        assert parent_div.tag_name == "div"
        print("TC09 Passed: Parent element located successfully.\n")
    except Exception as e:
        print(f"TC09 Failed: {e}\n")

    try:
        print("Executing TC10...")
        ancestor_form = driver.find_element(By.XPATH, "//input[@id='firstName']/ancestor::form")
        assert ancestor_form.tag_name == "form"
        print("TC10 Passed: Ancestor form element located successfully.\n")
    except Exception as e:
        print(f"TC10 Failed: {e}\n")

    try:
        print("Executing TC11...")
        child_input = driver.find_element(By.XPATH, "//form[@id='userForm']//child::input[@id='firstName']")
        assert child_input.is_displayed()
        print("TC11 Passed: Child input located successfully.\n")
    except Exception as e:
        print(f"TC11 Failed: {e}\n")

    try:
        print("Executing TC12...")
        following_input = driver.find_element(By.XPATH, "//input[@id='firstName']/following::input[1]")
        following_input.clear()
        following_input.send_keys("Doe")
        print("TC12 Passed: Following element located successfully.\n")
    except Exception as e:
        print(f"TC12 Failed: {e}\n")

    try:
        print("Executing TC13...")
        checkbox = driver.find_element(By.XPATH, "//label[@for='hobbies-checkbox-1']")
        driver.execute_script("arguments[0].click();", checkbox)
        print("TC13 Passed: Checkbox located and selected.\n")
    except Exception as e:
        print(f"TC13 Failed: {e}\n")

    try:
        print("Executing TC14...")
        radio_btn = driver.find_element(By.XPATH, "//label[@for='gender-radio-1']")
        driver.execute_script("arguments[0].click();", radio_btn)
        print("TC14 Passed: Radio button located and selected.\n")
    except Exception as e:
        print(f"TC14 Failed: {e}\n")

    try:
        print("Executing TC15...")
        # Temporary switch to dropdown practice URL for native select verification
        driver.switch_to.new_window('tab')
        driver.get("https://the-internet.herokuapp.com/dropdown")
        dropdown_element = driver.find_element(By.XPATH, "//select[@id='dropdown']")
        select = Select(dropdown_element)
        select.select_by_visible_text("Option 1")
        print("TC15 Passed: Dropdown option selected successfully.\n")
        driver.close()
        driver.switch_to.window(driver.window_handles[0])
    except Exception as e:
        print(f"TC15 Failed: {e}\n")

    try:
        print("Executing TC16...")
        second_textbox = driver.find_element(By.XPATH, "(//input[@type='text'])[2]")
        assert second_textbox.is_displayed()
        print("TC16 Passed: Second textbox located via XPath index.\n")
    except Exception as e:
        print(f"TC16 Failed: {e}\n")

    try:
        print("Executing TC17...")
        driver.switch_to.new_window('tab')
        driver.get("https://the-internet.herokuapp.com/javascript_alerts")
        driver.find_element(By.XPATH, "//button[text()='Click for JS Alert']").click()
        
        alert = wait.until(EC.alert_is_present())
        alert.accept()
        
        result_text = driver.find_element(By.XPATH, "//p[contains(text(), 'You successfully clicked an alert')]")
        assert result_text.is_displayed()
        print("TC17 Passed: Submitted message verified using text().\n")
        driver.close()
        driver.switch_to.window(driver.window_handles[0])
    except Exception as e:
        print(f"TC17 Failed: {e}\n")

    try:
        print("Executing TC18...")
        inputs = driver.find_elements(By.XPATH, "//input")
        assert len(inputs) > 0
        print(f"TC18 Passed: Found {len(inputs)} input fields using find_elements().\n")
    except Exception as e:
        print(f"TC18 Failed: {e}\n")

   
    try:
        print("Executing TC19...")
        dynamic_elem = driver.find_element(By.XPATH, "//div[contains(@id, 'user')]")
        assert dynamic_elem.is_displayed()
        print("TC19 Passed: Dynamic element located using contains().\n")
    except Exception as e:
        print(f"TC19 Failed: {e}\n")

    try:
        print("Executing TC20: Complete Registration Automation Flow...")
        driver.get("https://demoqa.com/automation-practice-form")
        
        driver.find_element(By.XPATH, "//input[@id='firstName']").send_keys("John")
        
        
        driver.find_element(By.XPATH, "(//input[@type='text'])[2]").send_keys("Doe")
        
        
        driver.find_element(By.XPATH, "//input[contains(@id, 'userEmail')]").send_keys("john.doe@example.com")
        
        gender_radio = driver.find_element(By.XPATH, "//label[@for='gender-radio-1']")
        driver.execute_script("arguments[0].click();", gender_radio)
        
        
        driver.find_element(By.XPATH, "//input[starts-with(@id, 'userN')]").send_keys("9876543210")
        
  
        hobby_checkbox = driver.find_element(By.XPATH, "//label[@for='hobbies-checkbox-1']")
        driver.execute_script("arguments[0].click();", hobby_checkbox)
        
       
        submit_btn = driver.find_element(By.XPATH, "//button[text()='Submit']")
        driver.execute_script("arguments[0].click();", submit_btn)

        modal_title = wait.until(EC.visibility_of_element_located((By.XPATH, "//div[contains(@class, 'modal-title')]")))
        assert "Thanks for submitting" in modal_title.text
        
        print("TC20 Passed: Full student registration flow completed and verified successfully!\n")
    except Exception as e:
        print(f"TC20 Failed: {e}\n")

finally:
    input("All 20 test cases executed! Press ENTER in the terminal to close the browser...")
    driver.quit()
```
### OUTPUT
<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/8217f5c3-00a3-4c57-bb6d-bda328b73569" />

<img width="1600" height="900" alt="image" src="https://github.com/user-attachments/assets/53a9cc10-36bf-48d7-935b-1a7ad1d1463d" />


