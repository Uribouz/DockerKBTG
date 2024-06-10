# DevOps learning sessions

## Key take aways

### 1) Continuous Integration (CI)
- Pre-Commit: verify if the source code is valid before commit and push to the repository.

### 2) Continuous Delivery vs Continuous Deployment (CD)
- Continuous Delivery: manually need approve from Approver before deploy to desired environment..
- Continuous Deployment: automatic deploy to desired environment.

### 3) Health Check
#### 1) Readiness
- check response time เช่นถ้าเกิน 1 วินาที ให้ตัดการเชื่อมต่อตัวนี้ไปใช้ตัวอื่น
#### 2) Liveness

### 4) Cloud vs On-Premise
Cloud ก็คือเครื่อง server On-Premise ที่มีความยิดหยุ่น (Elasticity) ในการรองรับการใช้งานของผู้ใช้ ซึ่งจะมีลักษณะเฉพาะตัวหลากหลายข้อ
 เช่น ต้องสามารถเพิ่มขนาด disk ได้ตามจำนวนข้อมูลที่เพิ่มขึ้น, ต้องรองรับ API request ที่เข้ามาเยอะๆขึ้นได้จาก การใช้งานในช่วง peak time เวลานั้น  

### 5) การ Maximize Developer Effectiveness
ยิ่งเราได้รับรู้ว่าสิ่งที่เราทำ/แก้ไขไปนั้นมีผลลัพธ์เป็นอย่างไรได้เร็วขึ้นเท่าไหร่ เราก็ยิ่งจะสามารถแก้ไขและปรับฯปรุงสิ่งของนั้นๆได้เร็วยิ่งขึ้น
เราควรออกแบบ/ใช้งาน ระบบที่สามารถทำให้เรารับรู้ผลลัพธ์ของงานที่เราทำให้เร็วที่สุด เท่าที่จะเป็นไปได้

#### บทความ Maximize Developer Effectiveness:
- https://martinfowler.com/articles/developer-effectiveness.html?fbclid=IwAR3oiUALWaH1Tu_WL8pJa_iSdtN87mi-mAALg0cJqJld15KaF-mNhm97baQ
#### ลดการ Context Switching:
- https://medium.com/@Adrien_Liard/why-you-should-limit-work-in-progress-and-stop-multitasking-ba7ecd4670f




## Useful URL
#### 1) Contract Testing: 
- https://pact.io/
#### 2) All technology to build a software:
- https://landscape.cncf.io/
#### 3) Site Reliability Engineering (SRE)
- https://www.youtube.com/watch?v=tEylFyxbDLE
#### 4) Hacktoberfest: contribute to open source project.
- https://hacktoberfest.com/
#### 5) Sentry: Tool for monitor logging
- https://sentry.io/welcome/
#### 6) MTTR: Mean time to repair
- https://www.atlassian.com/incident-management/kpis/common-metrics
#### 7) DevSusOps: Develop with sustainability in mind.
- https://www.infoq.com/presentations/devsusops/