# Modifyproject Nodemcu-to-firebase-and-mysql 

การอัพโหลดขอข้อมูลขึ้น firebaseและmysql วันนี้จะมานำเสนอการใช้งาน Module เล็กๆ สีฟ้า DHT11 (DHT11 Humitdity and Temperature Sensor กับบอร์ด Ardiono)ที่ใช้ในการวัดอุณหภูมิกับความชื่นในอากาศกันกครับ

# Temperature and Humidity Sensor

ก่อนอื่นมาดู Specification ของ DHT11 กันนะครับว่ามันทำอะไรได้บ้าง
ย่านวัดความชื่น 20-90% RH โดยมีค่าความแม่นยำ +- 5% RH ความละเอียดในการวัด 1 % แสดงผลแบบ 8 บิต ย่านวัดอุณหภูมิ 0 -50 องศาเซลเซียส โดยมีค่าความแม่นยำ +- 2 องศาเซลเซียส ความละเอียดในการวัด 1 องศาเซลเซียส แสดงผลแบบ 8 บิต มิ PIN 4 ขารายละเอียดดังรูปด้านบน กินกระแส 0.5 - 2.5 mA (ขณะทำการวัดค่า) ที่ระดับแรงดัน 3 - 5.5 VDC อ่านค่าสัญญาณ (Sample Rate) ทุก 1 วินาที รายละเอียดของ Spec อื่นๆ นอกเหนือจากนี้ดูในที่ Manual นะครับ

จริงๆแล้ว Sensor วัด อุณหภูมิ กับ ความชื้นใน Series นี้มีออกมาหลายรุ่นครับ เช่น DHT11 DHT 22 DHT21 บางทีมาแต่ตัว sensor บางทีมาเป็น module ความแตกต่างก็คือความแม่นยำในการวัดค่าของ sensor ครับ

ทีนี้มาดูวิธีการต่อใช้งานครับ

<a href="http://www.mx7.com/view2/A2v6md22PxdZfQLa" target="_blank"><img border="0" src="http://www.mx7.com/i/0a4/5pnkIF.png" /></a>

# วิธีการต่อขาของ Nodemcu

<a href="http://www.mx7.com/view2/A2v75Wi1ptvOEn2u" target="_blank"><img border="0" src="http://www.mx7.com/i/05d/GjLehl.gif" /></a>

ในการการต่อวัดแบบปกติ คือ ระยะห่างระหว่าง Sensor กับตัว Arduino ห่างกันไม่เกิน 20 เมตร จะต้องใช้ Pull up resistor ขนาด 5kohm  (ว่าง่ายๆ คือต่อ R 5k ไว้กับแหล่งจ่ายแรงดันและต่อเข้าไปที่ขา DATA ด้วย)  

   Pin 1  ต่อกับ VDD

   Pin 2  ต่อเป็นขา DATA

   Pin 3  ไม่ได้ใช้

   Pin 4  ลงกราวด์

   โดยใช้แหล่งจ่ายแรงดัน VDD ขนาด 3-5.5 VDC ครับ  ซึ่งข้อดีคือจะทำให้ DHT11 นี้สามารถใช้งานได้กับ Arduino หลายรุ่น แต่ในที่นี้เราจะใช่ Arduno NodeMCU ครับ
   
   เมื่อต่อเสร็จแล้วนำโค๊ดที่อัพโหลดให้มาทำการดัดแปลงนิดหน่อย ซึ่งจะมีคำอธิบายไว้ไห้แล้ว
   ผลลัพธ์ของโปรแกรมก็จะแสดงออกมาแบบมี error นิดหน่อยเพราะตัว dht11 ของผมมันไม่ดีครับ
   
   <a href="http://www.mx7.com/view2/A2vdxskCZbuTzqLV" target="_blank"><img border="0" src="http://www.mx7.com/i/0b3/RFn9iF.PNG" /></a>
   
   อย่าลืมเปลี่ยน baud rate นะครับ เพราะใช้ NodeMCU ต้องใช้ baud rate ที่ 115200
   
