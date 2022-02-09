# ชื่อ นายชินภัทร คล้ายบรรจง รหัส 6310680514 
วันนี้จะมาสรุปหัวข้อต่างๆ อาทิ เช่น markdown,เนื้อหา Microcontroller และ สรุปการทดลอง ESP-01

# MARKDOWN
ในการสร้างหัวเรื่อง ให้พิมสัญลักษณ์ # และถ้ามีหัวเรื่องย่อยอีก ก็พิมเป็น ## มีหัวข้อย่อยอีกก็สามารถเพิ่มตัว # ได้เรื่อยๆครับ

การเขียนตัวหนา ทำได้โดยกดคีย์ลัด ctrl+B และ การเขียนตัวเอียง ทำได้โดยการกด ctrl+I และสามารถอ้างข้อความได้โดยการพิมเครื่องหมาย ( > )
> การอ้างข้อความโดยการกดเครื่องหมาย ( > ) จะแสดงลักษณะประมาณนี้ครับ

เราสามารถ list รายการที่ต้องการจะพิม โดยการพิม ( - ) หรือ ( * ) ได้เลยครับ
- จะแสดงเป็นแบบประมาณนี้ครับ  

เราสามารถแทรกรูปภาพได้ด้วยครับ

# สรุปเนื้อหาเกี่ยวกับ Microcontroller ESP-01
1. digital เกิดจากสัญญาณไฟฟ้าซึ่งจะเขียนด้วยเลขฐาน 2 จะแสดงแค่เลข 0 กับ 1 เท่านั้น จะขึ้นอยุ่กับแรงดัน
2. voltage คือ ความต่างศักย์ไฟฟ้าระหว่างจุดสองจุด มี 2 ประเภท คือ กระแสสลับ ซึงเป็นไฟบ้าน และ แรงดันกระแสตรง ที่มีขั้วบวกขั้วลบ เช่น แบตเตอรี่
3. computer มีวิวัฒนาการมานานมาก มีความเร็วสูง มีความจุ สามารถเชื่อมโยงผ่านอินเตอร์เน็ตได้
4. internet ทำให้ทุกสิ่งสามารถเชื่อมโยงกันได้ 
5. program lang การพัฒนาโดยการเขียนซอฟแวร์ให้รันบนคอมพิวเตอร์ 
6. platformio คือ การพัฒนาซอฟแวร์มาตรฐานแบบเปิด โดยเขียนลงใน microcontroller ได้หลายแบบ และ ชิพที่ใช้สามารถพัฒนาได้หลายชิพ

# สรุปการทดลองบน ESP-01 จำนวน 6 การทดลอง
## run example 1
เราจะเขียนโปรแกรมเข้าไปใน microcontroller เมื่อนำโปรแรมเข้าไปแล้ว จะมี 2 ส่วนหลักๆคือ setup และ loop โดย loop เราจะตั้งค่าให้หน่วงทุกๆ 1 วินาที โดยจะใช้ platformio และ upload program ไปใน microcontroller ต้องกดปุ้มที่ตัวเครื่องด้วย และรอโหลด เมื่อโหลดเสร็จแล้วโปรแกรมจะพร้อมรัน ให้เราใช้คำสั่ง pio device monitor ตัวแปร count จะนับเพิ่มทีละ 1 ทุก 1 วินาที และถ้าเรากดปุ้ม reset บน microcontroller ก็จะ reset และเริ่มนับ 1 ใหม่ 
## run example 2 
หลังจากเสียบแล้ว upload preogram แล้ว จะมี2ส่วนคือ ส่วน setup wifi และส่วน loop และเมื่อ upload ครบ 100 % แล้วใช่คำสั่ง pio device monitor แล้วก็จะขึ้น wifi ที่เจอ
## run example 3
มี output port และ input port เมื่อเขียนโปรแกรมใน microcontroller แล้วนำไปเสียบกับ USB และจะนำ io port ที่มี port 0 กับ port 1 มาใช้งานด้วย จะเสียบผ่าน adapter และจะทำให้ output ออกมาที่ port 0 และจะวน loop 0.5 วินาที แล้วเพิ่มจำนวนรอบคี่ให้เป็น on และคู่เป็น off แล้ว LED เมื่อเปล่งแสงออกมาจะเป็น on
## run relay 
จะนำ mitrocontroller ที่เขียนโปรแกรมไว้แล้ว เสียบเข้ากับ relay เพื่อเปิดและปิดสวิตซ์ จะควบคุมการเปิดปิดทุกๆ 0.5 วินาที
## run example 4
การนำสัญญาณ input จากภายนอกเข้ามาใน microcontroller โดนจะ set ให้ port 0 เป็น input และ port 2 เป็น output โปรแกรมจะวนลูปและอ่านข้อมูลจาก port 0 อ่านเป็นสัญญาณ digital ถ้าเป็น 1 ให้ส่งไปยัง port 2 ทำให้ไฟดับ เพราะฉนั้นสัญญาณ input จาก port 0 จะเป็นตัวควบคุมให้ไฟเปิดหรือปิด
## run wifi
การสร้าง web server ผ่าน wifi เราต้องใส่ชื่อ wifi กับ password ลงไป หลังจากนั้นโปรแกรมก้จะมี 2 ส่วนคือ setup และ loop การ setup จะเป็นการ connect กับ wifi ที่เลือกไว้ หลังจากนั้นก็ setup web server และเราจะ upload โปรแกรมขึ้นไปบน microcontroller โดยการเสียบไปที่ USB เราจะใช้ wed browser ในการทดสอบโปรแกรม
## run wiri AP
เป็นโปรแกรมที่ใช่ wifi โดยจะสร้าง wifi ขึ้นมาเอง เราต้องกำหนดชื่อ และ password ด้วย และให้คนมาเชื่อมต่อ โดยกำหนด gate way และเตรียม wed server ด้วย โดยกำหนด password และ IP เมื่ออัพโหลดโปรแกรม ต่อมาก็จะ run โปรแกรม เมื่ออัพโหลดเสร็จก็สร้าง wifi access point ขึ้นมา และจะทดสอบโดยใช้คอมพิวเตอร์ หรือโทรศัพท์มือถือในการเช็คว่า wifi ตัวนั้นมีหรือไม่ ถ้าพบว่ามีเราก็สามารถที่จะเชื่อมต่อได้เลย
