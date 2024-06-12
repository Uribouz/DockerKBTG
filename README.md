# DevOps learning sessions

## Docker Workshop Code-snippet
- Day1: https://eji4h.notion.site/Day1-0b3b6693d7b94ab6a9fafde069f9806a
- Day2: https://eji4h.notion.site/Day2-b12648dd782f4589947ec61ef0001e75

### Docker Security
#### 1. Attack: Privilege Escalation
- Using user 'root' in dockerContainer to have an access to the host's kernel
- Preventive: must run docker as nonroot user

#### 2. Attack: Surface Attack
- A fairly new attack surface that was introduced with containers is the use of public images (cloud
container registry).
- Two of the most popular public image registries are Docker Hub and Quay and while it’s great that they provide publicly accessible images, you have to make sure that these images were not modified to include malicious software.
- Preventive: check tags of the image first before using: https://hub.docker.com/_/ubuntu/tags

#### 3. Secure Conatiner
##### Distroless image (google)
- Type of image that restricted user that can only "run the application"
- Contains only Application Runtime (if required) and Application (executable file) and it does not
provide any OS packages even shell commands.
#### UBI Micro Image (Red Hat)
- Reduce the attack surface of Linux containers
(FROM registry.access.redhat.com/ubi9/ubi-micro:9.2-15)


### Buildx

#### 1) Prepare docker environment to run 'buildx'
```bash
$ docker buildx create --use
```

#### 2) run multi platform build using following command.
```bash
$ docker buildx build --platform=linux/amd64,linux/arm64,linux/arm/v7 -t <image_name> .
```

### Images type

#### Debian Releases (-bookworm/-bullseye/-buster):

● Image that have -bookworm/ -bullseye/-buster/-stretch extension. Images tagged are codenames for different Debian releases:
    ○ bookworm: the stable Debian release is 12
    ○ bullseye: all version 11 variations
    ○ buster: all version 10 variations, under LTS support
    ○ stretch: all version 9 variations, extended LTS support
Example:
    ● python:3.11.5-bookworm
    ● python:3.11.5-bullseye

Slim (-slim):
    ● The slim image is a paired down version of the full image.
    ● This image generally only installs the minimal packages needed to run your particular tool.
Example:
    ● python:3.11.5-slim-bookworm
    ● python:3.11.5-slim-bullseye

#### Alpine (-alpine):
● Alpine images are based on the Alpine Linux Project, which is an operating system that was built specifically for use inside of containers.
● Alpine Linux is built around musl libc and busybox. This makes it small and very resource efficient.
● A container requires no more than 8 MB and a minimal installation to disk requires around 130 MB of
storage.
Example:
    ● python:3.11.5-alpine, python:3.11.5-alpine3.18
    ● python:3.11.5-alpine3.17


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


### 6) ในการทำ Dockerfile ใช้ประโยชน์จาก Layer Caching 
เช่น ถ้าเรารู้ว่า package* จะไม่ค่อยเปลี่ยนแปลง เราจึง Copy แค่ package* ไปก่อน
แล้วค่อย COPY code ของเราส่วนที่เหลือไป จะได้ลดเวลาในการ build image ให้ได้เร็วขึ้น

```Dockerfile
ROM node:20.9-slim AS build
WORKDIR /app
COPY package* ./
RUN npm i
COPY . .
RUN npm run build
```

### 7) OSI model
ALB = Application Load Balancer
- Layer 7: Application Layer
NLB = Network Load Balancer
- Layer 4: Transport Layer
F5: Prevent DDOS attack at Hardware level
- Layer 2: DataLink Layer


### Tip & Tricks in dockerfile
#### Avoid mistake
● Running apt-get
● Using ADD instead of COPY
● Adding your entire application directory in one line
● Using :latest
● Using external services during the build
● Adding EXPOSE and ENV at the top of your Dockerfile
● Multiple services running in the same container
● Build images for every environment

#### Best practices
● ENTRYPOINT exec form
● Understand how CMD and ENTRYPOINT interact
● Docker ignore
● Use multi-stage builds
● Leverage build cache

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
#### 8) Linux distribution timeline:
- https://upload.wikimedia.org/wikipedia/commons/1/1b/Linux_Distribution_Timeline.svg
#### 9) Docker Security Cheat sheet:
- https://cheatsheetseries.owasp.org/cheatsheets/Docker_Security_Cheat_Sheet.html
#### 10) Team topologies: How to build team
- https://teamtopologies.com/
#### 11) Domain-Driven Design
#### 12) Software Architecture
#### 13) Handling multiple env when using Docker Compose
- https://levelup.gitconnected.com/handling-multiple-environments-in-react-with-docker-543762989783
#### 14) Coding Standard for team: Using commitizen
- https://commitizen-tools.github.io/commitizen/
#### 15) ARGO-CD: GitOps continuous delivery tool for Kubernetes.
- https://argo-cd.readthedocs.io/en/stable/
#### 16) GIT CICD
- https://github.com/docker/setup-buildx-action
- https://docs.gitlab.com/ee/ci/