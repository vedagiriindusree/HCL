# WEB TABLES
### CODE
```
import re
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait, Select
from selenium.webdriver.support import expected_conditions as EC

def run_tests():
    driver = webdriver.Chrome()
    wait = WebDriverWait(driver, 10)

    try:
        driver.get("https://assertqa.com/practice/webtables")
        driver.maximize_window()

        table = wait.until(EC.presence_of_element_located((By.XPATH, "//table")))

        try:
            row_select_elem = driver.find_element(
                By.XPATH, 
                "//select[contains(@class, 'rows') or .//option[@value='15' or text()='15']]"
            )
            Select(row_select_elem).select_by_visible_text("15")
        except Exception:
            pass  
        print("\n--- TC01: Column Headings ---")
        headers = [
            th.text.strip() 
            for th in driver.find_elements(By.XPATH, "//table//thead//th") 
            if th.text.strip()
        ]
        print("Column Headings:", headers)

        print("\n--- TC02: First Data Row ---")
        first_row_cells = [
            td.text.strip() 
            for td in driver.find_elements(By.XPATH, "//table//tbody/tr[1]/td")
        ]
        print("First Row Record:", " | ".join(first_row_cells))

        print("\n--- TC03: Last Data Row ---")
        last_row_cells = [
            td.text.strip() 
            for td in driver.find_elements(By.XPATH, "//table//tbody/tr[last()]/td")
        ]
        print("Last Row Record:", " | ".join(last_row_cells))

        print("\n--- TC04: Search by Last Name ('Williams') ---")
        target_last_name = "Williams"
        matching_rows = driver.find_elements(
            By.XPATH, 
            f"//table//tbody/tr[td[contains(text(), '{target_last_name}')]]"
        )
        
        if matching_rows:
            for row in matching_rows:
                cells = [td.text.strip() for td in row.find_elements(By.TAG_NAME, "td")]
                print("Matching Record:", " | ".join(cells))
        else:
            print(f"No record found with last name '{target_last_name}'.")

        print("\n--- TC05: All Email Addresses ---")
        email_cells = driver.find_elements(By.XPATH, "//table//tbody/tr/td[4]")
        emails = [cell.text.strip() for cell in email_cells if cell.text.strip()]
        for idx, email in enumerate(emails, start=1):
            print(f"{idx}. {email}")

        print("\n--- TC06: Highest Compensation/Amount ---")
        rows = driver.find_elements(By.XPATH, "//table//tbody/tr")
        max_amount = -1.0
        highest_paid_employee = None

        for row in rows:
            cells = row.find_elements(By.TAG_NAME, "td")
            if len(cells) >= 6:
                name = f"{cells[1].text.strip()} {cells[2].text.strip()}"
                amount_str = cells[5].text.strip()
                cleaned_num = re.sub(r"[^\d.]", "", amount_str)
                if cleaned_num:
                    val = float(cleaned_num)
                    if val > max_amount:
                        max_amount = val
                        highest_paid_employee = (name, amount_str)

        if highest_paid_employee:
            print(f"Employee with highest amount: {highest_paid_employee[0]} ({highest_paid_employee[1]})")

        print("\n--- TC07: Verify Website Link Existence ---")
        target_url = "https://assertqa.com"
        links = driver.find_elements(By.XPATH, f"//table//a[contains(@href, '{target_url}')]")
        
        if links:
            print(f"PASS: Link matching '{target_url}' found in table.")
        else:
            print(f"FAIL: No link matching '{target_url}' exists within table cells.")

        print("\n--- TC08: Count Data Rows ---")
        data_rows = driver.find_elements(By.XPATH, "//table//tbody/tr")
        print(f"Total Data Rows in Current View: {len(data_rows)}")

    finally:
        input("\nPress Enter to close the browser...")
        driver.quit()

if __name__ == "__main__":
    run_tests()
```
### OUTPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/9f1c6308-34b6-4ac8-be50-983c0dec867b" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0ddc4057-db60-4294-84fc-84a862659935" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/76c3fd1a-61c4-4bb7-ad72-2f304b1dc163" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/638d86dc-32d2-4511-83ab-8e364456ef96" />


