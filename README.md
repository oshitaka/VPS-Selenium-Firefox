# VPS-Selenium-Firefox
Troubleshooting of non working Firefox with Selenium on VPS

If default tweaks doesn't work this might help you to manage

1. Create a project directory and enter it
2. Create [[env for Python|virtual enviroment]] and activate it
3. Update `pip install -U pip` and `pip install -U setuptools`
4. Install Selenium: `pip install selenium`

> > [!Source]-
> > Port problems: https://serverfault.com/questions/1142186/could-not-start-a-new-session-response-code-500-message-failed-to-read-marion
> > Dependencies needed: https://stackoverflow.com/questions/67090130/webdriverexception-process-unexpectedly-closed-with-status-255-selenium-ge
> 
> Manual installation
> 1. Delete firefox if installed: `apt purge firefox`
> 2. Find latest release [here](https://download-installer.cdn.mozilla.net/pub/firefox/releases/) 
> 3. Download latest release: `
wget https://download-installer.cdn.mozilla.net/pub/firefox/releases/116.0.3/linux-x86_64/en-US/firefox-116.0.3.tar.bz2`
> 4. Unpack archive into opt: `tar -xf firefox-116.0.3.tar.bz2 --directory /opt/`
> 5. Create simlink: `ln -s /opt/firefox/firefox /usr/bin/firefox`
> 6. Install dependencies `apt-get update && apt-get install -y wget bzip2 libxtst6 libgtk-3-0 libx11-xcb-dev libdbus-glib-1-2 libxt6 libpci-dev`
> 7. Check latest driver [release](https://github.com/mozilla/geckodriver/releases/)
> 8. Download latest driver: `wget https://github.com/mozilla/geckodriver/releases/download/v0.29.0/geckodriver-v0.29.0-linux32.tar.gz`
> 9. Unpack driver: `tar -xzvf geckodriver-v0.29.0-linux32.tar.gz`

3. Update packages: `apt update && apt upgrade -y`
4. Use paths to firefox and driver in script:
```python
options.binary_location = "/usr/bin/firefox"
service = Service(executable_path="/home/user/projectname/geckodriver")
```

Note that you can place firefox and driver in any directory you like
