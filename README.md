## AWS Elastic Block Store (EBS)

📌 Overview
- Amazon Elastic Block Store (EBS) is a block-level storage service designed for use with Amazon EC2 instances.
- It provides persistent storage, ensuring that data remains intact even when an EC2 instance is stopped or restarted.
---
## 🧠 Simple Explanation
- EBS is a virtual hard disk for EC2 instances.
- Just like a physical HDD or SSD is used in a computer, an EBS volume is used as storage for an EC2 instance.
---

## 🔑 Key Features
- Persistent block-level storage
- High availability and durability
- Attach and detach volumes from EC2 instances
- Snapshot support for backup and recovery
- Data encryption supported
- Multiple volume types based on performance requirements
---

## ⚙️ EBS Configuration (Step-by-Step)
- 📝 Prerequisites
- An EC2 instance must already be running
- The EBS volume and EC2 instance must be in the same Availability Zone
---

## Step 1️⃣: Create an EBS Volume
- Log in to the AWS Management Console
- Navigate to EC2 → Volumes
- Click Create volume
- Configure the following:
- Volume type: gp3 (recommended)
- Size: 8 GiB (or as required)
- Availability Zone: Same as the EC2 instance
- Click Create volume

## 🔍 Verify EBS Volume Attachment
- Go to EC2 → Instances
- Select your instance (e.g., mywebserver)
- Open the Storage tab
- Check attached volumes:
- Root volume (e.g., /dev/xvda)
- Additional volume (e.g., /dev/xvdf or /dev/sdc)
- Status should be Attached
- From the Linux terminal, verify using:
```
lsblk
```
---

## 📌 Note
- If the volume is not visible:
- Ensure the Availability Zone matches
- Confirm the volume is attached to the correct instance
---

## ✏️ Modify EBS Volume Size
- To increase or modify an existing EBS volume:
- Go to EC2 → Volumes
- Select the target volume
- Click Actions → Modify volume
- Update:
- Volume size (e.g., 8 GiB → 20 GiB)
- Or volume type (e.g., gp2 → gp3)
- Click:- Modify
- Confirm the changes
---

## Important Notes
- Volume size can only be increased, not decreased
- File system resizing is required at the OS level after modification
- Volumes can be modified while the EC2 instance is running
---

## 🗑️ Detach and Delete an EBS Volume
- Step 1️⃣: Stop the EC2 Instance (Recommended)
- Navigate to EC2 → Instances
- Select the instance
- Click Instance state → Stop
- Wait until the instance status is Stopped
- Stopping the instance helps prevent data corruption.
---

## Step 2️⃣: Detach the Volume
- Go to EC2 → Volumes
- Select the EBS volume
- Click Actions → Detach volume
- Confirm and wait until the volume status becomes Available

## Step 3️⃣: Delete the Volume
- Select the detached volume
- Click Actions → Delete volume
- Type delete to confirm
- Click Delete
 
 - ⚠️ Warning:
Deleted EBS volumes cannot be recovered. Always create a snapshot before deletion if backup is required.
---

## ▶️ Start EC2 Instance and Attach Volume (Optional)
- Step 1️⃣: Attach an EBS Volume
- Go to EC2 → Volumes
- Select the volume
- Click Actions → Attach volume
- Choose the EC2 instance
- Specify device name (e.g., /dev/xvdf)
- Click Attach

## Step 2️⃣: Start the EC2 Instance
- Navigate to EC2 → Instances
- Select the instance
- Click Instance state → Start
- Wait until the instance status becomes Running
---

## 👨‍💻 Author

Kumlesh Kurre
💼 IT Support & Network Engineer

⭐ If you find this guide useful, please star the repository.
