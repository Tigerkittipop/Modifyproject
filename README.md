# Modifyproject Nodemcu-to-firebase-and-mysql 

การอัพโหลดขอข้อมูลขึ้น firebaseและmysql วันนี้จะมานำเสนอการใช้งาน Module เล็กๆ สีฟ้า DHT11 (DHT11 Humitdity and Temperature Sensor กับบอร์ด Ardiono)ที่ใช้ในการวัดอุณหภูมิกับความชื่นในอากาศกันกครับ

Temperature and Humidity Sensor

ก่อนอื่นมาดู Specification ของ DHT11 กันนะครับว่ามันทำอะไรได้บ้าง
ย่านวัดความชื่น 20-90% RH โดยมีค่าความแม่นยำ +- 5% RH ความละเอียดในการวัด 1 % แสดงผลแบบ 8 บิต ย่านวัดอุณหภูมิ 0 -50 องศาเซลเซียส โดยมีค่าความแม่นยำ +- 2 องศาเซลเซียส ความละเอียดในการวัด 1 องศาเซลเซียส แสดงผลแบบ 8 บิต มิ PIN 4 ขารายละเอียดดังรูปด้านบน กินกระแส 0.5 - 2.5 mA (ขณะทำการวัดค่า) ที่ระดับแรงดัน 3 - 5.5 VDC อ่านค่าสัญญาณ (Sample Rate) ทุก 1 วินาที รายละเอียดของ Spec อื่นๆ นอกเหนือจากนี้ดูในที่ Manual นะครับ

จริงๆแล้ว Sensor วัด อุณหภูมิ กับ ความชื้นใน Series นี้มีออกมาหลายรุ่นครับ เช่น DHT11 DHT 22 DHT21 บางทีมาแต่ตัว sensor บางทีมาเป็น module ความแตกต่างก็คือความแม่นยำในการวัดค่าของ sensor ครับ

ทีนี้มาดูวิธีการต่อใช้งานครับ

<a href="http://www.mx7.com/view2/A2v6md22PxdZfQLa" target="_blank"><img border="0" src="http://www.mx7.com/i/0a4/5pnkIF.png" /></a>



# รูปภาพการวัดค่า SleepMode1

![alt text](https://github.com/Tigerkittipop/Modifyproject/blob/master/Sleep%20Mode1.jpg)


# รูปภาพการวัดค่า SleepMode2

![alt text](https://github.com/Tigerkittipop/Modifyproject/blob/master/Sleep%20Mode2.jpg)


# รูปภาพการวัดค่า SleepMode3

![alt text](https://github.com/Tigerkittipop/Modifyproject/blob/master/Sleep%20Mode3.jpg)
