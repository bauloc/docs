**mitmproxy** is a free and open source interactive HTTPS proxy.

# Homepage
https://mitmproxy.org/

Install
```
brew install mitmproxy
```

# HTTP
- Ready to use

# HTTPS
- Install mitmproxy certificate
- Open safari in iphone http://mitm.it

## How to install on macOS
* Double-click the PEM file
* The "Keychain Access" applications opens
* Find the new certificate "mitmproxy" in the list
* Double-click the "mitmproxy" entry
* A dialog window openes up
* Change "Secure Socket Layer (SSL)" to "Always Trust"
* Close the dialog window (and enter your password if prompted)
* Done!

## How to install on iOS 13+
* Install and active the new Profile
* Goto Settings -> General -> About -> Certificate Trust Settings
* Toggle mitmproxy to ON
* Done!

## How to install on browsers
* Safari on macOS uses the macOS keychain. So installing our CA in the system is enough.
* Chrome on macOS uses the macOS keychain. So installing our CA in the system is enough.
* Firefox on macOS has its own CA store and needs to be installed with Firefox-specific instructions that can be found [https://wiki.mozilla.org/MozillaRootCertificate#Mozilla_Firefox].

# Example
## Step1: In macos Terminal
**Use GUI**
```
mitmweb
```
**User TUI**
```
mitmproxy
```
## Step2: In iphone
- Setup HTTP Proxy to current wifi connected
- Configure Proxy -> Manual
- Server: **macos ip** [ex: 10.0.3.138]
- Port: **8080**

## Step3: Make a few connections on the iPhone to see the results

Status

```
Last login: Thu Oct 29 09:13:38 on ttys003
bauloc@BAUs-MBP-New ~ % mitmweb
Web server listening at http://127.0.0.1:8081/
Proxy server listening at http://*:8080
10.0.3.130:64308: clientconnect
10.0.3.130:64308: clientdisconnect
10.0.3.130:64309: clientconnect
10.0.3.130:64309: clientdisconnect
10.0.3.130:64310: clientconnect
10.0.3.130:64310: clientdisconnect
10.0.3.130:64311: clientconnect
```

Request

```
Last login: Thu Oct 29 10:42:52 on ttys001
bauloc@BAUs-MBP-New ~ % mitmproxy
>>11:09:43 HTTPS POST ….googleapis.com /v1/firelog/legacy/batchlog                                       200 …ion/x-protobuf   30b 192ms 
  11:09:43 HTTPS POST …ph.facebook.com /v6.0/693867204034086/activities                                  200 …plication/json   16b 706ms 
  11:09:44 HTTPS GET   api.fptplay.net /api/ver6.2_ios/structure/highlights?st=TUM87U6qjDUyjvRpkdviOQ&e… 200 …plication/json 5.95k  28ms 
  11:09:44 HTTPS POST …s.appsflyer.com /api/v5.2/iosevent?app_id=646297996&buildnumber=5.2.0             200 …plication/json    4b 236ms 
  11:09:44 HTTPS GET   api.fptplay.net /api/ver6.2_ios/highlight?st=-gED-tAUwHmnHe7VHlC1og&e=1603987784… 200 …plication/json  3.7k  23ms 
  11:09:44 HTTPS GET   api.fptplay.net /api/ver6.2_ios/highlight?st=-gED-tAUwHmnHe7VHlC1og&e=1603987784… 200 …plication/json  4.1k  25ms 
  11:09:44 HTTPS GET   api.fptplay.net /api/ver6.2_ios/highlight?st=-gED-tAUwHmnHe7VHlC1og&e=1603987784… 200 …plication/json 4.13k  32ms 
  11:09:44 HTTPS GET   api.fptplay.net /api/ver6.2_ios/highlight?st=-gED-tAUwHmnHe7VHlC1og&e=1603987784… 200 …plication/json 4.38k  21ms 
  11:09:44 HTTPS GET   api.fptplay.net /api/ver6.2_ios/highlight?st=-gED-tAUwHmnHe7VHlC1og&e=1603987784… 200 …plication/json 2.46k  21ms 
  11:09:44 HTTPS GET   api.fptplay.net /api/ver6.2_ios/highlight?st=-gED-tAUwHmnHe7VHlC1og&e=1603987784… 200 …plication/json 3.28k  18ms 
  11:09:44 HTTPS GET   api.fptplay.net /api/ver6.2_ios/highlight?st=-gED-tAUwHmnHe7VHlC1og&e=1603987784… 200 …plication/json 3.26k  21ms 
  11:09:44 HTTPS GET   api.fptplay.net /api/ver6.2_ios/highlight?st=-gED-tAUwHmnHe7VHlC1og&e=1603987784… 200 …plication/json 3.38k  19ms 
  11:09:45 HTTPS GET    ua.fptplay.net /i?p=ios&eid=18b2d5ab-a4b5-45c4-9493-1c2bdcfcc9b3&aid=fptplay&nt… 200       image/gif   43b 143ms 
  11:09:45 HTTPS GET    ua.fptplay.net /i?p=ios&eid=7937d55f-5ad9-4443-902e-0f073f19c986&aid=fptplay&nt… 200       image/gif   43b 157ms 
  11:09:45 HTTPS GET    ua.fptplay.net /i?p=ios&tz=GMT%2B07:00&res=375.0x667.0&dtm=2020-10-29%2011:09:4… 200       image/gif   43b 174ms 
  11:09:45 HTTPS GET    ua.fptplay.net /i?p=ios&tz=GMT%2B07:00&res=375.0x667.0&dtm=2020-10-29%2011:09:4… 200       image/gif   43b 277ms 
  11:09:45 HTTPS GET   api.fptplay.net /api/ver6.2_ios/tv?st=uHMz5nQ5DQxhHcbbVFdwRQ&e=1603987785&user_i… 200 …plication/json ….99k 602ms 
  11:09:45 HTTPS GET   api.fptplay.net /api/ver6.2_ios/service/sport?st=Bn6V0xWCw7aoLOMg4ZktfA&e=160398… 200 …plication/json 2.32k 101ms 
  11:09:46 HTTPS GET    ua.fptplay.net /i?p=ios&dmf=Apple&ov=12.0.1&tna=fplay&dml=iPhone%207&dtm=2020-1… 200       image/gif   43b 874ms 
  11:09:46 HTTPS GET    ua.fptplay.net /i?p=ios&dmf=Apple&ov=12.0.1&tna=fplay&dml=iPhone%207&dtm=2020-1… 200       image/gif   43b 880ms 
```