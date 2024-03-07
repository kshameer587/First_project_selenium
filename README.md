# First_project_selenium
#This is a website which creates demo ticket online and I automated all the fields mentioned in this website using Selenium with Python.

#The code is mentioned below. However I do not used any function to optimize this code and I am still working on it.

from selenium import webdriver
from selenium.webdriver.common.by import By
import time
from selenium.webdriver.support.select import Select

driver = webdriver.Chrome()

driver.get("https://www.dummyticket.com/dummy-ticket-for-visa-application/")

# Radio button
driver.find_element(By.XPATH,"//input[@id='product_549']").click()
time.sleep(2)
# First name
name = driver.find_element(By.XPATH,"//input[@id='travname']")
name.send_keys("Shahmeer")
time.sleep(1)
# Last name
last_name = driver.find_element(By.XPATH,"//input[@id='travlastname']")
last_name.send_keys("Khan")
time.sleep(1)
# Text box
texting = driver.find_element(By.XPATH,"//textarea[@id='order_comments']")
texting.send_keys("han bhai yeh tou kisi aik passenger ka scene hai")
time.sleep(1)

# DOB
driver.find_element(By.XPATH, "//input[@id='dob']").click()
def DOB(mon,yea):
    month = Select(driver.find_element(By.XPATH, "//select[@aria-label='Select month']"))
    month.select_by_visible_text(mon)
    year = Select(driver.find_element(By.XPATH, "//select[@aria-label='Select year']"))
    year.select_by_visible_text(yea)
    time.sleep(1)
    alldates = driver.find_elements(By.XPATH, "//*[@id='ui-datepicker-div']/table/tbody/tr/td/a")
    for dates in alldates:
        if dates.text == "11":
            dates.click()
            time.sleep(1)
            break

DOB("Jul","1999")
# Sex / gender
time.sleep(2)
driver.find_element(By.XPATH,"//input[@id='sex_1']").click()
time.sleep(1)

# checkbox of add more passengers

driver.find_element(By.XPATH,"//input[@id='addmorepax']").click()
time.sleep(1)

driver.find_element(By.XPATH,"(//span[@role='presentation'])[1]").click()
all_drop = driver.find_elements(By.XPATH,"//ul[@id='select2-addpaxno-results']/li")
for drops in all_drop:
    if drops.text == "add 1 more passenger (100%)":
        drops.click()
        time.sleep(1)
        break

#
# adding first name for second passengers
name = driver.find_element(By.XPATH,"//input[@id='travname2']")
name.send_keys("Abdullah")
#time.sleep(1)
# Last name for second passengers
last_name = driver.find_element(By.XPATH,"//input[@id='travlastname2']")
last_name.send_keys("Khan")
time.sleep(1)

# DOB for second passengers
driver.find_element(By.XPATH,"//input[@id='dob2']").click()
DOB("Jul","2000")
"""driver.find_element(By.XPATH,"//input[@id='dob2']").click()
month = Select(driver.find_element(By.XPATH,"//select[@aria-label='Select month']"))
month.select_by_visible_text("Jul")
year = Select(driver.find_element(By.XPATH,"//select[@aria-label='Select year']"))
year.select_by_visible_text("2000")
#time.sleep(1)
alldates = driver.find_elements(By.XPATH,"//*[@id='ui-datepicker-div']/table/tbody/tr/td/a")
for dates in alldates:
    if dates.text == "12":
        dates.click()
        time.sleep(1)
        break"""

# Sex / gender for second passengers
driver.find_element(By.XPATH,"//input[@id='sex2_1']").click()
#time.sleep(1)

# passenger's type

driver.find_element(By.XPATH,"//span[@id='select2-paxtype2-container']").click()

agin_drop = driver.find_elements(By.XPATH,"//ul[@id='select2-paxtype2-results']/li")
for dropkaro in agin_drop:
    if dropkaro.text == "Child":
        dropkaro.click()
        time.sleep(1)
        break

