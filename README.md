# Google Image Scraper
A library to scrap google images.<br>
If you are looking for other image scrapers.<br>
JJLimmm has created an image scrapper for getty, shuttershock, and bing. <br>
Visit his repo here: https://github.com/JJLimmm/Website-Image-Scraper

## Pre-requisites:
1. Pip install Selenium Library
2. Pip install PIL
3. Download Google Chrome 
4. Download Google Webdriver based on your Chrome version

```bash
# install X virtual framebuffer in memory
sudo apt update 
sudo apt install -y xvfb libxi6 libgconf-2-4

# install chrome
sudo curl -sS -o - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add 
sudo bash -c "echo 'deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main' >> /etc/apt/sources.list.d/google-chrome.list" 
sudo apt -y update 
sudo apt -y install google-chrome-stable 

# install chromedriver
google-chrome --version 
# based on the version download the right driver from next webpage
# https://chromedriver.chromium.org/downloads
wget https://chromedriver.storage.googleapis.com/[?????????]/chromedriver_linux64.zip 
unzip chromedriver_linux64.zip 

# move it to the right place
sudo mv chromedriver /usr/bin/chromedriver 
sudo chown root:root /usr/bin/chromedriver 
sudo chmod +x /usr/bin/chromedriver
```

## Setup:
1. Open cmd
2. Clone the repository (or [download](https://github.com/ohyicong/Google-Image-Scraper/archive/refs/heads/master.zip))
    ```
    git clone https://github.com/ohyicong/Google-Image-Scraper
    ```
3. Install Dependencies
    ```
    pip install -r requirements.txt
    ```
4. Run the code
    ```
    python main.py
    ```

## Usage:
```python
#Import libraries (Don't change)
from GoogleImageScrapper import GoogleImageScraper
import os
from pyvirtualdisplay import Display

#Define file path (Don't change)
webdriver_path = 'chromedriver'
image_path = os.path.normpath(os.path.join(os.getcwd(), 'photos'))

#Add new search key into array ["cat","t-shirt","apple","orange","pear","fish"]
search_keys= ["cat","t-shirt"]

#Parameters
number_of_images = 10
headless = True
min_resolution=(0,0)
max_resolution=(1920,1080)

# run on the virtual framebuffer
display = Display(backend='xvfb')
display.start()


#Main program
for search_key in search_keys:
    image_scrapper = GoogleImageScraper(webdriver_path,image_path,search_key,number_of_images,headless,min_resolution,max_resolution)
    image_urls = image_scrapper.find_image_urls()
    image_scrapper.save_images(image_urls)
    
display.stop()

```
## Youtube Video:
[![IMAGE ALT TEXT](https://github.com/ohyicong/Google-Image-Scraper/blob/master/youtube_thumbnail.PNG)](https://youtu.be/QZn_ZxpsIw4 "Google Image Scraper")

Do remember to like, share and subscribe!
