# สรุปความรู้
## -Digital
คือการนำสัญญาณไฟฟ้ามาในคอมพิวเตอร์แทนด้วยเลขฐาน 2 คือ 0 และ 1
## -voltage
คือความต่างศักย์ระหว่างจุด 2 จุดแบ่งเป็น 2 ประเภทคือ แรงดันไฟฟ้ากระแสตรงและแรงดันไฟฟ้ากระแสสลับ
## -computer
ในอดีตคอมพิวเตอร์มีขนาดใหญ่และประมวลผลช้า เวลาผ่านมาจวบจนปัจจุบันนั้นมีขนาดเล็กลงมากและประมวลผลเร็วมากเช่นกัน รวมถึงมีการใช้คอมพิวเตอร์ตัวจิ๋วในการใช้งาน IOT
## -internet
เป็นตัวเชื่อมโยงทุกๆอย่างเข้าด้วยกัน ทั้งอุปกรณ์มีสายและอุปกรณ์ไร้สาย
## -program language
การพัฒนาโปรแกรมให้ผู้ใช้งานง่ายต่อการเข้าใจและการใช้ มีการพัฒนาจากภาษาc แต่ปัจจุบันมีความหลากหลายมากกว่านั้้นเช่น python
## -platformio
เป็นแหล่งข้อมูลแบบเปิดที่ทุกคนสามารถพัฒนาได้ สามารถนำมาใช้กับอุปกรณ์ IOT โดยใช้กับ micro controller

# การทดลอง
## -01 run example 1
เขียนcodeลงบน micro controller โดยcodeประกอบไปด้วย set up และ loopเพื่อนับค่าตัวแปรโดยหน่วงเวล่ 1 วินาที และทำการโหลดโดยการกดปุ่มload ตามด้วย reset
## -02 run example 2
โหลดโปรแกรมสแกนหาสัญญาณ wifi รอบๆตัวเองเข้าสู่ micro controller
## -03 run example 3
นำโปรแกรมที่เขียนไว้ใน run example 2 มาใช้งานผ่าน relay โดยสั่งเปิด-ปิดผ่านสัญญาณดิจิตอล เมื่อจ่ายไฟเลี้ยงให้ relay และ micro controller จะทำการเปิด-ปิดตามโปรแกรมที่ตั้งไว้
## -04 run example 4
เป็นการนำสัญญาณ input จากภายนอก โดยให้ Port0 เป็น input Port2 เป็น Output โดยสัญญาณ Input จาก Port0 จะเป็นตัวควบคุม Output Input เป็น 0 หลอดไฟจะสว่าง Input เป็น 1 หลอดไฟจะดับ เมื่อนำไปต่อกับเซนเซอร์แสง โดยต่อเซนเซอร์เข้าไปที่ Port0 เมื่อมีแสงจะเป็น 0 มืดจะเป็น 1 เมื่อมีแสงไฟจึงสว่าง เมื่อบังแสงไฟจึงดับ
## -05 run example 5
สร้าง web server ผ่าน wifi โดยการใส่ SSID และ password สามารถทดสอบได้โดยใช้ web browser
## -06 run example 6
สร้าง wifi access point ขึ้นมาโดยกำหนด SSID และ Password และต้องกำหนด IP gateway + subnet ขึ้นมาแล้วอัพโหลด สามารถทดสอบด้วยโทรศัพท์หรือคอมพิวเตอร์

# โปรแกรมแสดงตัวอักษรบน OUTPUT

1.ในขั้นแรกคือระบบจะเรียกค่า address0000 มาเรียงใหม่แบบ word ถัดมาคือดูว่าในนั้นมีคำสั่งให้ทำอะไรจากนั้นนำค่า x0และ20 รวมกันแล้วนำมาแทนค่าที่x1เดิม

2.จาก address0004 คำสั่งคือเอา c0000 มาแค่20ิbite แล้วก็เอา address0040 มาเรียงแบบ word จากนั้นคำสั่งบอกว่าให้โหลด c0000 ลงไปแทนใน x2

3.คำสั่งคือโหลดค่าจาก x1 มา 1 bite นำมาใส่ใน x3 แล้วเอา address0008 มาเรียงแบบ word เหมือนเดิม จากนั้นโหลด x1 ไปยัง x3 

4.ขั้นตอนนี้เช็คว่า x0 เท่่ากับ x3 หรือไม่ ถ้าไม่เท่าให้ไปต่อ

5.ต่อมานำค่า x3 ไปแทนใน x2 จากนั้นนำค่า x3 ไปแสดงปลยังหน้่จอแสดงผลซึ่งจะเป็นอักษรตัว V

6.จากนั้นjump x1+1 ไปแทนใน x1 แล้วก็ย้อนกลับไปที่ address0008 อีกครั้ง

7.จากนั้นวนลูปใหม่กับ 4a เช่นเดิมจากข้อที่3 จะได้ว่าผลที่แสดงบนหน้าจอคือ VJ