# trip type
driver.find_element(By.XPATH,"//input[@id='traveltype_2']").click()
#time.sleep(2)

driver.find_element(By.XPATH,"//input[@id='fromcity']").send_keys("Karachi")
driver.find_element(By.XPATH,"//input[@id='tocity']").send_keys("Lahore")



# DOB for second passengers

driver.find_element(By.XPATH,"//input[@id='departon']").click()
DOB("May","2025")
"""month = Select(driver.find_element(By.XPATH,"//select[@aria-label='Select month']"))
month.select_by_visible_text("May")
year = Select(driver.find_element(By.XPATH,"//select[@aria-label='Select year']"))
year.select_by_visible_text("2025")
#time.sleep(2)
alldates = driver.find_elements(By.XPATH,"//*[@id='ui-datepicker-div']/table/tbody/tr/td/a")
for dates in alldates:
    if dates.text == "10":
        dates.click()
        time.sleep(1)
        break"""

driver.find_element(By.XPATH,"//input[@id='returndate']").click()
month = Select(driver.find_element(By.XPATH,"//select[@aria-label='Select month']"))
month.select_by_visible_text("Dec")
year = Select(driver.find_element(By.XPATH,"//select[@aria-label='Select year']"))
year.select_by_visible_text("2025")
#time.sleep(2)
alldates = driver.find_elements(By.XPATH,"//*[@id='ui-datepicker-div']/table/tbody/tr/td/a")
for dates in alldates:
    if dates.text == "7":
        dates.click()
        time.sleep(1)
        break

driver.find_element(By.XPATH,"//textarea[@id='notes']").send_keys("chal be")


driver.find_element(By.XPATH,"//span[@id='select2-reasondummy-container']").click()

allticket = driver.find_elements(By.XPATH,"//ul[@id='select2-reasondummy-results']/li")

for ticket in allticket:
    if ticket.text == "Visa extension":
        ticket.click()
        time.sleep(1)
        break

driver.find_element(By.XPATH,"//input[@id='deliverymethod_2']").click()
#time.sleep(2)

driver.find_element(By.XPATH,"//input[@id='billname']").send_keys("Anwer")
driver.find_element(By.XPATH,"//input[@id='billing_phone']").send_keys("123456789")
driver.find_element(By.XPATH,"//input[@id='billing_email']").send_keys("kshameer587@gmail.com")
#time.sleep(2)

driver.find_element(By.XPATH,"//span[@id='select2-billing_country-container']").click()
country = driver.find_elements(By.XPATH,"//ul[@id='select2-billing_country-results']/li")
for allcountry in country:
    if allcountry.text == "India":
        allcountry.click()
        time.sleep(1)
        break

driver.find_element(By.XPATH,"//input[@id='billing_address_1']").send_keys("R-231")
driver.find_element(By.XPATH,"//input[@id='billing_address_2']").send_keys("R-231")
driver.find_element(By.XPATH,"//input[@id='billing_city']").send_keys("pakistan")

driver.find_element(By.XPATH,"//*[@id='select2-billing_state-container']/span").click()
allcity = driver.find_elements(By.XPATH,"//ul[@id='select2-billing_state-results']/li")
for city in allcity:
    if city.text == "Goa":
        city.click()
        time.sleep(1)
        break

driver.find_element(By.XPATH,"//input[@id='billing_postcode']").send_keys("74621")
time.sleep(2)
radiokatext = driver.find_element(By.XPATH,"//*[@id='order_review']/div[1]/table/tbody/tr/td[2]/span").text
print("The text of radio button at the start",radiokatext)

tablekatext = driver.find_element(By.XPATH,"//*[@id='order_review']/div[1]/table/tfoot/tr[3]/td/strong/span").text
print("The text of the result button at the end",tablekatext)

if radiokatext == tablekatext:
    print("no additional passengers added")
else:
    print("additional passengers added")
time.sleep(5)
