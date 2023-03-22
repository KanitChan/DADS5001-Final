# DADS5001-Final
IMDb Insight

Dataset Information
•	Data from https://github.com/yash91sharma/IMDB-Movie-Dataset-Analysis/blob/master/movie_metadata.csv 
•	Data เกี่ยวกับ ข้อมูลที่เกี่ยวข้อง ใน website IMDb
•	IMDb คือ  เป็นฐานข้อมูลออนไลน์รวบรวมเกี่ยวกับเรื่องราวของ นักแสดง ผู้กำกับ และบุคคลที่เกี่ยวข้องในวงการภาพยนตร์ และยังเป็นคอมมูนิตี้สำหรับคนดูหนัง เปิดให้คนจากทั่วโลกเข้ามาให้คะแนนหนังที่ดูจบไปแล้ว รวมทั้งร่วมวิจารณ์บนเว็บไซต์ได้เลย ถือเป็นเว็บไซต์หนังที่ได้รับความนิยมทั่วโลก เราจึงมักจะใช้คะแนนจากนักรีวิวบน IMDb มาเป็นตัวเลขอ้างอิงว่าหนังเรื่องดังกล่าวถูกจริตผู้คนทั่วโลกอย่างไร
•	คะแนนของ IMDb มาจากไหนบ้าง?
คะแนนของหนัง (imdb_score) จะมาจากการ่วมโหวตของคนทั่วโลกที่ เพียงสมัครสมาชิกบนเว็บไซต์ ก็เข้าไปกดโหวตได้ทันที คะแนนจะมีตั้งแต่ 1-10

DATA Processing
Cleansing data
•	Cleansing data โดยการดูข้อมูลที่มี rows data เป็น nan จากการหา จำนวน nan มาวัดเป็น percent และ drop rows ที่เป็นหัวข้อของข้อมูล percent missing value สูงมากกว่า 7.5 % จึง ดรอปข้อมูล 'Gross' และ 'budget' เนื่องจาก percent สูง และต้องการใช้งานทั้ง 2 ตัวแปรนี้ ผลลัพธ์ที่ได้ บาง rows ที่ถูกลบออกไปเป็น rows ที่มีค่า nan หายไปจำนวนมากอยู่แล้วทำให้ผลกระทบ percent ของตัวอื่นน้อยลงไปด้วย
•	แล้วโชว์กราฟอีกรอบว่าอะไรหายไปบ้าง ซึ่งคราวนี้ %missing values จะมีค่าน้อยลง จนถึงขั้นที่ accceptable จึงใช้ข้อมูลนี้ต่อ
 
Correct data
•	มาตรวจสอบข้อมูล ว่าข้อมูลส่วนไหนจำเป็นต่อการใช้งานของเราบ้าง และนำข้อมูลมาตรวจสอบจะเจอว่าข้อมูล country ไม่ถูกต้อง >> จึงทำการแก้ไขให้ถูกต้อง


OBJECTIVE: Use information from the dataset to answer the following question
1.	Industry Growth (จำนวนหนังที่เพิ่มขึ้นสูงในแต่ละปี ทำให้มีรายได้รวมที่เพิ่มขึ้นในทุกๆปี แต่จริงหรือไม่ที่การเติบโตเฉลี่ยนั้นเพิ่มขึ้นตาม >> ถ้าไม่เพราะอะไร)

จากกราฟ 1.1) จะเห็นว่ากราฟค่ารวมรายได้ของหนังต่อปี มีรายได้ที่เพิ่มขึ้นเรื่อยๆต่อปีอย่างมาก แต่กลับกัน พอมาดูกราฟ 1.2) ที่เป็นค่าเฉลี่ยรายได้ต่อปี กลับพบว่าไม่ได้มีค่าสูงขึ้นแต่อย่างใด ซึ่งสาเหตุนั้นมาจากในแต่ละปีนั้นก็มีจำนวนหนังที่เพิ่มสูง (คู่แข่งจำนวนมากขึ้น)ซึ่งทำให้มีการแบ่ง market share ออกไปด้วยเช่นกัน
 
กราฟ 1.1)
 
						กราฟ 1.2)

2.	Budget vs Gross (USA) >> หนังที่มีต้นทุนสูง จะมีรายได้สูงตาม จริงหรือไม่?

จากกราฟ 2.1) พบว่าหนังที่มีต้นทุนสูง นั้นจะส่งผลให้มี รายได้ที่เพิ่มสูงตาม และมีแนวโน้มเป็นความสัมพันธ์แบบแปรผันตรงเชิงบวก
 
						กราฟ 2.1)

