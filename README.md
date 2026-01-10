# AWS EBS (Elastic Block Store)

## 📌 Definition
**AWS Elastic Block Store (EBS)** ek block-level storage service hai jo **Amazon EC2 instances** ke saath use hoti hai.  
Ye EC2 ke liye **persistent storage** provide karti hai, jisme data instance stop ya restart hone ke baad bhi safe rehta hai.

---

## 🧠 Simple Explanation
> **EBS = EC2 ke liye virtual hard disk**

Jaise computer me HDD/SSD hoti hai,  
waise hi EC2 instance ke liye EBS volume hota hai.

---

## 🔑 Key Features
- Persistent storage
- High availability & durability
- EC2 ke saath attach/detach support
- Snapshot (backup) support
- Encryption supported
- Different performance-based volume types

---

## ⚙️ Configure AWS EBS (Step-by-Step)

### 📝 Notes
- Is guide me maana gaya hai ki **EC2 web server instance pehle se bana hua hai**.  
  Agar aapke case me EC2 instance create nahi hai, to pehle EC2 instance create kar lijiye.
- **EC2 instance aur EBS volume ka Availability Zone same hona chahiye**, warna volume attach nahi hoga.

---

### Step 1️⃣: Create EBS Volume
1. AWS Console me login karein
2. **EC2 → Volumes** par jaayein
3. **Create volume** par click karein
4. Neeche diye gaye options select karein:
   - Volume type: `gp3` (recommended)
   - Size: `8 GiB` (ya requirement ke hisaab se)
   - Availability Zone: **EC2 instance ke same zone me**
5. **Create volume** par click karein

---

### 🔍 How to Check EBS Volume Attached or Not

1. AWS Console me **EC2 → Instances** par jaayein
2. Apni instance select karein (example: `mywebserver`)
3. Neeche **Storage** tab par click karein
4. Yahan aapko attached volumes dikhai denge, jaise:
   - Root volume: `/dev/xvda`
   - Additional EBS volume: `/dev/xvdf` ya `/dev/sdc`
5. Agar volume ke saamne **Attached** status dikh raha hai,  
   to iska matlab EBS volume successfully attach ho chuka hai.
6. open linux terminal and type this command
   ```lsblk``` showing disk.
---

### 📌 Note
- Agar additional volume **Storage** section me nahi dikh raha hai,  
  to ensure karein ki:
  - Volume aur EC2 instance **same Availability Zone** me hain
  - Aapne sahi instance select ki hai
---
## ✏️ Modify EBS Volume Size

Agar aapko existing EBS volume ka size badhana ya change karna hai, to neeche diye gaye steps follow karein:

1. AWS Console me **EC2 → Volumes** par jaayein
2. Jis **EBS volume** ka size modify karna hai, use select karein
3. **Actions → Modify volume** par click karein
4. Apni requirement ke according:
   - Volume size increase karein (example: 8 GiB → 20 GiB)
   - Ya volume type change karein (gp2 → gp3)
5. **Modify** par click karein
6. Confirmation ke liye **Yes** par click karein

---

### 📌 Important Notes
- EBS volume ka **size sirf increase** kiya ja sakta hai, decrease nahi
- Volume modify hone ke baad:
  - Linux me partition aur file system resize karna padta hai
- Running EC2 instance ke saath bhi volume modify ho sakta hai
---

## 👨‍💻 Author

  Kumlesh Kurre
💼 IT Support & Network Engineer

⭐ If you find this guide helpful, don’t forget to star ⭐ the GitHub repository
