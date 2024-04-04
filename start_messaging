import time
import datetime
from selenium import webdriver
from selenium.webdriver.common.keys import Keys

def send_whatsapp_message(contact_name, message):
    # Шлях до веб-драйвера Chromium
    driver_path = '/usr/bin/chromedriver'

    # URL WhatsApp Web
    url = 'https://web.whatsapp.com/'

    # Запуск веб-браузера Chromium
    options = webdriver.ChromeOptions()
    options.add_argument('--no-sandbox')
    options.add_argument('--disable-dev-shm-usage')
    driver = webdriver.Chrome(executable_path=driver_path, options=options)
    driver.get(url)

    # Очікування, доки користувач увійде у WhatsApp Web
    while True:
        try:
            driver.find_element_by_xpath("//div[@title='Запустіть WhatsApp у телефоні, щоб сканувати код']")
            time.sleep(1)
        except:
            break

    # Пошук контакту та відправлення повідомлення
    search_box = driver.find_element_by_xpath("//div[@contenteditable='true'][@data-tab='3']")
    search_box.send_keys(contact_name)
    time.sleep(2)
    driver.find_element_by_xpath("//span[contains(@title,'" + contact_name + "')]").click()

    message_box = driver.find_element_by_xpath("//div[@contenteditable='true'][@data-tab='1']")
    message_box.send_keys(message)
    message_box.send_keys(Keys.ENTER)

    # Закриття браузера
    driver.quit()

if __name__ == "__main__":
    # Встановлення адресата та повідомлення
    recipient = "Ім'я користувача або номер телефону"
    message = "Ваше підготовлене повідомлення тут"

    # Отримання поточного часу
    current_time = datetime.datetime.now()

    # Очікування до встановленого часу
    target_time = current_time.replace(hour=10, minute=0, second=0, microsecond=0)  # Встановлюємо час 10:00 AM
    while current_time < target_time:
        current_time = datetime.datetime.now()
        time.sleep(60)  # Очікування 60 секунд перед перевіркою часу

    # Відправлення повідомлення
    send_whatsapp_message(recipient, message)
