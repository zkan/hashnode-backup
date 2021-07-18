## dbt คืออะไรนะ?

ตอนนี้ในสายงาน Data Engineering มีเครื่องมือตัวหนึ่งที่เริ่มเป็นที่รู้จักกันแล้ว นั่นก็คือ [dbt](https://www.getdbt.com/) หรือ data build tool ครับ เรามาลองทำความรู้จักกับมันดีกว่า ว่ามันคืออะไร แล้วทำไมเราถึงควรให้ความสนใจ 😉

> dbt (data build tool) enables data analysts and engineers to transform data in their warehouses. 

จาก [บทความ What, exactly, is dbt?](https://blog.getdbt.com/what-exactly-is-dbt/)  ของ  [Tristan Handy, Founder & CEO @ dbt Labs](https://twitter.com/jthandy)  และเป็นผู้สร้างเครื่องมือนี้ขึ้นมา

ผมจะแปลได้ประมาณว่า dbt เป็นเครื่องมือที่ช่วยให้ชีวิตของชาว Data Analysts และ Engineers ในการทำ Data Transformation หรือเปลี่ยนแปลงรูปแบบของข้อมูลใน Data Warehouse ดีขึ้น.. 😲 ซึ่งการใช้งาน dbt จะอยู่ในส่วนของ Data Warehouse เลย ทำหน้าที่หลักๆ คือส่วน "T" ใน  [ELT](https://www.talend.com/resources/what-is-elt/) หรือส่วน Transform นั่นเอง ตามรูปด้านล่างนี้ 👇

![dbt-in-data-pipeline.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626444896574/zxYdg5kAS.png)

### dbt น่าสนใจอย่างไร?

ก่อนอื่นเลยคือ ด้วยความที่เราสามารถเขียนโค้ด SQL บนเครื่องเราได้ แล้วสั่งให้ไปรันบน Data Warehouse ของเรา อีกทั้งยังสามารถแยก Environment ได้ว่าจะให้ไปรันที่ Development หรือ Production ตรงนี้ทำให้ Workflow ของเราในการทำ Analytics ดีขึ้น และคล่องขึ้น

การใช้ dbt ช่วยให้เราเขียน SQL Queries ได้ในขณะที่เราไม่ต้องกังวลเรื่องของ Dependencies เช่น เราต้องรัน Query A ก่อนนะ แล้วค่อยไปรัน Query B ข้อมูลใน View สุดท้ายเราถึงจะถูกต้อง ตรงนี้ dbt จัดการให้ ทำให้เรามั่นใจได้ว่าเราสามารถเขียน Query แยกออกจากกันเป็นส่วนๆ ได้ (ใช้ WITH Clause) โดยที่ผลลัพธ์ยังคงถูกต้อง

และเนื่องจากที่เราสามารถแยก Query เราออกเป็นส่วนๆ ได้แล้ว dbt ก็สามารถให้เราเอา SQL ที่เราเคยเขียนไปแล้วกลับมาใช้ได้ด้วย (reusable) 🤩

ความ Amazing ของ dbt ยังไม่จบนะ เครื่องมือตัวนี้ได้นำเอา Software Engineering Principles ต่างๆ เหล่านี้เข้ามาสู่โลก Analytics เช่น Testing, Documentation และ Version Control เป็นต้น

#### Testing

เราสามารถใช้ dbt ตรวจสอบคุณภาพของข้อมูล การเชื่อมต่อกันระหว่างตาราง และการทดสอบข้อมูลอะไรก็ตามที่เราเขียนขึ้นมาตาม Use Case ของเราเอง ในส่วนนี้เราสามารถเอาเข้าไปในกระบวนการ Continuous Integration ได้ด้วย

#### Documentation

dbt มีคำสั่งสร้าง Document ให้เราแบบอัตโนมัติเลย ตรงนี้ดีงามมาก เพราะเราสามารถเห็น Data Lineage ได้เลยว่า ข้อมูลจากตารางนี้ เกิดจากตารางไหนรวมกันกับตารางไหน หน้าตาแบบนี้เลย!

![dbt-data-lineage-example.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1626447125429/uOqOT7wqig.png)

#### Version Control

ตรงนี้หลายคนอาจจะบอกว่า เราก็เขียน SQL ใน Data Warehouse แล้วก็เอาโค้ดมาเข้า Version Control (VC) สิ ซึ่งผมบอกได้เลยว่าชีวิตเราก็จะลำบากในการคัดลอกโค้ดตรงนั้นออกมา สุดท้ายแล้วเราอาจจะลืมเอาเข้า VC เองด้วย 😅 การที่เราใช้ dbt เราจะสามารถรันคำสั่งบนเครื่องของเราต่อไปยัง Data Warehouse ได้ เราแก้โค้ดเมื่อไหร่ เราก็เอาเข้า VC ได้เลยทันที

อีกความสามารถหนึ่งของ dbt ก็คือการสามารถใช้  [Template หรือ Macro](https://docs.getdbt.com/docs/building-a-dbt-project/jinja-macros)  ได้ นั่นทำให้เราสามารถทำอะไรนอกเหนือจากที่ SQL ปกติทำได้ 👍

### สรุป

dbt เป็น Open-Source Tool ตัวหนึ่งที่น่าสนใจมากๆ น่าจะพัฒนามาได้ประมาณ 5 ปีแล้ว (นับปีจากตอนที่เขียนบทความนี้อยู่) แล้วก็เริ่มดังก็ประมาณ 2 ปีที่แล้ว (ผมนับจากที่มีคนไปพูดในงาน DataEngConf หรือ Data Council ในปัจจุบัน อิอิ)

%[https://www.youtube.com/watch?v=qqlbYDfqeI4]

นอกจากเครื่องมือตัวนี้จะช่วยส่งเสริมให้ Workflow และการทำงานต่างๆ เกี่ยวกับการปรับเปลี่ยน หรือบิดข้อมูลใน Data Warehouse ของเราดีขึ้น ยังช่วยให้เราทำงานร่วมกับคนอื่นได้ดีขึ้นด้วย เพราะมีข้อดีหลายๆ อย่างตามที่กล่าวไปด้านบน ลองดูกันครับ แล้วชีวิตของการทำ Data Transformation ของเราจะเปลี่ยนไป! (ในทางที่ดีขึ้นนะ)

ส่วนถ้าใครสงสัยเรื่องการเริ่มต้นใช้งาน เดี๋ยวบทความหน้าเราจะมาลองดูกันครับ 😎