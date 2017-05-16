# Charles Proxy Mobile Guide
The mobile hackers' guide to Charles Proxy :thumbsup:

## Intro

[Charles](https://www.charlesproxy.com/) is an HTTP proxy / HTTP monitor / Reverse Proxy that enables a developer to view all of the HTTP and SSL / HTTPS traffic between their machine and the Internet. This includes requests, responses and the HTTP headers (which contain the cookies and caching information).

## SSL Proxying

### Computer (macOS)

* **Charles** -> **Proxy** -> **SSL Proxying Settings...** -> **SSL Proxying**
    * Check "**Enable SSL Proxying**"
    * Add location matcher "**Host: &ast;**", "**Port: &ast;**"
    <img src="https://github.com/thyrlian/Charles-Proxy-Mobile-Guide/blob/master/Screenshots/macOS/SSL-Proxying-Settings.png">
* **Charles** -> **Help** -> **SSL Proxying** -> **Install Charles Root Certificate**
    * It would install the certificate to **Keychain**, and open it up automatically
    * Double click the certificate in Keychain
    * Expand **Trust**, select **Always Trust** for **When using this certificate**
    <img src="https://github.com/thyrlian/Charles-Proxy-Mobile-Guide/blob/master/Screenshots/macOS/Root-Certificate-not-trusted.png">
    <img src="https://github.com/thyrlian/Charles-Proxy-Mobile-Guide/blob/master/Screenshots/macOS/Root-Certificate-trusted.png">
* Get the **IP address** that Charles is listening to
    * **Charles** -> **Help** -> **Local IP Address**
    * Or get the WLAN IP address via command line (right into your clipboard)
        ```shell
        ifconfig | tr "\n" "→" | tr "\r" "→" | grep -Eo "→en0.*?→en[[:digit:]]" | grep -Eo "inet[[:blank:]+]([0-9]{1,3}\.){3}[0-9]{1,3}" | cut -d' ' -f2 | tr -d "\n" | pbcopy && pbpaste
        ```
    * Or get the LAN IP address via command line (right into your clipboard)
        ```shell
        ifconfig | tr "\n" "→" | tr "\r" "→" | grep -Eo "→en[[:digit:]].*?active→" | grep -v "en0" | grep -Eo "inet[[:blank:]+]([0-9]{1,3}\.){3}[0-9]{1,3}" | cut -d' ' -f2 | tr -d "\n" | pbcopy && pbpaste
        ```

### Android

* Launch **Charles** and keep it running
* Get the **IP address**
* Make sure the Android device uses the same network as Charles
* On **Android** device
    * Go to **Settings** -> **Wi-Fi** -> long click the **network** in use -> **Modify network** -> **Advanced options** -> **Proxy** -> **Manual**
    * Set **Proxy hostname** to the **IP address**, and **Proxy port** to **8888**, then click **Save**
    * Launch **Browser**, visit https://chls.pro/ssl, save the certificate
    * The system would ask you to set a lock screen **PIN** or **password**, just set one and save it
    * Now the certificate is installed
    * Open an application and monitor the traffic on Charles
* A dialog pops up on computer asking "A connection attempt to  Charles has been made from the host ...", just click **Allow** button

### iOS

