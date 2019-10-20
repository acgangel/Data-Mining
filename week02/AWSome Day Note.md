# **AWSome Day Note**
>Time：2019/10/02  
>Location：希爾頓酒店  

=========================================

## **AWS公司沿革與介紹**
* ### 前言
  * Amazon Web Service(AWS) 亞馬遜雲端運算服務
  * 任何公司在做產品研發前都需要謹慎評估
  * 採用模型與MVP圖進行評估

* ### 簡介與架構
  * AWS市佔率為51%
  * AWS雲端運算有三種層級架構
    * Global
    * Region
    * Avaliable Zone(AZ)
  * 一個區域(region)內最少有兩個可用區(avaliable zone), 斷電仍可使用
  * AWS Global Infrastructure，大部分的region已經相連
  * 服務放在region內，服務有分等級：Global/region level/AZ level

* ### [17直播](https://17.live/)
  * Development → Stage → Product
  * Beanstalk(one container per vm)
  * ECS(EC2 Container Service): customized + vm with lambda
  * Cluster Scaling(QPS)
  * EKS(Elastic Kubernetes Service)
  * DMS：Database Migration Service
  * AWS Customer Support  


### **AWS基本服務（計算和服務）**
* ### EC2
  * Resizable compute capacity
  * Complete control of your computing service
  * Save more time & Less investment of hardware
  * Scale capacity could vary according to demand
  * OS：Linux & Windows
  * budget is related to instance type

* ### Amazon Machine Image(AMI)
  * OS透過AMI放進來
  * region/OS/Architecture(32&64bit)/Launch Permission/Storge for root device
  * 計算與儲存的服務費用分開計算
  * AWS Marketplace

* ### EC2 Instance
  * Metadata
  * Instance User Dat

* ### Fargate
* ### Lambda
  * connect your application & AWS service

* ### VPC
  * private, isolated virtue
  * Region>AZ>VPC>[internet gateway]>public subnet
  * Public Subnet/Private Subnet/VPN Subnet


## **AWS儲存服務**
>Storage Service Amazon S3 & EBS


### **S3**
_適合影片、影像等非結構資料/Object_

* ### Facts
  * store unlimited objects
  * High durability and availability
  * HTTPs
Concept: up to 100 buckets, objects are in bucket  
Security: default is private → access policy(json) controlled access

* ### Storge Class
  * Standard: hot data
  * IA: raw data
  * Glacier(磁帶，速度慢): backup, whole data

* ### S3 Object Iife Cycle
  * 進入S3服務下的 Bucket 的 management:Life cycle management→Storge class transition
  * 可設定隨時間推移，自動搬遷資料至降階Storage
  
  
### **EBS(Elastic Block Store)**  
_適合需頻繁變更的資料_

* ### EBS Lifecycle
  * Creat→Attach→Attached and use→Create Snapshot→Dettach→Delete
  * Type Volume (2種4選項)：SSD v.s. HDD

* ### Facts
  * long-term persistence
  * encrypted
  * point-in-time snapshots(快照)
  
* ### Scope
  * EBS volumes are in a single AZ.
  * Volume data is replicated accross multiple servers in an AZ.
  
EBS 為跨AZ；S3為跨Region
EFS
RDS:可用於備份
  
  
  
## **資安、身份、訪問管理**
>由IAM控制存取權限  
>Group/User/Role

* ### IAM Roles
  * 龐大使用者，不想建權限時
  * 暫時性權限，比起永久權限安全
  
* ### IAM Policy
  * IAM restricted policy
  * IAM admin policy→分享暫時性權限給USER(繼承)，給他去執行特別事項，acces他平常不會接觸的資料
  * Role：要填上account ID，允許特定使用者有權利繼承暫時性權限，再於予assign暫時性權限給該特定user
  
* ### Access Type
  * User setting(採用：最小權限原則)
  * Pro
  * AWS console
  
* ### IAM best practice
  * Delete root user
  * 建立 power user 做管理
  * MFA
  * IAM role to those in need
