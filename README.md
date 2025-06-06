# U-net.

U-net เป็นการทำ image segmentation คือเป้าหมายหลักๆคือหา object ที่ต้องการจากในรูปเเล้วเจาะเอาในระดับ pixel
มันเริ่มมาจากเปเอร์ https://arxiv.org/abs/1505.04597
![image](https://github.com/user-attachments/assets/8c7e49a2-c542-4fba-b2ec-ae92cbcdb6f0)

จะมี 3 ส่วนหลักๆ Encoder- Bottle Neck - Decoder 
ตัว method ที่จะใช้ทำ feature extraction คือตัว Double Conv ผสมกับการทำ skip connection ระหว่างภาพจาก Encoder ไปใช้ร่วมกับภาพในขั้ตอน decoder

![image](https://github.com/user-attachments/assets/0de0d859-87bb-4d48-bc48-a7c9a404e4dc)

ในส่วน Encoder
- ทำ Double Conv เเล้ว Maxpool ทำให้ compress รุปลงไปเรื่อยๆ

ในส่วน Bottle Neck
- ทำ Double Conv เเต่ไม่ max pool

ในส่วน Decoder
- จะ transposed convolution ทำให้ image ใหญ้ขึ้น + ในชั้นเดียวกันจะใช้ skip connection เอาภาพจาก encoder ในชั้นเดียวกันมาช่วยทำด้วยเพราะหลังผ่าน encoder- bottle neck มาอาจทำให้มีบาง detail จาก feature ดั้งเดิมหลุดไปเลยจะเอาตรงนี้มาช่วยทำด้วย