# วิธีการต่อ NodeMCU ESP8266 แสดงผลออก จอ LCD
 
 ![alt text](https://github.com/Tigerkittipop/Modifyproject/blob/master/all%20pic/2.jpg)
  
  การต่อสาย ขา I2C ของ NodeMCU คือ
      
      - SCL - D1
     
      - SDA - D2
      
  จอ LCD ส่วนมากใช้ไฟ 5V ดังนั้นต้องใช้ไฟ 5V จ่ายให้ คือไฟที่มาจากขา Vin ใน NodeMCU 

  การต่อขา NodeMCU LCD
      - Vin - VCC
      
      - GND - GND
      
      - D1 - SCL
      
      - D2 - SDA
   

# การวัดค่า sleep moded

การวัดค่า sleep mode สายกราว์ อเดบเตอร์ ต่อ GND ของ node mcu สายไฟ+ของ อเดบเตอร์ ไปต่อเข้ากับ สายไฟ+ของมิเตอร์ กราว์ของมิเตอร์ไปเข้า Vinของ mode mcu ถ้าถอดสาย usb ออกไฟจะเลี้ยงไม่พอ

![alt text](https://scontent.fbkk13-1.fna.fbcdn.net/v/t34.0-12/20706422_10203632449488293_139098640_n.jpg?oh=b5ed1e80ffeec47abe8ffda05b8c70f1&oe=598D8EC4)

# วิธีการดักข้อมูลโดยใช้โปรแกรม Wireshark
 
 ![alt text](https://scontent.fbkk13-1.fna.fbcdn.net/v/t34.0-12/20750438_1550147938378235_831784712_n.png?oh=5fd6c19007f14112af1df8bc02907bd5&oe=598C6B6B)

# รูปภาพการวัดค่า SleepMode1

![alt text](https://github.com/Tigerkittipop/Modifyproject/blob/master/all%20pic/Sleep%20Mode2.jpg)


# รูปภาพการวัดค่า SleepMode2

![alt text](https://github.com/Tigerkittipop/Modifyproject/blob/master/all%20pic/Sleep%20Mode2.jpg)


# รูปภาพการวัดค่า SleepMode3

![alt text](https://github.com/Tigerkittipop/Modifyproject/blob/master/all%20pic/Sleep%20Mode3.jpg)


# ความคิดสร้างสรรค์

![alt text](https://scontent.fbkk13-1.fna.fbcdn.net/v/t34.0-12/20706727_1425473977544547_1920847302_n.jpg?oh=89840935ff8a794fa3551d9800ca5c1e&oe=598D67DE)

จากรูป MCU รับค่าแสงที่ ขาA0 และ สั่งให้หลอดไฟติดที่ ขาD5

เมื่อค่าแสงมีค่ามากกว่า500(>500) MCU จะสั่งให้หลอดไฟดับ

และ ถ้าค่าแสงน้อยกว่า500(<500) MCU จะสั่งให้หลอดไฟติด

โดยผ่านวงจรรีเรย์

อุปกรณ์

![alt text](https://i.lnwfile.com/_/i/_raw/iu/c4/2m.jpg)

1. LDR เป็นตัวต้านทานที่ปรับค่าได้ตามความเข้มของแสง LDR เราสามารถใช้ Arduino อ่านค่าความต้านทานที่เปลี่ยนแปลงตามความเข้มของแสงเพื่อนำไปใช้งานที่ต้องการได้ โดยค่าที่อ่านได้เป็นแบบ อะนาล็อก

![alt text](https://o.lnwfile.com/_/o/_raw/o6/n3/ej.jpg)

2. 4-Channel Relay รีเลย์ 4 ตัว เพื่อใช้งานในการควบคุมอุปกรณ์ไฟฟ้า รับกระแสได้สูงถึง 10 A ใช้งานได้ทั้งไฟฟ้ากระแสตรง และ กระแสสลับ รับแรงดันระดับ 5 V ตรงจาก Arduino board มี LED แสดงสถานะการทำงานของรีเลย์ ออกแบบให้ป้องกันวงจรด้านควบคุมออกจากด้านกำลังโดยการใช้การส่งผ่านด้วยแสง (Optocoupler) ในทุกตัวรีเลย์

![alt text](https://cdn.homepro.co.th/catalog/250000/447x447/272523.jpg)

3. หลอดไฟฟ้า หรือ หลอดไฟ เป็นอุปกรณ์ที่ใช้ไฟฟ้าเพื่อทำให้เกิดแสงสว่าง

# สมาชิกกลุ่ม

 ![alt text](https://scontent.fbkk13-1.fna.fbcdn.net/v/t34.0-12/20732888_1636241733085203_2083336209_n.jpg?oh=2c3778602c8d10917b50ae76a2fe71d2&oe=598C5551)
 
 Mr.Kridsada  Wungsan
 
 Mr.Sarawut   Khunyotying
 
 Mr.Pratchaya Mueangmanoi

 Mr.Thanakrit Tasuwan
 
 Mr.Kittipop Tejapromma
 
