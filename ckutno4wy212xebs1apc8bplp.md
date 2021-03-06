## ธนาคารไหนทำระบบได้ดีที่สุด? จากข้อมูลระบบออนไลน์ธนาคารไหนล่มมากที่สุดในรอบครึ่งปี 64

ขอบคุณรูปสวยๆ จาก <a href="https://unsplash.com/@jordanharrison?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Jordan Harrison</a> on <a href="https://unsplash.com/s/photos/server?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

จาก[โพสต์ของเพจ Marketeer Online](https://www.facebook.com/marketeeronline/photos/4658676524184407)  ที่มาบอกจำนวนครั้งที่ระบบออนไลน์ของธนาคารล่มตามรูปด้านล่างนี้

![Banking System Downtime](https://cdn.hashnode.com/res/hashnode/image/upload/v1634376838689/R0aYmMIDI.jpeg)

ผมคิดว่าเป็นตัวอย่างที่น่าสนใจในการนำเสนอมุมมองจากข้อมูล ที่มีโอกาสให้ชวนคิดไปในแง่ที่จริงๆ แล้วระบบเค้าอาจจะไม่ได้แย่ขนาดนั้นซะทีเดียว ซึ่งจากรูป ดูแล้วเป็นการเรียงลำดับจำนวนครั้งที่ระบบล่มจากมากไปน้อย และตัวเลขจำนวนครั้งที่ล่มก็ดูจะเป็นจุดสนใจกับคนที่มาอ่านข่าว

ถ้าเราเอาจำนวนครั้งที่ล่มอย่างเดียวมาลองวาดกราฟเล่นๆ ดู จะได้เปรียบเทียบกันง่ายมากขึ้น (บทความนี้จะขอเลือกเฉพาะ Mobile Banking มาชวนคุยกันนะครับ)

![Screen Shot 2564-10-16 at 20.59.55.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1634392799041/s6yjchFPA.png)

จะเห็นว่ามีอยู่ 2 ธนาคาร (SCB กับ ttb) ที่มีจำนวนครั้งที่ล่มสูงที่สุดในรอบครึ่งปี 64 และอีก 4 ธนาคารมีจำนวนครั้งที่ล่มเพียงแค่ 1 ครั้งเท่านั้น.. ถึงตรงนี้แล้วเราสามารถตอบได้เลยไหมว่า ระบบของธนาคาร 4 ธนาคารนั้นทำได้ดีกว่าธนาคาร 2 ธนาคารแรกหรือไม่?

คำตอบของผมคือ "ก็อาจจะเป็นไปได้" แต่จะให้ฟันธงเลยจริงๆ คงไม่ได้ครับ ในแง่การวิเคราะห์ข้อมูลนั้น สิ่งที่อันตรายมากที่สุดคือ การมองข้อมูลเพียงมุมเดียว ดังนั้นเราควรหาข้อมูลอื่นมาเสริมด้วย

OK! ทีนี้ถ้าเราเอาจำนวน ชม. ที่ล่มรวม มาด้วยล่ะ? กราฟที่ได้ก็จะประมาณนี้

![Screen Shot 2564-10-16 at 21.00.12.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1634392816961/nOpPtsLuS.png)

เนื่องจากของธนาคารกสิกรไทยเค้าไม่ได้เจาะจงตัวเลข ชม. มา ผมขอตั้งเป็น 0.7 ชม. นะครับ เป็นตัวเลขที่ผมสุ่มขึ้นมานะ

ทีนี้จากกราฟจะเห็นได้ว่า ธนาคารกรุงศรีล่มนานที่สุดคือ 11 ชม. และที่น้อยที่สุดคือธนาคารกสิกรไทย ถึงตรงนี้มีสิ่งที่น่าสนใจเกิดขึ้นครับ คือจากกราฟแรก ธนาคารที่มีจำนวนครั้งที่ล่มน้อยๆ เริ่มกลับมาอยู่ด้านหน้าแหละ ซึ่งก็เป็นการยืนยันได้ในระดับหนึ่งว่า การที่เราดูจำนวนครั้งที่ระบบล่ม ไม่น่าจะเพียงพอในการที่เราจะบอกว่าระบบของธนาคารนั้นๆ ดีแค่ไหน เราควรเอาปัจจัยอื่น อย่างเช่น เวลาล่มรวม เข้ามาด้วย

จากข้อมูล 2 อย่างนี้ เราจะเทียบได้อย่างไรว่าระบบของธนาคารไหนทำได้ดีที่สุด?

ถึงตรงนี้แล้วเราอาจจะต้องมาดูข้อมูลในมุมมองด้านอื่นเพิ่ม อย่างเช่น มุมมองของการกู้ระบบกลับมาให้ทำงานเหมือนเดิม เป็นต้น ซึ่งจากข้อมูลแล้วเราสามารถวิเคราะห์ได้เบื้องต้น คือ เราอาจจะดูว่าการที่ระบบล่มในแต่ละครั้งโดยเฉลี่ยแล้ว เค้าล่มเป็นเวลานานเท่าไหร่?

ผมลองคำนวณง่ายๆ ครั้ง คือเอาเวลาที่ล่มโดยรวม มาหารด้วย จำนวนครั้งที่ล่ม จะได้กราฟมาตามนี้

![Screen Shot 2564-10-16 at 21.00.33.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1634392836773/zXcwDN8Rr.png)

เห็น Surprise อะไรไหมครับ? 🙂 บางทีการที่ระบบล่มหลายครั้ง ก็ไม่ใช่ว่าระบบจะแย่เสมอไปถ้าเค้ามีความสามารถในการกู้คืนระบบกลับมาได้เร็ว

ถ้าพูดจากข้อมูลทั้ง 3 มุมมองนี้ ระบบธนาคารไหนทำได้ดี เค้าก็จะเกาะกลุ่มท้ายๆ ของข้อมูลทั้ง 3 มุมมองนี้ ส่วนธนาคารไหนที่ดูสลับไปสลับมาระหว่างกลุ่มต้น กับ กลุ่มท้าย ก็อาจจะต้องมาดูเพิ่มเติมว่าเค้าควรจะปรับอะไรให้ดีขึ้นบ้าง

### ทิ้งท้าย

สุดท้ายสิ่งที่อยากจะสื่อในบทความนี้ก็คือว่า เวลาที่เราวิเคราะห์ข้อมูล เราควรมองจากหลายๆ มุมครับ มันจะอันตรายมาก ถ้าเรามองแค่ไม่กี่มุม แล้วตัดสินใจจากจุดนั้น

สิ่งที่เราควรทำคือ หาข้อมูลในมุมอื่นมาเสริม เก็บข้อมูลเพิ่ม ทดสอบสมมุติฐานของเราเรื่อยๆ เปิดรับมุมมองใหม่ๆ อยู่เสมอ ทั้งนี้ทั้งนั้นก็เพื่อให้การวิเคราะห์ข้อมูลของเราแน่นขึ้น และน่าเชื่อถือมากขึ้นด้วยครับ 

ปล. ถ้าถามผมว่าในกรณีธนาคารนี้ แค่ 3 มุมมองนี้พอไหมในการวิเคราะห์? ตอบได้เลยว่า ไม่พอครับ ต่างธนาคาร ต่างบริบท ถ้าจะเทียบกันจริงๆ น่าจะมีมุมมองอีกเป็น 100 ให้เอามาคิดเพิ่ม 😎