แต่กลับกัน การที่มีต้นทุนในการทำหนังที่สูง มีแนวโน้มส่งผลให้มี imdb_score ที่สูง แต่หนังที่มีต้นทุนในการทำหนังที่ต่ำ ไม่ได้หมายความว่าจะมี imdb_score ที่ต่ำเสมอไป ดังกราฟ 2.2) scatter plot ด้านล่าง


						กราฟ 2.2)

3.	หนังที่มี imdb_score สูง นั้นจะทำให้มีรายได้สูงเสมอหรือไม่?  

จากกราฟ 3.1) พบว่า imdb_score ที่มีค่าต่ำนั้นทำให้มีรายได้อยู่ในระดับต่ำอย่างแน่นอน แต่หนังที่มีคะแนน imdb_score ที่สูงนั้นมีโอกาสที่จะมีรายได้ที่สูง หรือต่ำก็ได้ (มีการกระจายในวงที่ค่อนข้างกว้าง)
 
						กราฟ 3.1)


4.	Duration ช่วงไหน ทำให้มี high gross + high imdb_score (ทำแบ่งเป็นกลุ่มเพิ่มๆ short, medium, long)

สรุปได้ว่า ช่วง Long หรือระยะเวลาหนังตั้งแต่ 120 นาทีขึ้นไป (กลุ่ม Long) จะทำให้มี ค่าเฉลี่ย imdb_score และ รายได้ที่สูงกว่าในช่วงกลุ่มอื่น 
หมายเหตุ (ซึ่งตรงนี้ควรได้รับการศึกษาเพิ่มเนื่องจาก perfect duration ของหนังแต่ละ Genres นั้นค่อนข้างแตกต่างกันไป ตามประเภทของหนัง)


 

5.	ทำไมหนังเก่าๆจึงมี imdb_score ที่สูง อะไรเป็นสาเหตุดังกล่าว?

จากกราฟ 5.1) จะเห็นการกระจายของ imdb_score ของในแต่ละปีที่ผลิตหนัง ซึ่งพบว่าในปีเก่าๆนั้นจะมีคะแนน imdb_score มีค่าค่อนข้างสูง เมื่อเทียบกับปีหลังๆ
 
						กราฟ 5.1)


โดยพบว่า หนังที่ผลิตก่อนปี 2000 นั้น ติดอันดับ Top 10 ของทั้งหมด ในสัดส่วน 6 ใน 10

โดยเรื่องที่ติด อันดับ 1 อย่าง The Shawshank Redemtion นั้นครองใจคนดูเป็น Top 1 ตลอดมา

Top 10 before 2000 				Top 10 after 2000


           








6.	Actionable Insight (Produce movie with multiple feature) >>เสนอแนะนำว่าจากข้อมูลที่หามาจะแนะนำ industry อย่างไร
a.	เป็
b.	Should produce with 3 best genres -………….
c.	Should produce 

 

























7.	หนัง Drama มีจำนวนเยอะใน IMDb website จริง แต่ หนัง drama ในแต่ละปีมี รายได้เฉลี่ยสูงตามหรือไม่

กราฟ 7.1) จะพบว่าถึงแม้จำนวนหนัง drama นั้นมีจำนวนมาก ก็จริง แต่รายได้เฉลี่ยของหนัง drama ที่เพิ่ใมขึ้นต่อปีนั้นไม่ได้มีแนวโน้มสูงขึ้นอย่างมีนัยสำคัญตาม
 

















8.	Director vs Gross and Director vs imdb_score Top 10

กราฟดังกล่าวแสดง ชื่อ Director ที่ทำหนังแล้วมีรายได้สูง 10 คนแรก มีรายการดังนี้ (กราฟ 8.1)
นำรายชื่อ Director แต่ละคนที่ทำรายได้สูงสุดมาดูค่า imdb_score ซึ่ง Director ที่ทำหนังได้รายได้สูง ไม่ได้มี imdb_score ที่สูงตามแบบมีความสัมพันธ์กัน แต่ทุกๆคนนั้นมี imdb_score อยู่ในระดับตั้งแต่ 6 ขึ้นไป (กลางค่อนสูง จนถึงสูง)

 



CHALLENGE
•	ข้อมูล dataset นี้เป็นข้อมูลที่ไม่ได้มีข้อมูลครบถึงในปีปัจจุบัน จึงทำให้ไม่ได้เห็นแนวโน้มถึงในปีล่าสุด
•	ข้อมูลไม่ได้มีมุมที่จะนำมาวิเคราะห์หา insight บางทีลอง plot กราฟดูแล้ว อาจจะไม่เจอ insight ที่ต้องการ
•	ในการนำ insight ที่วิเคราะห์มาไปใช้จริง คิดว่าอาจจะต้องมีข้อมูลจากแหล่งอื่นๆมาร่วมวิเคราะห์เพิ่มย
