Emma2Click toolset supports Magento debugging with Xdebug out of the box. Only a few configuration steps are required.

## Configuration for PHPStorm IDE

Open **Servers** preferences section.

```
Preferences | Languages & Frameworks | PHP | Servers
```

Add the new server to match your project and configure path mappings. Your project directory must be mapped to `/var/www/html` path. Don't forget to press `Apply` or `OK` button. Check the screenshot below as reference.
![Configuration of servers](assets/images/xdebug-configuration-servers.png)

After that, go to the **PHP** preferences section.

```
Preferences | Languages & Frameworks | PHP
```

Select **PHP language level** to match PHP version used in your Magento project.

For **CLI Interpreter**, click on three dots to add new one. A new **CLI Interpreters** dialog box will appear, press on plus (+) sign and choose `From Docker, Vagrant, VM, Remote...`
![Configuration CLI interpreters](assets/images/xdebug-configuration-cli-interpreters.png)

In the appeared dialog box, select `Docker` and for **Image name** choose mage2click xdebug Docker image with corresponding PHP version to your Magento project, for example `mage2click/m2c:php-fpm-7.2-xdebug-alpine`. Press `OK`.
![Configuration remote interpreters](assets/images/xdebug-configuration-remote-php-interpreter.png)

Also, press `OK` on **CLI Interpreters** dialogue box.
![Configuration CLI interpreters](assets/images/xdebug-configuration-cli-interpreters.png)

Make sure that newly created **CLI Interpreter** is selected and press `OK` on **PHP** preferences section.
![Configuration preferences](assets/images/xdebug-configuration-php-preferences.png)

## Usage
To start/stop debugging, press `Start/Stop Listening for PHP Debug Connections` button.
![Start stop debugging](assets/images/xdebug-configuration-start-stop-debugging.png)

On the browser side, you will need to set `XDEBUG_SESSION` cookie to activate Xdebug or simply use **Xdebug Helper** browser extension for that.
![Xdebug browser configuration](assets/images/xdebug-configuration-browser.png)
