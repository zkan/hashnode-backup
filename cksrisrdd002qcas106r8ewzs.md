## ลองเล่น  Configuration File Parser ของ Python

ในการสร้างแอพพลิเคชั่นหรือระบบอะไรก็ตาม จะมีไฟล์ Configuration เพื่อให้เราปรับค่าต่างๆ ให้ระบบทำงานตามที่เราอยากจะให้เป็นได้ ทีนี้ใน Python ก็มีโมดูลหนึ่งที่อยู่ใน Standard Library ที่เอาไว้อ่านไฟล์ Configuration เป็นแบบ  [INI](https://en.wikipedia.org/wiki/INI_file)  และมีมานานแล้วด้วย เราไปรู้จักกับโมดูลนี้กันครับ มันมีชื่อว่า  [configparser](https://docs.python.org/3/library/configparser.html)  นั่นเอง

เราไม่ต้องติดตั้งอะไรเพิ่มเติมเลย เริ่มต้นเราอาจจะมีไฟล์ Configuration ตามนี้ ชื่อ `main.conf`

```
[DEFAULT]
ServerAliveInterval = 45
Compression = yes
CompressionLevel = 9
ForwardX11 = yes

[bitbucket.org]
User = hg

[topsecret.server.com]
Port = 50022
ForwardX11 = no
```

จากไฟล์ด้านบนนี้จะแบ่งออกเป็น 3 Sections ครับ นั่นก็คือ `DEFAULT`, `bitbucket.org` และ `topsecret.server.com` โดยที่ `DEFAULT` (ตัวใหญ่หมด) นี่จะเป็น Section พิเศษหน่อยๆ คือ ค่าที่อยู่ข้างใน Section นี้ จะตามไปเป็นค่า Default ใน Section อื่นๆ ด้วย

เริ่มต้นการใช้งานเราก็จะอิมพอร์ตมันเข้ามา และสร้าง `parser` ขึ้นมาตามนี้

```py
import configparser


parser = configparser.ConfigParser()
parser.read("main.conf")
```

ถ้าเราอยากรู้ว่าโค้ดเราอ่านมาถูกต้องหรือเปล่า ลองคำสั่งนี้ได้ครับ ซึ่งมันจะแสดง Section ทั้งหมดออกมา (ไม่รวม `DEFAULT` นะ)

```py
sections = parser.sections()
print("Sections:", sections)
```

ถ้าเราอยากได้ค่าที่อยู่ข้างใน Section `DEFAULT` เราจะเขียนแบบนี้

```py
server_alive_interval = parser["DEFAULT"]["ServerAliveInterval"]
print("ServerAliveInterval:", server_alive_interval)
```

หรือ แบบด้านล่างนี้ก็ได้ ได้ผลลัพธ์เหมือนกัน

```py
another_server_alive_interval = parser.get("DEFAULT", "ServerAliveInterval")
print("Another ServerAliveInterval:", another_server_alive_interval)
```

ส่วนค่าที่เหลือก็เขียนโค้ดตามนี้ได้เลย (ซึ่งจะเห็นว่าใน Section อื่นๆ สามารถดึงค่า Default ออกมาได้)

```py
bitbucket_user = parser.get("bitbucket.org", "User")
print("Bitbucket User:", bitbucket_user)

bitbucket_server_alive_interval = parser.get("bitbucket.org", "ServerAliveInterval")
print("Bitbucket ServerAliveInterval:", bitbucket_server_alive_interval)

bitbucket_forward_x11 = parser.get("bitbucket.org", "ForwardX11")
print("Bitbucket ForwardX11:", bitbucket_forward_x11)

topsecret_port = parser.get("topsecret.server.com", "Port")
print("Topsecret Port:", topsecret_port)

topsecret_forward_x11 = parser.get("topsecret.server.com", "ForwardX11")
print("Topsecret ForwardX11:", topsecret_forward_x11)
```

ดูแล้วไม่วุ่ยวาย และดู Simple ดีใช่ไหมครับ 😇 ก็ลองเอาไปประยุกต์ใช้งานกันได้นะ บางทีเราอาจจะไม่ได้อยากได้ Configuration ที่อลังการมาก ถึงกับต้องไปใช้ Framework อะไรแบบนี้กันเลยทีเดียว ซึ่ง Library ตัวนี้ก็ตอบโจทย์ในแง่ของ Keep It Simple & Stupid ดีนะ 😉