# 🚢 การสร้างและจัดการระบบแบบ Container Orchestration (Kubernetes)

## 📑 สารบัญ
- [🚢 การสร้างและจัดการระบบแบบ Container Orchestration (Kubernetes)](#-การสร้างและจัดการระบบแบบ-container-orchestration-kubernetes)
  - [📑 สารบัญ](#-สารบัญ)
  - [บทนำ## บทนำ## บทนำ](#บทนำ-บทนำ-บทนำ)
  - [🔰 พื้นฐาน Container และ Kubernetes## 🔰 พื้นฐาน Container และ Kubernetes## 🔰 พื้นฐาน Container และ Kubernetes](#-พื้นฐาน-container-และ-kubernetes--พื้นฐาน-container-และ-kubernetes--พื้นฐาน-container-และ-kubernetes)
    - [Container คืออะไร?### Container คืออะไร?### Container คืออะไร?](#container-คืออะไร-container-คืออะไร-container-คืออะไร)
    - [Kubernetes คืออะไร?### Kubernetes คืออะไร?### Kubernetes คืออะไร?](#kubernetes-คืออะไร-kubernetes-คืออะไร-kubernetes-คืออะไร)
    - [สถาปัตยกรรมของ Kubernetes### สถาปัตยกรรมของ Kubernetes### สถาปัตยกรรมของ Kubernetes](#สถาปัตยกรรมของ-kubernetes-สถาปัตยกรรมของ-kubernetes-สถาปัตยกรรมของ-kubernetes)
      - [แผนภาพสถาปัตยกรรม Kubernetes#### แผนภาพสถาปัตยกรรม Kubernetes#### แผนภาพสถาปัตยกรรม Kubernetes](#แผนภาพสถาปัตยกรรม-kubernetes-แผนภาพสถาปัตยกรรม-kubernetes-แผนภาพสถาปัตยกรรม-kubernetes)
  - [⚙️ การเตรียมสภาพแวดล้อมสำหรับ Windows User## ⚙️ การเตรียมสภาพแวดล้อมสำหรับ Windows User## ⚙️ การเตรียมสภาพแวดล้อมสำหรับ Windows User](#️-การเตรียมสภาพแวดล้อมสำหรับ-windows-user-️-การเตรียมสภาพแวดล้อมสำหรับ-windows-user-️-การเตรียมสภาพแวดล้อมสำหรับ-windows-user)
      - [MacOScOScOS](#macoscoscos)
      - [Linuxnuxnux](#linuxnuxnux)
    - [เริ่มใช้งาน Minikube่มใช้งาน Minikube่มใช้งาน Minikube](#เริ่มใช้งาน-minikube่มใช้งาน-minikube่มใช้งาน-minikube)
  - [🚀 เริ่มต้นใช้งาน Kubernetes## 🚀 เริ่มต้นใช้งาน Kubernetes## 🚀 เริ่มต้นใช้งาน Kubernetes](#-เริ่มต้นใช้งาน-kubernetes--เริ่มต้นใช้งาน-kubernetes--เริ่มต้นใช้งาน-kubernetes)
    - [การตรวจสอบสถานะของ Clusterตรวจสอบสถานะของ Clusterตรวจสอบสถานะของ Cluster](#การตรวจสอบสถานะของ-clusterตรวจสอบสถานะของ-clusterตรวจสอบสถานะของ-cluster)
    - [kubectl config### kubectl config### kubectl config](#kubectl-config-kubectl-config-kubectl-config)
    - [Kubernetes YAML Filess YAML Filesg current-context](#kubernetes-yaml-filess-yaml-filesg-current-context)
    - [การใช้งานคำสั่งพื้นฐาน  name: nginx-pod### การใช้งานคำสั่งพื้นฐาน](#การใช้งานคำสั่งพื้นฐาน--name-nginx-pod-การใช้งานคำสั่งพื้นฐาน)
  - [🔄 การ Deploy แอปพลิเคชันบน Kubernetes](#-การ-deploy-แอปพลิเคชันบน-kubernetes)
    - [Deployment คืออะไร?](#deployment-คืออะไร)
      - [บทบาทและความสำคัญของ Deploymenteploymentนบน Kubernetes](#บทบาทและความสำคัญของ-deploymenteploymentนบน-kubernetes)
      - [ตัวอย่างสถานการณ์การทำงานจริงของ Deployment](#ตัวอย่างสถานการณ์การทำงานจริงของ-deployment)
      - [แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Deploymentนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Deploymenteployment เริ่มทำ Rolling Update โดย:](#แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ-deploymentนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ-deploymenteployment-เริ่มทำ-rolling-update-โดย)
        - [สิ่งที่ควรทำ ✅](#สิ่งที่ควรทำ-)
      - [แผนภาพกระบวนการ Deployment และ ServiceServiceน เช่น `image: myapp:v1.2.3` หรือ SHA hash](#แผนภาพกระบวนการ-deployment-และ-serviceserviceน-เช่น-image-myappv123-หรือ-sha-hash)
    - [การสร้าง DeploymentI: Create Serviceloyment](#การสร้าง-deploymenti-create-serviceloyment)
    - [Service คืออะไร?](#service-คืออะไร)
      - [บทบาทและความสำคัญของ Service](#บทบาทและความสำคัญของ-service)
      - [ประเภทของ Serviceายนอก](#ประเภทของ-serviceายนอก)
      - [ประเภทของ Service](#ประเภทของ-service)
      - [ตัวอย่างสถานการณ์การทำงานจริงของ Serviceงานจริงของ Service](#ตัวอย่างสถานการณ์การทำงานจริงของ-serviceงานจริงของ-service)
        - [สถานการณ์: แอปพลิเคชันอีคอมเมิร์ซที่มีหลายส่วนประกอบรณ์: แอปพลิเคชันอีคอมเมิร์ซที่มีหลายส่วนประกอบIP address ภายนอกที่สามารถเข้าถึงได้จากอินเทอร์เน็ต](#สถานการณ์-แอปพลิเคชันอีคอมเมิร์ซที่มีหลายส่วนประกอบรณ์-แอปพลิเคชันอีคอมเมิร์ซที่มีหลายส่วนประกอบip-address-ภายนอกที่สามารถเข้าถึงได้จากอินเทอร์เน็ต)
      - [แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Service](#แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ-service)
        - [สิ่งที่ควรทำ ✅##### สิ่งที่ควรทำ ✅   - หนึ่งใน product-service pods เกิดปัญหาและไม่ผ่าน readiness probe](#สิ่งที่ควรทำ--สิ่งที่ควรทำ------หนึ่งใน-product-service-pods-เกิดปัญหาและไม่ผ่าน-readiness-probe)
        - [สิ่งที่ควรหลีกเลี่ยง ❌](#สิ่งที่ควรหลีกเลี่ยง-)
      - [แผนภาพการทำงานของ Service](#แผนภาพการทำงานของ-service)
  - [📈 การ Scale และ Update แอปพลิเคชัน# สร้าง service## 📈 การ Scale และ Update แอปพลิเคชัน](#-การ-scale-และ-update-แอปพลิเคชัน-สร้าง-service--การ-scale-และ-update-แอปพลิเคชัน)
    - [การ Scale แอปพลิเคชัน](#การ-scale-แอปพลิเคชัน)
  - [🌐 การทำ Networking ใน Kubernetess](#-การทำ-networking-ใน-kubernetess)
- [Update image ของ deployment](#update-image-ของ-deployment)
    - [Service Types](#service-types)
    - [Ingress](#ingress)
      - [Ingress คืออะไร?](#ingress-คืออะไร)
      - [Ingress Controller คืออะไร?](#ingress-controller-คืออะไร)
      - [ตัวอย่างสถานการณ์การทำงานจริงของ Ingress#### ตัวอย่างสถานการณ์การทำงานจริงของ Ingress#### Ingress Controller คืออะไร?](#ตัวอย่างสถานการณ์การทำงานจริงของ-ingress-ตัวอย่างสถานการณ์การทำงานจริงของ-ingress-ingress-controller-คืออะไร)
      - [แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Ingress](#แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ-ingress)
        - [สิ่งที่ควรทำ ✅รทำ ✅](#สิ่งที่ควรทำ-รทำ-)
    - [Network Policiesciesร้าง URL ที่สมเหตุสมผลและสอดคล้องกับโครงสร้าง microservices](#network-policiesciesร้าง-url-ที่สมเหตุสมผลและสอดคล้องกับโครงสร้าง-microservices)
- [persistent-volume-claim.yaml my-pvstent-volume-claim.yaml](#persistent-volume-claimyaml-my-pvstent-volume-claimyaml)
    - [การใช้ PVC กับ Pod](#การใช้-pvc-กับ-pod)
    - [ConfigMaps และ Secrets  - name: nginx### ConfigMaps และ Secrets](#configmaps-และ-secrets----name-nginx-configmaps-และ-secrets)
      - [ConfigMapumeMounts:nfigMap](#configmapumemountsnfigmap)
      - [ConfigMap](#configmap)
      - [Secret](#secret)
- [my-secret.yaml](#my-secretyaml)
      - [แผนภาพสิทธิ์การเข้าถึงด้วย RBACถึงด้วย RBAC](#แผนภาพสิทธิ์การเข้าถึงด้วย-rbacถึงด้วย-rbac)
    - [Pod Security Policies](#pod-security-policies)
    - [การ Deploy แอปพลิเคชันบน DOKSn sgp1 \\oy แอปพลิเคชันบน DOKS](#การ-deploy-แอปพลิเคชันบน-doksn-sgp1-oy-แอปพลิเคชันบน-doks)
- [ติดตั้ง Helm](#ติดตั้ง-helm)
- [ติดตั้ง Istio](#ติดตั้ง-istio)

## บทนำ## บทนำ## บทนำ

Container Orchestration คือการจัดการ containers จำนวนมากให้สามารถทำงานร่วมกันได้อย่างมีประสิทธิภาพ Kubernetes (K8s) เป็นระบบ container orchestration ที่ได้รับความนิยมมากที่สุดในปัจจุบัน เราจะเรียนรู้ตั้งแต่พื้นฐานไปจนถึงการ deploy บน cloud provider อย่าง Digital OceanContainer Orchestration คือการจัดการ containers จำนวนมากให้สามารถทำงานร่วมกันได้อย่างมีประสิทธิภาพ Kubernetes (K8s) เป็นระบบ container orchestration ที่ได้รับความนิยมมากที่สุดในปัจจุบัน เราจะเรียนรู้ตั้งแต่พื้นฐานไปจนถึงการ deploy บน cloud provider อย่าง Digital OceanContainer Orchestration คือการจัดการ containers จำนวนมากให้สามารถทำงานร่วมกันได้อย่างมีประสิทธิภาพ Kubernetes (K8s) เป็นระบบ container orchestration ที่ได้รับความนิยมมากที่สุดในปัจจุบัน เราจะเรียนรู้ตั้งแต่พื้นฐานไปจนถึงการ deploy บน cloud provider อย่าง Digital Ocean

## 🔰 พื้นฐาน Container และ Kubernetes## 🔰 พื้นฐาน Container และ Kubernetes## 🔰 พื้นฐาน Container และ Kubernetes

### Container คืออะไร?### Container คืออะไร?### Container คืออะไร?

Container เป็นหน่วยของซอฟต์แวร์ที่แพ็กโค้ดและส่วนประกอบทั้งหมดที่จำเป็นเพื่อให้แอปพลิเคชันทำงานได้ในทุกสภาพแวดล้อม ต่างจาก VM ตรงที่ container ใช้ทรัพยากรน้อยกว่า และทำงานบน OS kernel เดียวกันContainer เป็นหน่วยของซอฟต์แวร์ที่แพ็กโค้ดและส่วนประกอบทั้งหมดที่จำเป็นเพื่อให้แอปพลิเคชันทำงานได้ในทุกสภาพแวดล้อม ต่างจาก VM ตรงที่ container ใช้ทรัพยากรน้อยกว่า และทำงานบน OS kernel เดียวกันContainer เป็นหน่วยของซอฟต์แวร์ที่แพ็กโค้ดและส่วนประกอบทั้งหมดที่จำเป็นเพื่อให้แอปพลิเคชันทำงานได้ในทุกสภาพแวดล้อม ต่างจาก VM ตรงที่ container ใช้ทรัพยากรน้อยกว่า และทำงานบน OS kernel เดียวกัน

### Kubernetes คืออะไร?### Kubernetes คืออะไร?### Kubernetes คืออะไร?

Kubernetes เป็นแพลตฟอร์มโอเพนซอร์สที่ออกแบบมาเพื่อจัดการ container จำนวนมากโดยอัตโนมัติ ไม่ว่าจะเป็นการ deploy, การปรับขนาด และการจัดการKubernetes เป็นแพลตฟอร์มโอเพนซอร์สที่ออกแบบมาเพื่อจัดการ container จำนวนมากโดยอัตโนมัติ ไม่ว่าจะเป็นการ deploy, การปรับขนาด และการจัดการKubernetes เป็นแพลตฟอร์มโอเพนซอร์สที่ออกแบบมาเพื่อจัดการ container จำนวนมากโดยอัตโนมัติ ไม่ว่าจะเป็นการ deploy, การปรับขนาด และการจัดการ

### สถาปัตยกรรมของ Kubernetes### สถาปัตยกรรมของ Kubernetes### สถาปัตยกรรมของ Kubernetes

Kubernetes ประกอบด้วยองค์ประกอบหลักดังนี้:Kubernetes ประกอบด้วยองค์ประกอบหลักดังนี้:Kubernetes ประกอบด้วยองค์ประกอบหลักดังนี้:

1. **Control Plane (Master Node)**:
   - API Server: จุดศูนย์กลางการติดต่อกับ Kubernetes cluster
   - etcd: ฐานข้อมูลแบบ key-value สำหรับเก็บข้อมูลของ clustererer
   - Scheduler: ทำการตัดสินใจว่า pod ควรจะทำงานที่ node ไหน
   - Controller Manager: จัดการสถานะของ cluster ให้ตรงกับที่ต้องการ   - Controller Manager: จัดการสถานะของ cluster ให้ตรงกับที่ต้องการ   - Controller Manager: จัดการสถานะของ cluster ให้ตรงกับที่ต้องการ

2. **Worker Nodes**:
   - Kubelet: เอเจนต์ที่ทำงานบนแต่ละ node เพื่อสื่อสารกับ control planeรกับ control planeรกับ control plane
   - Kube-proxy: จัดการ network rules และการเชื่อมต่อ่อมต่อ่อมต่อ
   - Container Runtime: เช่น Docker, containerd   - Container Runtime: เช่น Docker, containerd   - Container Runtime: เช่น Docker, containerd

3. **Kubernetes Objects**:
   - Pod: หน่วยพื้นฐานที่เล็กที่สุดที่สามารถ deploy บน Kubernetesetesetes
   - Service: การเชื่อมต่อระหว่าง Pods และการเข้าถึงจากภายนอกและการเข้าถึงจากภายนอกและการเข้าถึงจากภายนอก
   - Volume: การจัดการพื้นที่เก็บข้อมูล
   - Namespace: การแบ่งแยกทรัพยากรในคลัสเตอร์   - Namespace: การแบ่งแยกทรัพยากรในคลัสเตอร์   - Namespace: การแบ่งแยกทรัพยากรในคลัสเตอร์

#### แผนภาพสถาปัตยกรรม Kubernetes#### แผนภาพสถาปัตยกรรม Kubernetes#### แผนภาพสถาปัตยกรรม Kubernetes

```mermaid
flowchart TB
    subgraph "Control Plane (Master Node)"de)"de)"
        API[API Server] --> ETCD[etcd]CD[etcd]CD[etcd]
        API --> SCH[Scheduler]
        API --> CM[Controller Manager] API --> CM[Controller Manager] API --> CM[Controller Manager]
    endendend
    
    subgraph "Worker Node 1"
        KL1[Kubelet] --> CR1[Container Runtime]> CR1[Container Runtime]> CR1[Container Runtime]
        KP1[Kube-proxy]
        subgraph "Pods"
            P1[Pod 1] --> C1[Container 1]iner 1]iner 1]
            P1 --> C2[Container 2] P1 --> C2[Container 2] P1 --> C2[Container 2]
        end end end
    endendend
    
    subgraph "Worker Node 2"
        KL2[Kubelet] --> CR2[Container Runtime]> CR2[Container Runtime]> CR2[Container Runtime]
        KP2[Kube-proxy]
        subgraph "Pods"
            P2[Pod 2] --> C3[Container 3] P2[Pod 2] --> C3[Container 3] P2[Pod 2] --> C3[Container 3]
        end end end
    endendend
    
    API --> KL1
    API --> KL222
    CM --> KL1
    CM --> KL2
    SCH --> KL1
    SCH --> KL2 SCH --> KL2 SCH --> KL2
`````````

## ⚙️ การเตรียมสภาพแวดล้อมสำหรับ Windows User## ⚙️ การเตรียมสภาพแวดล้อมสำหรับ Windows User## ⚙️ การเตรียมสภาพแวดล้อมสำหรับ Windows User

สำหรับผู้ใช้ Windows จำเป็นต้องเตรียมสภาพแวดล้อมให้พร้อมก่อนเริ่มใช้งาน Kubernetes:สำหรับผู้ใช้ Windows จำเป็นต้องเตรียมสภาพแวดล้อมให้พร้อมก่อนเริ่มใช้งาน Kubernetes:สำหรับผู้ใช้ Windows จำเป็นต้องเตรียมสภาพแวดล้อมให้พร้อมก่อนเริ่มใช้งาน Kubernetes:

1. **ติดตั้ง Windows Subsystem for Linux (WSL2)** - ทำให้สามารถรัน Linux บน Windows ได้้ง Windows Subsystem for Linux (WSL2)** - ทำให้สามารถรัน Linux บน Windows ได้้ง Windows Subsystem for Linux (WSL2)** - ทำให้สามารถรัน Linux บน Windows ได้
   ```bash
   # เปิด PowerShell as Administrator แล้วรันคำสั่งhell as Administrator แล้วรันคำสั่งhell as Administrator แล้วรันคำสั่ง
   wsl --install
   # รีสตาร์ทเครื่องีสตาร์ทเครื่องีสตาร์ทเครื่อง
   ```   ```   ```

2. **ติดตั้ง Docker Desktop** - ดาวน์โหลดและติดตั้งจาก [docker.com](https://www.docker.com/products/docker-desktop)ิดตั้งจาก [docker.com](https://www.docker.com/products/docker-desktop)ิดตั้งจาก [docker.com](https://www.docker.com/products/docker-desktop)
   - ตั้งค่า Docker Desktop ให้ใช้งานกับ WSL2   - ตั้งค่า Docker Desktop ให้ใช้งานกับ WSL2   - ตั้งค่า Docker Desktop ให้ใช้งานกับ WSL2

3. **ติดตั้ง kubectl** - เครื่องมือสำหรับควบคุม Kubernetes cluster้ง kubectl** - เครื่องมือสำหรับควบคุม Kubernetes cluster้ง kubectl** - เครื่องมือสำหรับควบคุม Kubernetes cluster
   ```bash
   curl -LO "https://dl.k8s.io/release/stable.txt"stable.txt"stable.txt"
   $version = $(Get-Content stable.txt)
   curl -LO "https://dl.k8s.io/release/$version/bin/windows/amd64/kubectl.exe"dl.k8s.io/release/$version/bin/windows/amd64/kubectl.exe"dl.k8s.io/release/$version/bin/windows/amd64/kubectl.exe"
   # ย้ายไปไว้ใน PATH้ายไปไว้ใน PATH้ายไปไว้ใน PATH
   ```   ```   ```

4. **ติดตั้ง Windows Terminal** - แนะนำให้ใช้งานเพื่อความสะดวก แนะนำให้ใช้งานเพื่อความสะดวก แนะนำให้ใช้งานเพื่อความสะดวก
   - ดาวน์โหลดจาก Microsoft Store   - ดาวน์โหลดจาก Microsoft Store   - ดาวน์โหลดจาก Microsoft Store

## 🏗️ การติดตั้ง Minikube## 🏗️ การติดตั้ง Minikube## 🏗️ การติดตั้ง Minikube

Minikube เป็นเครื่องมือที่ช่วยให้รัน Kubernetes แบบ single-node cluster บนเครื่องของเราได้ เหมาะสำหรับการเรียนรู้และพัฒนาMinikube เป็นเครื่องมือที่ช่วยให้รัน Kubernetes แบบ single-node cluster บนเครื่องของเราได้ เหมาะสำหรับการเรียนรู้และพัฒนาMinikube เป็นเครื่องมือที่ช่วยให้รัน Kubernetes แบบ single-node cluster บนเครื่องของเราได้ เหมาะสำหรับการเรียนรู้และพัฒนา

### การติดตั้ง Minikube### การติดตั้ง Minikube### การติดตั้ง Minikube

#### Windowsndowsndows
```bash
# ดาวน์โหลด installer จาก https://minikube.sigs.k8s.io/docs/start/r จาก https://minikube.sigs.k8s.io/docs/start/r จาก https://minikube.sigs.k8s.io/docs/start/
# หรือใช้ chocolatey
choco install minikubeco install minikubeco install minikube
`````````

#### MacOScOScOS
```bash
brew install minikubew install minikubew install minikube
`````````

#### Linuxnuxnux
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64/latest/minikube-linux-amd64/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikubeo install minikube-linux-amd64 /usr/local/bin/minikubeo install minikube-linux-amd64 /usr/local/bin/minikube
`````````

### เริ่มใช้งาน Minikube่มใช้งาน Minikube่มใช้งาน Minikube
```bash
# เริ่มต้น Minikube
minikube start --driver=dockerminikube start --driver=dockerminikube start --driver=docker

# ตรวจสอบสถานะ
minikube statusminikube statusminikube status

# เปิด Kubernetes DashboardDashboardDashboard
minikube dashboardikube dashboardikube dashboard
`````````

## 🚀 เริ่มต้นใช้งาน Kubernetes## 🚀 เริ่มต้นใช้งาน Kubernetes## 🚀 เริ่มต้นใช้งาน Kubernetes

เมื่อติดตั้ง Minikube เรียบร้อยแล้ว เราสามารถเริ่มใช้งาน Kubernetes ได้ทันทีเมื่อติดตั้ง Minikube เรียบร้อยแล้ว เราสามารถเริ่มใช้งาน Kubernetes ได้ทันทีเมื่อติดตั้ง Minikube เรียบร้อยแล้ว เราสามารถเริ่มใช้งาน Kubernetes ได้ทันที

### การตรวจสอบสถานะของ Clusterตรวจสอบสถานะของ Clusterตรวจสอบสถานะของ Cluster
```bash
# ดูข้อมูลของ clusterrr
kubectl cluster-infokubectl cluster-infokubectl cluster-info

# ดูรายการ nodes
kubectl get nodeskubectl get nodeskubectl get nodes

# ดูรายการ namespace
kubectl get namespacesectl get namespacesectl get namespaces
`````````

### kubectl config### kubectl config### kubectl config
```bash
# ดู context ที่ใช้งานอยู่# ดู context ปัจจุบันkubectl config เป็นคำสั่งที่ใช้ในการจัดการการเชื่อมต่อกับ Kubernetes clusters หลายๆ คลัสเตอร์ โดยเฉพาะในสถานการณ์ที่คุณต้องทำงานกับหลายสภาพแวดล้อม เช่น development, staging และ production
kubectl config current-context config current-context

# ดูรายการ context ทั้งหมดtext ทั้งหมด kubectl ทั้งหมด
kubectl config get-contextsonfig get-contextsonfig view

# สลับ context(การเชื่อมต่อกับ clusters)
kubectl config use-context <context-name>onfig use-context <context-name>onfig get-contexts
```
nt-context ที่กำลังใช้งานอยู่
### Kubernetes YAML Filess YAML Filesg current-context

การสร้างและจัดการทรัพยากรใน Kubernetes จะใช้ไฟล์ YAML เป็นหลัก ตัวอย่าง:กรใน Kubernetes จะใช้ไฟล์ YAML เป็นหลัก ตัวอย่าง:น
ontext my-cluster-name
```yaml
# ตัวอย่าง Podัวอย่าง Podั้งค่า namespace เริ่มต้นสำหรับ context ปัจจุบัน
apiVersion: v1apiVersion: v1kubectl config set-context --current --namespace=my-namespace
kind: Pod
metadata:
  name: nginx-podวย kubectl config จะช่วยให้คุณสามารถสลับระหว่างสภาพแวดล้อมต่างๆ ได้อย่างรวดเร็ว และป้องกันความผิดพลาดในการรันคำสั่งบน cluster ที่ไม่ต้องการ
  labels:
    app: nginx### Kubernetes YAML Files    app: nginx
spec:
  containers:รทรัพยากรใน Kubernetes จะใช้ไฟล์ YAML เป็นหลัก ตัวอย่าง:
  - name: nginx  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80apiVersion: v1    - containerPort: 80
```

### การใช้งานคำสั่งพื้นฐาน  name: nginx-pod### การใช้งานคำสั่งพื้นฐาน
```bash
# สร้าง resource จาก YAML
kubectl apply -f my-pod.yamlspec:kubectl apply -f my-pod.yaml
ners:
# ดูรายการ pods
kubectl get pods image: nginx:latestectl get pods
    ports:
# ดูรายละเอียดของ podort: 80ง pod
kubectl describe pod nginx-pod```kubectl describe pod nginx-pod

# เข้าถึง shell ของ pod### การใช้งานคำสั่งพื้นฐาน# เข้าถึง shell ของ pod
kubectl exec -it nginx-pod -- /bin/bash
# สร้าง resource จาก YAML
# ดูบันทึกของ pod
kubectl logs nginx-pod

# ลบ podkubectl get pods# ลบ pod
kubectl delete pod nginx-pod
```# ดูรายละเอียดของ pod```

### Pod คืออะไร?

Pod เป็นหน่วยพื้นฐานที่เล็กที่สุดที่สามารถ deploy และจัดการได้ใน Kubernetes โดยมีลักษณะสำคัญดังนี้:

#### หลักการทำงานของ Pod# ดูบันทึกของ pod#### หลักการทำงานของ Pod

- **กลุ่มของ Containers**: Pod สามารถประกอบด้วย container หนึ่งตัวหรือหลายตัวที่ทำงานร่วมกัน และแชร์ทรัพยากรระหว่างกัน- **กลุ่มของ Containers**: Pod สามารถประกอบด้วย container หนึ่งตัวหรือหลายตัวที่ทำงานร่วมกัน และแชร์ทรัพยากรระหว่างกัน
- **Shared Namespace**: Containers ในแต่ละ Pod จะแชร์ network namespace, IPC namespace และ UTS namespace ทำให้สามารถสื่อสารกันผ่าน localhost ได้ผ่าน localhost ได้
- **Atomic Unit**: ไม่สามารถแยก deploy containers ในแต่ละ Pod ได้ ทุก container จะถูก schedule ไปยัง node เดียวกันและทำงานหรือล้มเหลวไปพร้อมกันner จะถูก schedule ไปยัง node เดียวกันและทำงานหรือล้มเหลวไปพร้อมกัน

#### คุณลักษณะเฉพาะของ Pod
### Pod คืออะไร?
1. **Ephemeral (ชั่วคราว)**: Pods ถูกออกแบบให้เป็นหน่วยแบบใช้แล้วทิ้ง ไม่ควรคาดหวังว่า Pod จะมีอายุยาวนานds ถูกออกแบบให้เป็นหน่วยแบบใช้แล้วทิ้ง ไม่ควรคาดหวังว่า Pod จะมีอายุยาวนาน
2. **Storage Volume**: สามารถกำหนด volumes ที่จะแชร์ระหว่าง containers ในแต่ละ Pod ได้2. **Storage Volume**: สามารถกำหนด volumes ที่จะแชร์ระหว่าง containers ในแต่ละ Pod ได้Pod เป็นหน่วยพื้นฐานที่เล็กที่สุดที่สามารถ deploy และจัดการได้ใน Kubernetes โดยมีลักษณะสำคัญดังนี้:
3. **Init Containers**: สามารถกำหนด containers พิเศษที่จะทำงานและเสร็จสิ้นก่อนที่ containers หลักจะเริ่มทำงาน
4. **Quality of Service (QoS)**: มีการจัดระดับความสำคัญของการใช้ทรัพยากรเป็น Guaranteed, Burstable และ BestEffortะ BestEffort
5. **Pod Lifecycle**: วงจรชีวิตของ Pod ประกอบด้วยหลายสถานะ เช่น Pending, Running, Succeeded, Failed และ Unknown

#### ข้อจำกัดของ Pod
- **Atomic Unit**: ไม่สามารถแยก deploy containers ในแต่ละ Pod ได้ ทุก container จะถูก schedule ไปยัง node เดียวกันและทำงานหรือล้มเหลวไปพร้อมกัน
1. **ไม่มี Self-healing**: หาก Pod ล้มเหลวหรือถูกลบ ระบบจะไม่พยายามสร้างใหม่โดยอัตโนมัติ (ต้องใช้ controllers เช่น Deployment)ระบบจะไม่พยายามสร้างใหม่โดยอัตโนมัติ (ต้องใช้ controllers เช่น Deployment)
2. **ไม่มี Auto-scaling**: ไม่สามารถขยายหรือลด Pod โดยอัตโนมัติได้ด้วยตัวเอง2. **ไม่มี Auto-scaling**: ไม่สามารถขยายหรือลด Pod โดยอัตโนมัติได้ด้วยตัวเอง#### คุณลักษณะเฉพาะของ Pod
3. **Node Binding**: เมื่อ Pod ถูกกำหนดให้ทำงานบน node ใดแล้ว จะไม่สามารถย้ายไปยัง node อื่นได้de Binding**: เมื่อ Pod ถูกกำหนดให้ทำงานบน node ใดแล้ว จะไม่สามารถย้ายไปยัง node อื่นได้
4. **IP Address**: แต่ละ Pod จะมี IP address เฉพาะ แต่ IP นี้จะเปลี่ยนเมื่อ Pod ถูกสร้างใหม่s**: แต่ละ Pod จะมี IP address เฉพาะ แต่ IP นี้จะเปลี่ยนเมื่อ Pod ถูกสร้างใหม่ (ชั่วคราว)**: Pods ถูกออกแบบให้เป็นหน่วยแบบใช้แล้วทิ้ง ไม่ควรคาดหวังว่า Pod จะมีอายุยาวนาน
e**: สามารถกำหนด volumes ที่จะแชร์ระหว่าง containers ในแต่ละ Pod ได้
#### ข้อควรระวังในการใช้งาน Podวรระวังในการใช้งาน Pod Containers**: สามารถกำหนด containers พิเศษที่จะทำงานและเสร็จสิ้นก่อนที่ containers หลักจะเริ่มทำงาน
ญของการใช้ทรัพยากรเป็น Guaranteed, Burstable และ BestEffort
1. **ไม่ควรสร้าง Pod โดยตรง**: ควรใช้ controllers (เช่น Deployment, StatefulSet, DaemonSet) ในการจัดการ Pod แทนวรสร้าง Pod โดยตรง**: ควรใช้ controllers (เช่น Deployment, StatefulSet, DaemonSet) ในการจัดการ Pod แทนLifecycle**: วงจรชีวิตของ Pod ประกอบด้วยหลายสถานะ เช่น Pending, Running, Succeeded, Failed และ Unknown
2. **การออกแบบ Multi-container Pods**: ควรใส่เฉพาะ containers ที่ต้องทำงานร่วมกันอย่างใกล้ชิดเท่านั้นบบ Multi-container Pods**: ควรใส่เฉพาะ containers ที่ต้องทำงานร่วมกันอย่างใกล้ชิดเท่านั้น
3. **Resource Request และ Limits**: ควรกำหนด resource requests และ limits ให้กับ containers เพื่อป้องกันการใช้ทรัพยากรมากเกินไปResource Request และ Limits**: ควรกำหนด resource requests และ limits ให้กับ containers เพื่อป้องกันการใช้ทรัพยากรมากเกินไปข้อจำกัดของ Pod
4. **Health Checks**: ควรกำหนด liveness และ readiness probes เพื่อให้ Kubernetes ตรวจสอบสถานะของ application ได้อย่างถูกต้องhecks**: ควรกำหนด liveness และ readiness probes เพื่อให้ Kubernetes ตรวจสอบสถานะของ application ได้อย่างถูกต้อง
5. **Pod Affinity/Anti-affinity**: พิจารณาใช้กฎการจัดวาง Pod เพื่อกระจายหรือรวมกลุ่ม Pod ตามความเหมาะสมnity/Anti-affinity**: พิจารณาใช้กฎการจัดวาง Pod เพื่อกระจายหรือรวมกลุ่ม Pod ตามความเหมาะสมlf-healing**: หาก Pod ล้มเหลวหรือถูกลบ ระบบจะไม่พยายามสร้างใหม่โดยอัตโนมัติ (ต้องใช้ controllers เช่น Deployment)
ือลด Pod โดยอัตโนมัติได้ด้วยตัวเอง
#### ตัวอย่าง YAML ของ Pod ที่มี Multiple Containers่าง YAML ของ Pod ที่มี Multiple ContainersBinding**: เมื่อ Pod ถูกกำหนดให้ทำงานบน node ใดแล้ว จะไม่สามารถย้ายไปยัง node อื่นได้
ฉพาะ แต่ IP นี้จะเปลี่ยนเมื่อ Pod ถูกสร้างใหม่
```yaml
apiVersion: v1
kind: Pod
metadata:data:*ไม่ควรสร้าง Pod โดยตรง**: ควรใช้ controllers (เช่น Deployment, StatefulSet, DaemonSet) ในการจัดการ Pod แทน
  name: multi-container-podner Pods**: ควรใส่เฉพาะ containers ที่ต้องทำงานร่วมกันอย่างใกล้ชิดเท่านั้น
  labels: ควรกำหนด resource requests และ limits ให้กับ containers เพื่อป้องกันการใช้ทรัพยากรมากเกินไป
    app: web liveness และ readiness probes เพื่อให้ Kubernetes ตรวจสอบสถานะของ application ได้อย่างถูกต้อง
spec:Affinity/Anti-affinity**: พิจารณาใช้กฎการจัดวาง Pod เพื่อกระจายหรือรวมกลุ่ม Pod ตามความเหมาะสม
  containers:
  - name: web
    image: nginx:1.20
    ports:
    - containerPort: 80 80
    volumeMounts:
    - name: shared-data
      mountPath: /usr/share/nginx/html: multi-container-podmountPath: /usr/share/nginx/html
    
  - name: content-generator
    image: alpine:3.14
    command: ["/bin/sh", "-c"]ontainers: command: ["/bin/sh", "-c"]
    args:  - name: web    args:
    - while true; do
        echo "<h1>เวลาปัจจุบัน: $(date)</h1>" > /content/index.html;        echo "<h1>เวลาปัจจุบัน: $(date)</h1>" > /content/index.html;    ports:
        sleep 10;
      done      done    volumeMounts:
    volumeMounts:
    - name: shared-data      mountPath: /usr/share/nginx/html    - name: shared-data
      mountPath: /content
      
  volumes:
  - name: shared-data
    emptyDir: {}    args:    emptyDir: {}
```
        echo "<h1>เวลาปัจจุบัน: $(date)</h1>" > /content/index.html;
## 🔄 การ Deploy แอปพลิเคชันบน Kubernetes
      done
การ deploy แอปพลิเคชันบน Kubernetes จะใช้ Deployment เป็นหลัก

### Deployment คืออะไร?

Deployment เป็น resource ที่จัดการชุดของ Pods ที่เหมือนกันหลาย ๆ ตัว มีความสามารถในการ:  volumes:Deployment เป็น resource ที่จัดการชุดของ Pods ที่เหมือนกันหลาย ๆ ตัว มีความสามารถในการ:
- จัดการและอัปเดตแอปพลิเคชันอย่างนุ่มนวล
- Roll back ไปยังเวอร์ชันก่อนหน้าได้- Roll back ไปยังเวอร์ชันก่อนหน้าได้    emptyDir: {}
- Scale และ autoscale แอปพลิเคชัน

#### บทบาทและความสำคัญของ Deploymenteploymentนบน Kubernetes

Deployment เป็นหนึ่งในทรัพยากรหลักที่สำคัญที่สุดใน Kubernetes มีหน้าที่ดังนี้:ี่ดังนี้:

1. **จัดการวงจรชีวิตของ Pods** - Deployment จะสร้าง ReplicaSet ซึ่งเป็นตัวควบคุมการสร้างและลบ Pods ตามจำนวนที่กำหนด1. **จัดการวงจรชีวิตของ Pods** - Deployment จะสร้าง ReplicaSet ซึ่งเป็นตัวควบคุมการสร้างและลบ Pods ตามจำนวนที่กำหนด### Deployment คืออะไร?
2. **รับประกันความพร้อมใช้งาน** - หาก Pod ล้มเหลว Deployment จะสร้าง Pod ใหม่ทดแทนโดยอัตโนมัติพร้อมใช้งาน** - หาก Pod ล้มเหลว Deployment จะสร้าง Pod ใหม่ทดแทนโดยอัตโนมัติ
3. **อัพเดตแบบ Rolling Update** - อัพเดตแอปพลิเคชันทีละส่วนโดยไม่ทำให้เกิดการหยุดให้บริการ้เกิดการหยุดให้บริการมีความสามารถในการ:
4. **ประวัติการ Deploy** - เก็บประวัติการเปลี่ยนแปลงและสามารถย้อนกลับไปใช้เวอร์ชันก่อนหน้าได้กลับไปใช้เวอร์ชันก่อนหน้าได้

#### ตัวอย่างสถานการณ์การทำงานจริงของ Deployment

สมมติว่าคุณเป็นผู้ดูแลระบบที่ต้องการ deploy แอปพลิเคชัน web server ให้มีความพร้อมใช้งานสูง:่ต้องการ deploy แอปพลิเคชัน web server ให้มีความพร้อมใช้งานสูง:ployment

1. **เริ่มต้น Deployment**:
   - คุณสร้าง Deployment ที่มี 3 replicas ของ nginxอง nginx
   - Kubernetes จะสร้าง ReplicaSet และ 3 Pods กระจายไปยัง nodes ต่างๆระจายไปยัง nodes ต่างๆร้าง ReplicaSet ซึ่งเป็นตัวควบคุมการสร้างและลบ Pods ตามจำนวนที่กำหนด
   - แอปพลิเคชันของคุณเริ่มทำงานและให้บริการผ่าน Serviceมัติ

2. **ระหว่างวัน**:
   - หนึ่งใน node เกิดปัญหาและล่ม ทำให้ Pod ที่ทำงานบน node นั้นหายไป   - หนึ่งใน node เกิดปัญหาและล่ม ทำให้ Pod ที่ทำงานบน node นั้นหายไป
   - Deployment ตรวจพบว่ามี Pods ที่ทำงานอยู่น้อยกว่าที่กำหนด (3)พบว่ามี Pods ที่ทำงานอยู่น้อยกว่าที่กำหนด (3)ณ์การทำงานจริงของ Deployment
   - Deployment สั่ง ReplicaSet ให้สร้าง Pod ใหม่บน node ที่ยังทำงานได้od ใหม่บน node ที่ยังทำงานได้
   - ระบบกลับมาให้บริการเต็มประสิทธิภาพโดยอัตโนมัติวามพร้อมใช้งานสูง:

3. **การอัปเดตแอปพลิเคชัน**:3. **การอัปเดตแอปพลิเคชัน**:1. **เริ่มต้น Deployment**:
   - คุณต้องการอัปเดตจาก nginx 1.14 เป็น nginx 1.15
   - คุณรัน `kubectl set image deployment/nginx-deployment nginx=nginx:1.15`   - คุณรัน `kubectl set image deployment/nginx-deployment nginx=nginx:1.15`   - Kubernetes จะสร้าง ReplicaSet และ 3 Pods กระจายไปยัง nodes ต่างๆ
   - Deployment เริ่มทำ Rolling Update โดย:มทำ Rolling Update โดย:ุณเริ่มทำงานและให้บริการผ่าน Service
     - สร้าง ReplicaSet ใหม่สำหรับเวอร์ชัน 1.15     - สร้าง ReplicaSet ใหม่สำหรับเวอร์ชัน 1.15
     - ค่อยๆ ลด Pods ในเวอร์ชันเก่าลง พร้อมๆ กับเพิ่ม Pods ในเวอร์ชันใหม่ กับเพิ่ม Pods ในเวอร์ชันใหม่
     - ตรวจสอบสถานะของ Pods ใหม่ว่าพร้อมให้บริการหรือไม่จสอบสถานะของ Pods ใหม่ว่าพร้อมให้บริการหรือไม่ใน node เกิดปัญหาและล่ม ทำให้ Pod ที่ทำงานบน node นั้นหายไป
     - เมื่อเสร็จสิ้น Pods ทั้งหมดจะเป็นเวอร์ชัน 1.15 และยังคงให้บริการได้ต่อเนื่องระหว่างการอัปเดตสร็จสิ้น Pods ทั้งหมดจะเป็นเวอร์ชัน 1.15 และยังคงให้บริการได้ต่อเนื่องระหว่างการอัปเดตnt ตรวจพบว่ามี Pods ที่ทำงานอยู่น้อยกว่าที่กำหนด (3)
Set ให้สร้าง Pod ใหม่บน node ที่ยังทำงานได้
4. **เมื่อพบปัญหา**:ารเต็มประสิทธิภาพโดยอัตโนมัติ
   - หลังอัปเดต พบว่ามีบั๊กในเวอร์ชัน 1.15ว่ามีบั๊กในเวอร์ชัน 1.15
   - คุณรัน `kubectl rollout undo deployment/nginx-deployment``kubectl rollout undo deployment/nginx-deployment`ดตแอปพลิเคชัน**:
   - Deployment จะย้อนกลับไปใช้เวอร์ชัน 1.14 โดยอัตโนมัติ ด้วยกระบวนการ Rolling Update แบบเดียวกันกลับไปใช้เวอร์ชัน 1.14 โดยอัตโนมัติ ด้วยกระบวนการ Rolling Update แบบเดียวกันาก nginx 1.14 เป็น nginx 1.15
yment/nginx-deployment nginx=nginx:1.15`
#### แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Deploymentนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Deploymenteployment เริ่มทำ Rolling Update โดย:

##### สิ่งที่ควรทำ ✅
     - ตรวจสอบสถานะของ Pods ใหม่ว่าพร้อมให้บริการหรือไม่
1. **กำหนดค่า Resource Limits และ Requests****อร์ชัน 1.15 และยังคงให้บริการได้ต่อเนื่องระหว่างการอัปเดต
   ```yaml
   resources:
     requests::ดต พบว่ามีบั๊กในเวอร์ชัน 1.15
       memory: "64Mi" rollout undo deployment/nginx-deployment`"
       cpu: "250m"ะย้อนกลับไปใช้เวอร์ชัน 1.14 โดยอัตโนมัติ ด้วยกระบวนการ Rolling Update แบบเดียวกัน"
     limits:
       memory: "128Mi"ีและควรหลีกเลี่ยงสำหรับ Deployment
       cpu: "500m"
   ```ควรทำ ✅
   - ช่วยให้ scheduler สามารถจัดสรรทรัพยากรได้เหมาะสมพยากรได้เหมาะสม
   - ป้องกันไม่ให้แอปพลิเคชันใช้ทรัพยากรมากเกินไปource Limits และ Requests**้แอปพลิเคชันใช้ทรัพยากรมากเกินไป

2. **กำหนด Liveness และ Readiness Probes**ละ Readiness Probes**
   ```yamlyamlequests:
   livenessProbe:
     httpGet:
       path: /health       path: /health     limits:
       port: 8080
     initialDelaySeconds: 30alDelaySeconds: 30: "500m"
     periodSeconds: 10econds: 10
   readinessProbe:ัดสรรทรัพยากรได้เหมาะสม
     httpGet:อปพลิเคชันใช้ทรัพยากรมากเกินไป
       path: /ready
       port: 8080adiness Probes**
     initialDelaySeconds: 5yamlnitialDelaySeconds: 5
     periodSeconds: 5
   ```
   - Liveness probes ตรวจสอบว่าแอปทำงานอยู่หรือไม่ ถ้าไม่จะรีสตาร์ท pod       path: /health   - Liveness probes ตรวจสอบว่าแอปทำงานอยู่หรือไม่ ถ้าไม่จะรีสตาร์ท pod
   - Readiness probes ตรวจสอบว่าแอปพร้อมรับรีเควสหรือยังวสหรือยัง
onds: 30
3. **ตั้งค่า RollingUpdate Strategy ให้เหมาะสม**่า RollingUpdate Strategy ให้เหมาะสม**dSeconds: 10
   ```yaml
   strategy:
     type: RollingUpdatedate
     rollingUpdate:
       maxSurge: 25% maxSurge: 25%nitialDelaySeconds: 5
       maxUnavailable: 25%
   ```   ```   ```
   - กำหนดว่าจะมี pod ใหม่เพิ่มได้มากสุดเท่าไร (maxSurge)ุดเท่าไร (maxSurge)นอยู่หรือไม่ ถ้าไม่จะรีสตาร์ท pod
   - กำหนดว่าสามารถมี pod ที่ไม่พร้อมใช้งานได้มากสุดเท่าไร (maxUnavailable)นได้มากสุดเท่าไร (maxUnavailable)บรีเควสหรือยัง

4. **ใช้ Labels และ Selectors อย่างมีความหมาย**ors อย่างมีความหมาย** Strategy ให้เหมาะสม**
   ```yaml   ```yaml   ```yaml
   labels:
     app: myapp     app: myapp     type: RollingUpdate
     tier: frontend
     version: v1.0.0
     environment: production
   ```   ```   ```
   - ช่วยในการจัดระเบียบ, การค้นหา, และการอ้างถึงกลุ่มของ podsนหา, และการอ้างถึงกลุ่มของ podsได้มากสุดเท่าไร (maxSurge)

5. **เก็บ YAML ไว้ใน Version Control**
   - ติดตามการเปลี่ยนแปลงของ configuration4. **ใช้ Labels และ Selectors อย่างมีความหมาย**   - ติดตามการเปลี่ยนแปลงของ configuration
   - ทำให้สามารถย้อนกลับไปยังเวอร์ชันที่ทำงานได้ถ้าเกิดปัญหาเวอร์ชันที่ทำงานได้ถ้าเกิดปัญหา
   - สนับสนุนแนวทาง GitOps

##### สิ่งที่ควรหลีกเลี่ยง ❌##### สิ่งที่ควรหลีกเลี่ยง ❌     tier: frontend

1. **การแก้ไข Pods โดยตรง**
   - ไม่ควรแก้ไข Pod โดยตรง เพราะเมื่อ Pod ถูกสร้างใหม่ การเปลี่ยนแปลงนั้นจะหายไปไป
   - ควรแก้ไขที่ Deployment และ apply การเปลี่ยนแปลง   - ควรแก้ไขที่ Deployment และ apply การเปลี่ยนแปลง   - ช่วยในการจัดระเบียบ, การค้นหา, และการอ้างถึงกลุ่มของ pods

2. **ไม่กำหนด Resource Limits**
   - อาจทำให้ Pod ใช้ทรัพยากรมากเกินไปจนกระทบกับ Pods อื่น
   - อาจถูก kill โดยระบบเมื่อ node มีทรัพยากรไม่เพียงพอ (OOMKilled)   - อาจถูก kill โดยระบบเมื่อ node มีทรัพยากรไม่เพียงพอ (OOMKilled)   - ทำให้สามารถย้อนกลับไปยังเวอร์ชันที่ทำงานได้ถ้าเกิดปัญหา

3. **ละเลย Readiness Probes**
   - อาจทำให้ traffic ถูกส่งไปยัง Pod ที่ยังไม่พร้อมให้บริการ
   - ก่อให้เกิดความล้มเหลวในการตอบสนองต่อผู้ใช้
1. **การแก้ไข Pods โดยตรง**
4. **Update หลายการเปลี่ยนแปลงพร้อมกัน**น**อ Pod ถูกสร้างใหม่ การเปลี่ยนแปลงนั้นจะหายไป
   - เมื่อเกิดปัญหา จะยากในการระบุว่าการเปลี่ยนแปลงใดเป็นสาเหตุเกิดปัญหา จะยากในการระบุว่าการเปลี่ยนแปลงใดเป็นสาเหตุ้ไขที่ Deployment และ apply การเปลี่ยนแปลง
   - ควรอัปเดตทีละส่วน เช่น อัปเดต image ก่อน แล้วค่อยเปลี่ยนแปลง configurationส่วน เช่น อัปเดต image ก่อน แล้วค่อยเปลี่ยนแปลง configuration
imits**
5. **ไม่ทดสอบการ Rollback**llback**ช้ทรัพยากรมากเกินไปจนกระทบกับ Pods อื่น
   - ควรมั่นใจว่า rollback สามารถทำได้จริงในกรณีฉุกเฉินวรมั่นใจว่า rollback สามารถทำได้จริงในกรณีฉุกเฉินาจถูก kill โดยระบบเมื่อ node มีทรัพยากรไม่เพียงพอ (OOMKilled)
   - ทดสอบกระบวนการ rollback เป็นประจำ เพื่อให้มั่นใจว่าสามารถกู้คืนระบบได้รวดเร็วามารถกู้คืนระบบได้รวดเร็ว

6. **ใช้ Latest Tag**6. **ใช้ Latest Tag**   - อาจทำให้ traffic ถูกส่งไปยัง Pod ที่ยังไม่พร้อมให้บริการ
   - `image: myapp:latest` ไม่สามารถติดตามได้ว่าใช้ image จริงๆ เวอร์ชันไหนด้ว่าใช้ image จริงๆ เวอร์ชันไหน้ใช้
   - เมื่อต้องการ rollback จะทำได้ยากเพราะไม่รู้ว่า latest คือเวอร์ชันอะไร   - เมื่อต้องการ rollback จะทำได้ยากเพราะไม่รู้ว่า latest คือเวอร์ชันอะไร
   - ควรใช้ tag ที่ระบุเวอร์ชันชัดเจน เช่น `image: myapp:v1.2.3` หรือ SHA hash้ tag ที่ระบุเวอร์ชันชัดเจน เช่น `image: myapp:v1.2.3` หรือ SHA hashe หลายการเปลี่ยนแปลงพร้อมกัน**
ระบุว่าการเปลี่ยนแปลงใดเป็นสาเหตุ
7. **ละเลยการวางแผน Update Strategy**างแผน Update Strategy**ทีละส่วน เช่น อัปเดต image ก่อน แล้วค่อยเปลี่ยนแปลง configuration
   ```yaml
   # ควรหลีกเลี่ยง
   strategy:
     type: Recreateนระบบได้รวดเร็ว
   ```
   - การใช้ Recreate ทำให้เกิดการหยุดให้บริการ (downtime)การหยุดให้บริการ (downtime)
   - ควรใช้ RollingUpdate ในระบบที่ต้องการความพร้อมใช้งานสูง   - ควรใช้ RollingUpdate ในระบบที่ต้องการความพร้อมใช้งานสูง   - `image: myapp:latest` ไม่สามารถติดตามได้ว่าใช้ image จริงๆ เวอร์ชันไหน

#### แผนภาพกระบวนการ Deployment และ ServiceServiceน เช่น `image: myapp:v1.2.3` หรือ SHA hash

```mermaidy**
sequenceDiagram
    actor User
    participant kubectl
    participant API as API Server
    participant Deploy as Deployment Controller
    participant RS as ReplicaSet Controller้บริการ (downtime)ller
    participant Nodes as Worker Nodes   - ควรใช้ RollingUpdate ในระบบที่ต้องการความพร้อมใช้งานสูง    participant Nodes as Worker Nodes
    participant SVC as Service
ละ Service
    User->>kubectl: kubectl apply -f deployment.yaml
    kubectl->>API: Create Deployment
    API->>Deploy: Notify Deployment creationment creation
    Deploy->>RS: Create ReplicaSet
    RS->>Nodes: Schedule Pods
    Nodes-->>RS: Pods Running
    RS-->>Deploy: ReplicaSet Ready    RS-->>Deploy: ReplicaSet Ready    participant Deploy as Deployment Controller
    Deploy-->>API: Deployment Ready
    API-->>kubectl: Status OK API-->>kubectl: Status OK participant Nodes as Worker Nodes
    kubectl-->>User: Deployment created    kubectl-->>User: Deployment created    participant SVC as Service

    User->>kubectl: kubectl apply -f service.yaml    User->>kubectl: kubectl apply -f service.yaml    User->>kubectl: kubectl apply -f deployment.yaml
    kubectl->>API: Create Serviceectl->>API: Create Serviceectl->>API: Create Deployment
    API->>SVC: Create Servicee Servicetify Deployment creation
    SVC->>Nodes: Set up kube-proxy rulest up kube-proxy ruleseate ReplicaSet
    Nodes-->>SVC: Rules Applied: Rules AppliedSchedule Pods
    SVC-->>API: Service Ready>>API: Service Ready-->>RS: Pods Running
    API-->>kubectl: Status OKus OKaSet Ready
    kubectl-->>User: Service createdtl-->>User: Service createdy-->>API: Deployment Ready
K
    Note over User,SVC: External traffic can now reach Podsote over User,SVC: External traffic can now reach Podsubectl-->>User: Deployment created
```
bectl apply -f service.yaml
### การสร้าง DeploymentI: Create Serviceloyment
reate Service
```yamlodes: Set up kube-proxy rules
# my-deployment.yamlSVC: Rules Appliednt.yaml
apiVersion: apps/v1I: Service Readypps/v1
kind: Deployment: Status OK
metadata:tl-->>User: Service created
  name: nginx-deployment
  labels:SVC: External traffic can now reach Pods
    app: nginx
spec:
  replicas: 3
  selector:ctor:
    matchLabels:```yaml    matchLabels:
      app: nginxployment.yamlpp: nginx
  template:
    metadata:
      labels:metadata:      labels:
        app: nginxdeploymentginx
    spec:
      containers:
      - name: nginxc:   - name: nginx
        image: nginx:1.14.2  replicas: 3        image: nginx:1.14.2
        ports:
        - containerPort: 80    matchLabels:        - containerPort: 80
```
  template:
```bash
# นำ deployment ไปใช้งาน      labels:# นำ deployment ไปใช้งาน
kubectl apply -f my-deployment.yaml
    spec:
# ตรวจสอบสถานะ
kubectl get deployments
kubectl get pods
```
        - containerPort: 80
### Service คืออะไร?

Service เป็น resource ที่ใช้เพื่อให้แอปพลิเคชันสามารถติดต่อกันได้ และให้บริการกับภายนอกติดต่อกันได้ และให้บริการกับภายนอก

#### บทบาทและความสำคัญของ Service

Service เป็นแบบจำลองที่ให้บริการ API แบบคงที่สำหรับชุดของ Pods ที่มีการเปลี่ยนแปลงตลอดเวลา โดยมีบทบาทสำคัญดังนี้:จำลองที่ให้บริการ API แบบคงที่สำหรับชุดของ Pods ที่มีการเปลี่ยนแปลงตลอดเวลา โดยมีบทบาทสำคัญดังนี้:

1. **Service Discovery** - ทำหน้าที่เป็นระบบค้นหาและตั้งชื่อภายใน Kubernetes clusterละตั้งชื่อภายใน Kubernetes cluster
2. **Load Balancing** - กระจาย traffic ไปยัง Pods หลายตัวที่ทำหน้าที่เดียวกันยัง Pods หลายตัวที่ทำหน้าที่เดียวกัน
3. **เสถียรภาพการเชื่อมต่อ** - ให้ IP address และ DNS name ที่คงที่ แม้ Pods จะถูกสร้างหรือลบ ที่คงที่ แม้ Pods จะถูกสร้างหรือลบ
4. **การเข้าถึงจากภายนอก** - อนุญาตให้ traffic จากภายนอกเข้าถึง Pods ในคลัสเตอร์4. **การเข้าถึงจากภายนอก** - อนุญาตให้ traffic จากภายนอกเข้าถึง Pods ในคลัสเตอร์### Service คืออะไร?

#### ประเภทของ Serviceายนอก

1. **ClusterIP (ค่าเริ่มต้น)**
   - สร้าง IP ภายในคลัสเตอร์ที่ใช้ได้เฉพาะภายในคลัสเตอร์เท่านั้นลัสเตอร์เท่านั้น
   - เหมาะสำหรับการสื่อสารระหว่างแอปพลิเคชันภายในคลัสเตอร์   - เหมาะสำหรับการสื่อสารระหว่างแอปพลิเคชันภายในคลัสเตอร์Service เป็นแบบจำลองที่ให้บริการ API แบบคงที่สำหรับชุดของ Pods ที่มีการเปลี่ยนแปลงตลอดเวลา โดยมีบทบาทสำคัญดังนี้:

2. **NodePort**
   - เปิด port บน nodes ทุกตัวที่มาพร้อมกับ ClusterIPพร้อมกับ ClusterIPfic ไปยัง Pods หลายตัวที่ทำหน้าที่เดียวกัน
   - เข้าถึงได้จากภายนอกผ่าน `<NodeIP>:<NodePort>`DNS name ที่คงที่ แม้ Pods จะถูกสร้างหรือลบ
   - ช่วง port: 30000-32767 (ค่าเริ่มต้น)   - ช่วง port: 30000-32767 (ค่าเริ่มต้น)4. **การเข้าถึงจากภายนอก** - อนุญาตให้ traffic จากภายนอกเข้าถึง Pods ในคลัสเตอร์
   - เหมาะสำหรับสภาพแวดล้อมการพัฒนา หรือการเข้าถึงชั่วคราว้าถึงชั่วคราว
#### ประเภทของ Service
3. **LoadBalancer**
   - สร้าง external load balancer บน cloud providers   - สร้าง external load balancer บน cloud providers1. **ClusterIP (ค่าเริ่มต้น)**
   - จัดสรร IP address ภายนอกที่สามารถเข้าถึงได้จากอินเทอร์เน็ตน
   - รวมความสามารถของ NodePort และ ClusterIPPort และ ClusterIPระหว่างแอปพลิเคชันภายในคลัสเตอร์
   - เหมาะสำหรับการให้บริการในสภาพแวดล้อมการผลิตารผลิต

4. **ExternalName**
   - สร้าง CNAME DNS record ที่ชี้ไปยัง external serviceชี้ไปยัง external serviceNodeIP>:<NodePort>`
   - ไม่มีการ proxy หรือ forwarding   - ไม่มีการ proxy หรือ forwarding   - ช่วง port: 30000-32767 (ค่าเริ่มต้น)
   - ใช้สำหรับการเชื่อมต่อกับบริการภายนอกคลัสเตอร์่อมต่อกับบริการภายนอกคลัสเตอร์แวดล้อมการพัฒนา หรือการเข้าถึงชั่วคราว

#### ตัวอย่างสถานการณ์การทำงานจริงของ Serviceงานจริงของ Service

##### สถานการณ์: แอปพลิเคชันอีคอมเมิร์ซที่มีหลายส่วนประกอบรณ์: แอปพลิเคชันอีคอมเมิร์ซที่มีหลายส่วนประกอบIP address ภายนอกที่สามารถเข้าถึงได้จากอินเทอร์เน็ต
rt และ ClusterIP
สมมติว่าคุณมีแอปพลิเคชันอีคอมเมิร์ซที่แบ่งเป็นส่วนต่างๆ ดังนี้:อมเมิร์ซที่แบ่งเป็นส่วนต่างๆ ดังนี้:รในสภาพแวดล้อมการผลิต
- frontend-service (React)nd-service (React)
- product-service (API สำหรับข้อมูลสินค้า)- product-service (API สำหรับข้อมูลสินค้า)4. **ExternalName**
- cart-service (API สำหรับตะกร้าสินค้า)หรับตะกร้าสินค้า)ecord ที่ชี้ไปยัง external service
- payment-service (API สำหรับการชำระเงิน)
- database-service (PostgreSQL)

**ขั้นตอนการทำงาน:****ขั้นตอนการทำงาน:**#### ตัวอย่างสถานการณ์การทำงานจริงของ Service

1. **การกำหนดค่า Services**
   - ทุก service กำหนด selector ที่ตรงกับ labels ของ pods ที่เกี่ยวข้อง:
     ```yaml     ```yamlสมมติว่าคุณมีแอปพลิเคชันอีคอมเมิร์ซที่แบ่งเป็นส่วนต่างๆ ดังนี้:
     selector:
       app: product-service
     ```

2. **การเริ่มต้นระบบ**- database-service (PostgreSQL)2. **การเริ่มต้นระบบ**
   - เมื่อ Pod ของ product-service ถูกสร้างขึ้น Kubernetes จะลงทะเบียน endpoints ของ pods ที่มี label ตรงกับ selector ของ servicees จะลงทะเบียน endpoints ของ pods ที่มี label ตรงกับ selector ของ service
   - kube-proxy จะสร้าง network rules (iptables หรือ IPVS) บนทุก node เพื่อ route traffic ไปยัง pods ที่เลือก เพื่อ route traffic ไปยัง pods ที่เลือก
   - DNS service ภายใน cluster จะลงทะเบียนชื่อ "product-service" ให้ตรงกับ ClusterIPervice" ให้ตรงกับ ClusterIP

3. **การเรียกใช้งานระหว่าง Services**3. **การเรียกใช้งานระหว่าง Services**   - ทุก service กำหนด selector ที่ตรงกับ labels ของ pods ที่เกี่ยวข้อง:
   - cart-service ต้องการข้อมูลสินค้าจะเรียก HTTP request ไปที่ `http://product-service:8080/api/products`้อมูลสินค้าจะเรียก HTTP request ไปที่ `http://product-service:8080/api/products`
   - การเรียกจะถูกส่งไปยัง IP ของ product-service service ซึ่งจะ route ไปยัง pod ที่พร้อมใช้งานce service ซึ่งจะ route ไปยัง pod ที่พร้อมใช้งาน

4. **การ Scale Up ระหว่างวัน**
   - เมื่อมีผู้ใช้งานมากขึ้น product-service scaling จาก 3 pods เป็น 10 pods   - เมื่อมีผู้ใช้งานมากขึ้น product-service scaling จาก 3 pods เป็น 10 pods
   - Service จะอัปเดท endpoints โดยอัตโนมัติ และกระจาย traffic ไปยัง pods ทั้ง 10 ตัวย traffic ไปยัง pods ทั้ง 10 ตัว
   - การเปลี่ยนแปลงนี้เป็นแบบไร้รอยต่อ ไม่มีการเปลี่ยนแปลง service IP หรือ DNS name   - การเปลี่ยนแปลงนี้เป็นแบบไร้รอยต่อ ไม่มีการเปลี่ยนแปลง service IP หรือ DNS name   - เมื่อ Pod ของ product-service ถูกสร้างขึ้น Kubernetes จะลงทะเบียน endpoints ของ pods ที่มี label ตรงกับ selector ของ service
ptables หรือ IPVS) บนทุก node เพื่อ route traffic ไปยัง pods ที่เลือก
5. **เหตุการณ์ Pod ล้มเหลว**5. **เหตุการณ์ Pod ล้มเหลว**   - DNS service ภายใน cluster จะลงทะเบียนชื่อ "product-service" ให้ตรงกับ ClusterIP
   - หนึ่งใน product-service pods เกิดปัญหาและไม่ผ่าน readiness probeญหาและไม่ผ่าน readiness probe
   - Service จะหยุดส่ง traffic ไปยัง pod นั้นโดยอัตโนมัติce จะหยุดส่ง traffic ไปยัง pod นั้นโดยอัตโนมัติียกใช้งานระหว่าง Services**
   - ขณะที่ deployment สร้าง pod ใหม่ traffic จะถูกส่งไปยัง pods ที่เหลือment สร้าง pod ใหม่ traffic จะถูกส่งไปยัง pods ที่เหลือต้องการข้อมูลสินค้าจะเรียก HTTP request ไปที่ `http://product-service:8080/api/products`
 IP ของ product-service service ซึ่งจะ route ไปยัง pod ที่พร้อมใช้งาน
6. **การเข้าถึงจากภายนอก**ยนอก**
   - frontend-service ถูกกำหนดเป็น LoadBalancervice ถูกกำหนดเป็น LoadBalancer ระหว่างวัน**
   - Cloud provider จัดสรร external IP และตั้งค่า load balancerexternal IP และตั้งค่า load balancerน product-service scaling จาก 3 pods เป็น 10 pods
   - ผู้ใช้สามารถเข้าถึงแอปผ่าน external IP นี้ึงแอปผ่าน external IP นี้endpoints โดยอัตโนมัติ และกระจาย traffic ไปยัง pods ทั้ง 10 ตัว
่ยนแปลงนี้เป็นแบบไร้รอยต่อ ไม่มีการเปลี่ยนแปลง service IP หรือ DNS name
#### แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Service

##### สิ่งที่ควรทำ ✅##### สิ่งที่ควรทำ ✅   - หนึ่งใน product-service pods เกิดปัญหาและไม่ผ่าน readiness probe

1. **ใช้ Readiness Probes อย่างเหมาะสม**
   ```yaml
   readinessProbe:   readinessProbe:6. **การเข้าถึงจากภายนอก**
     httpGet:Balancer
       path: /healthh: /health provider จัดสรร external IP และตั้งค่า load balancer
       port: 8080ามารถเข้าถึงแอปผ่าน external IP นี้ 8080
     initialDelaySeconds: 5
     periodSeconds: 10ี่ดีและควรหลีกเลี่ยงสำหรับ Service 10
   ```
   - Service จะส่ง traffic ไปยัง pods ที่พร้อมให้บริการเท่านั้นสิ่งที่ควรทำ ✅ervice จะส่ง traffic ไปยัง pods ที่พร้อมให้บริการเท่านั้น
   - ช่วยป้องกัน traffic ไปยัง pods ที่กำลังเริ่มต้นหรือมีปัญหา
1. **ใช้ Readiness Probes อย่างเหมาะสม**
2. **ตั้งชื่อ Service อย่างมีความหมาย**
   - ใช้ชื่อที่สื่อความหมายและสอดคล้องกับบทบาท เช่น `auth-service`, `product-api`่อที่สื่อความหมายและสอดคล้องกับบทบาท เช่น `auth-service`, `product-api`ssProbe:
   - หลีกเลี่ยงชื่อที่เปลี่ยนแปลงบ่อย เพราะชื่อ service จะถูกใช้เป็น DNS nameนแปลงบ่อย เพราะชื่อ service จะถูกใช้เป็น DNS name

3. **กำหนดค่า Selector ที่เฉพาะเจาะจง**Selector ที่เฉพาะเจาะจง**080
   ```yaml
   selector:ector:eriodSeconds: 10
     app: myapp
     tier: frontend     tier: frontend   - Service จะส่ง traffic ไปยัง pods ที่พร้อมให้บริการเท่านั้น
     version: v1
   ```
   - selector ที่เฉพาะเจาะจงช่วยให้ไม่เกิดความสับสนในการเชื่อมต่อยให้ไม่เกิดความสับสนในการเชื่อมต่อามหมาย**
ที่สื่อความหมายและสอดคล้องกับบทบาท เช่น `auth-service`, `product-api`
4. **ตั้งค่า Session Affinity เมื่อจำเป็น**
   ```yaml
   sessionAffinity: ClientIP3. **กำหนดค่า Selector ที่เฉพาะเจาะจง**   sessionAffinity: ClientIP
   sessionAffinityConfig:
     clientIP:r:tIP:
       timeoutSeconds: 10800 myappmeoutSeconds: 10800
   ```ontend
   - ใช้เมื่อแอปพลิเคชันต้องการรักษา session กับ client เดิมษา session กับ client เดิม

5. **ใช้ External Traffic Policy อย่างเหมาะสม**มสับสนในการเชื่อมต่อ**
   ```yaml
   externalTrafficPolicy: Local4. **ตั้งค่า Session Affinity เมื่อจำเป็น**   externalTrafficPolicy: Local
   ```
   - `Local`: ส่ง traffic ไปยัง pods บน node เดียวกันเท่านั้น รักษา source IP แต่อาจกระจาย traffic ไม่สม่ำเสมอds บน node เดียวกันเท่านั้น รักษา source IP แต่อาจกระจาย traffic ไม่สม่ำเสมอ
   - `Cluster` (ค่าเริ่มต้น): กระจาย traffic อย่างสม่ำเสมอ แต่อาจไม่รักษา source IPจไม่รักษา source IP
     clientIP:
6. **กำหนด targetPort ให้ชัดเจน**เจน**
   ```yaml   ```yaml   ```
   ports:
   - port: 80
     targetPort: http-web
   ```   ```   ```yaml
   - ใช้ชื่อ port แทนเลข port เพื่อความชัดเจนจน
   - ช่วยให้สามารถเปลี่ยน port ใน container ได้โดยไม่ต้องเปลี่ยน serviceiner ได้โดยไม่ต้องเปลี่ยน service
ffic ไม่สม่ำเสมอ
7. **ใช้ EndpointSlices สำหรับ Service ที่มี Endpoints จำนวนมาก** ที่มี Endpoints จำนวนมาก**raffic อย่างสม่ำเสมอ แต่อาจไม่รักษา source IP
   - เริ่มใช้งานใน Kubernetes 1.17   - เริ่มใช้งานใน Kubernetes 1.17
   - ช่วยเพิ่มประสิทธิภาพและลดเวลาในการอัปเดท endpoints จำนวนมากดท endpoints จำนวนมาก

##### สิ่งที่ควรหลีกเลี่ยง ❌

1. **การเปลี่ยนแปลง Service IP หรือ Port บ่อยๆ**1. **การเปลี่ยนแปลง Service IP หรือ Port บ่อยๆ**     targetPort: http-web
   - แอปพลิเคชันอื่นอาจจดจำ IP ไว้ (hardcode) ทำให้เกิดปัญหาเมื่อมีการเปลี่ยนแปลงhardcode) ทำให้เกิดปัญหาเมื่อมีการเปลี่ยนแปลง
   - ควรใช้ DNS name ของ service แทนการอ้างอิง IP โดยตรง

2. **การใช้ NodePort ในสภาพแวดล้อมการผลิต**2. **การใช้ NodePort ในสภาพแวดล้อมการผลิต**
   - ไม่มีความยืดหยุ่นเท่า LoadBalanceroints จำนวนมาก**
   - ยากในการจัดการเมื่อ nodes มีการเปลี่ยนแปลง
   - ไม่มีการตรวจสอบสุขภาพในระดับ node

3. **วางใจใน kube-proxy mode โดยไม่เข้าใจ**
   - iptables mode: ใช้ random selection แต่มีประสิทธิภาพต่ำกว่าเมื่อมี endpoints จำนวนมากles mode: ใช้ random selection แต่มีประสิทธิภาพต่ำกว่าเมื่อมี endpoints จำนวนมาก
   - IPVS mode: มีประสิทธิภาพสูงกว่าแต่ต้องการโมดูล Linux kernel เพิ่มเติมประสิทธิภาพสูงกว่าแต่ต้องการโมดูล Linux kernel เพิ่มเติมง Service IP หรือ Port บ่อยๆ**
   - ควรทำความเข้าใจกับ mode ที่คลัสเตอร์ของคุณใช้งานอยู่ำความเข้าใจกับ mode ที่คลัสเตอร์ของคุณใช้งานอยู่ลิเคชันอื่นอาจจดจำ IP ไว้ (hardcode) ทำให้เกิดปัญหาเมื่อมีการเปลี่ยนแปลง
ce แทนการอ้างอิง IP โดยตรง
4. **ละเลยการตั้งค่า Health Checks**ตั้งค่า Health Checks**
   - Service จะยังคงส่ง traffic ไปยัง pods ที่มีปัญหาถ้าไม่มี readiness probeังคงส่ง traffic ไปยัง pods ที่มีปัญหาถ้าไม่มี readiness probePort ในสภาพแวดล้อมการผลิต**
   - ควรกำหนด readiness probe เสมอเพื่อให้ service ส่ง traffic อย่างถูกต้องeadiness probe เสมอเพื่อให้ service ส่ง traffic อย่างถูกต้องืดหยุ่นเท่า LoadBalancer
เปลี่ยนแปลง
5. **ไม่คำนึงถึงการจำกัดการเข้าถึง Service**งการจำกัดการเข้าถึง Service**วจสอบสุขภาพในระดับ node
   - ClusterIP services สามารถเข้าถึงได้จากทุก namespace ในคลัสเตอร์lusterIP services สามารถเข้าถึงได้จากทุก namespace ในคลัสเตอร์
   - ใช้ NetworkPolicy เพื่อจำกัดการเข้าถึง services ที่มีความสำคัญ
   - iptables mode: ใช้ random selection แต่มีประสิทธิภาพต่ำกว่าเมื่อมี endpoints จำนวนมาก
6. **ความแออัดของ Service ด้วย multi-port**
   ```yaml
   # ควรหลีกเลี่ยง
   ports:   ports:4. **ละเลยการตั้งค่า Health Checks**
   - name: http่มีปัญหาถ้าไม่มี readiness probe
     port: 80     port: 80   - ควรกำหนด readiness probe เสมอเพื่อให้ service ส่ง traffic อย่างถูกต้อง
   - name: admin
     port: 8080t: 8080คำนึงถึงการจำกัดการเข้าถึง Service**
   - name: metrics
     port: 9090vices ที่มีความสำคัญ
   ```
   - ควรแยก service ตามหน้าที่แทน เช่น web-service, admin-service และ metrics-service*ความแออัดของ Service ด้วย multi-port** ควรแยก service ตามหน้าที่แทน เช่น web-service, admin-service และ metrics-service

7. **ใช้ externalIPs โดยตรงแทนที่จะใช้ Ingress หรือ Service Type LoadBalancer**จะใช้ Ingress หรือ Service Type LoadBalancer**
   - externalIPs ต้องจัดการเองและไม่มีการปรับขนาดอัตโนมัติไม่มีการปรับขนาดอัตโนมัติ
   - ไม่ได้รับประโยชน์จากฟีเจอร์ของ cloud provider เช่น automatic failoverอง cloud provider เช่น automatic failover

#### แผนภาพการทำงานของ Service

```mermaidide: metrics
graph TB
    Client[External Client] --> LoadBalancer[LoadBalancer Service]ent[External Client] --> LoadBalancer[LoadBalancer Service]
    LoadBalancer --> NodePort[NodePort Service]LoadBalancer --> NodePort[NodePort Service] ควรแยก service ตามหน้าที่แทน เช่น web-service, admin-service และ metrics-service
    NodePort --> ClusterIP[ClusterIP Service]Service]
     **ใช้ externalIPs โดยตรงแทนที่จะใช้ Ingress หรือ Service Type LoadBalancer**
    subgraph "Kubernetes Cluster"    subgraph "Kubernetes Cluster"   - externalIPs ต้องจัดการเองและไม่มีการปรับขนาดอัตโนมัติ
        ClusterIP --> Pod1[Pod 1]น์จากฟีเจอร์ของ cloud provider เช่น automatic failover> Pod1[Pod 1]
        ClusterIP --> Pod2[Pod 2]        ClusterIP --> Pod2[Pod 2]
        ClusterIP --> Pod3[Pod 3]
                
        kube[kube-proxy] -.-> iptables[iptables rules] kube[kube-proxy] -.-> iptables[iptables rules]aid
        iptables -.-> ClusterIP-.-> ClusterIP
        Client] --> LoadBalancer[LoadBalancer Service]
        dns[CoreDNS] -.-> ClusterIPcer --> NodePort[NodePort Service]oreDNS] -.-> ClusterIP
    endt --> ClusterIP[ClusterIP Service]
    
    Internal[Internal Client] --> dnsubgraph "Kubernetes Cluster"nternal[Internal Client] --> dns
```sterIP --> Pod1[Pod 1]
rIP --> Pod2[Pod 2]
### Service คืออะไร?ClusterIP --> Pod3[Pod 3]ice คืออะไร?

Service เป็น resource ที่ใช้เพื่อให้แอปพลิเคชันสามารถติดต่อกันได้ และให้บริการกับภายนอกproxy] -.-> iptables[iptables rules]rce ที่ใช้เพื่อให้แอปพลิเคชันสามารถติดต่อกันได้ และให้บริการกับภายนอก
 -.-> ClusterIP
```yaml     yaml
# my-service.yaml        dns[CoreDNS] -.-> ClusterIP# my-service.yaml
apiVersion: v1ion: v1
kind: Service
metadata:> dns
  name: nginx-service```  name: nginx-service
spec:
  selector:
    app: nginx
  ports:Service เป็น resource ที่ใช้เพื่อให้แอปพลิเคชันสามารถติดต่อกันได้ และให้บริการกับภายนอก  ports:
  - port: 80
    targetPort: 80
  type: NodePorty-service.yamlype: NodePort
```apiVersion: v1```

```bashmetadata:```bash
# สร้าง service
kubectl apply -f my-service.yamlpply -f my-service.yaml

# ดูรายละเอียด service
kubectl get services  ports:kubectl get services
kubectl describe service nginx-service
 targetPort: 80
# เข้าถึง service ใน minikube  type: NodePort# เข้าถึง service ใน minikube
minikube service nginx-service
``````

## 📈 การ Scale และ Update แอปพลิเคชัน# สร้าง service## 📈 การ Scale และ Update แอปพลิเคชัน
 apply -f my-service.yaml
### การ Scale แอปพลิเคชัน
```bash
# Scale deployment เป็น 5 replicas
kubectl scale deployment nginx-deployment --replicas=5escribe service nginx-servicecale deployment nginx-deployment --replicas=5

# หรือแก้ไขไฟล์ YAML แล้ว apply ใหม่าถึง service ใน minikubeอแก้ไขไฟล์ YAML แล้ว apply ใหม่
```nginx-service

### Horizontal Pod Autoscaler (HPA)
 แอปพลิเคชัน
HPA จะช่วย scale จำนวน pods อัตโนมัติตามการใช้งานทรัพยากรนมัติตามการใช้งานทรัพยากร
พลิเคชัน
```yaml
# my-hpa.yaml เป็น 5 replicas
apiVersion: autoscaling/v2 deployment nginx-deployment --replicas=5utoscaling/v2
kind: HorizontalPodAutoscaler
metadata:ล์ YAML แล้ว apply ใหม่
  name: nginx-hpa
spec:
  scaleTargetRef: Horizontal Pod Autoscaler (HPA)caleTargetRef:
    apiVersion: apps/v1    apiVersion: apps/v1
    kind: Deployment่วย scale จำนวน pods อัตโนมัติตามการใช้งานทรัพยากรd: Deployment
    name: nginx-deployment
  minReplicas: 2
  maxReplicas: 10y-hpa.yamlaxReplicas: 10
  metrics:apiVersion: autoscaling/v2  metrics:
  - type: Resourceler
    resource:metadata:    resource:
      name: cpu nginx-hpaame: cpu
      target:
        type: Utilization
        averageUtilization: 50    apiVersion: apps/v1        averageUtilization: 50
```

```bash  minReplicas: 2```bash
kubectl apply -f my-hpa.yaml
kubectl get hpa
``` type: Resource
    resource:
### การ Update แอปพลิเคชัน
      target:
```bashlization
# Update image ของ deployment        averageUtilization: 50# Update image ของ deployment
kubectl set image deployment/nginx-deployment nginx=nginx:1.16.1

# ตรวจสอบประวัติการ roll out
kubectl rollout history deployment/nginx-deployment
kubectl get hpa
# Roll back ไปยังเวอร์ชันก่อนหน้าอร์ชันก่อนหน้า
kubectl rollout undo deployment/nginx-deploymentkubectl rollout undo deployment/nginx-deployment
```

## 🌐 การทำ Networking ใน Kubernetess
# Update image ของ deployment
### Service Types

1. **ClusterIP** - เข้าถึงได้เฉพาะภายใน cluster
2. **NodePort** - เปิด port ที่ทุก node สำหรับเข้าถึงจากภายนอก
3. **LoadBalancer** - ใช้ load balancer ของผู้ให้บริการ cloud
4. **ExternalName** - สร้าง CNAME DNS record
kubectl rollout undo deployment/nginx-deployment
### Ingress

Ingress ช่วยจัดการการเข้าถึงจากภายนอกในระดับ HTTP/HTTPS

#### Ingress คืออะไร?

Ingress เป็น Kubernetes resource ที่จัดการการเข้าถึงจากภายนอกไปยัง Services ภายใน cluster โดยทำหน้าที่เป็น layer 7 (HTTP/HTTPS) load balancer และ reverse proxy ช่วยให้สามารถ:การการเข้าถึงจากภายนอกไปยัง Services ภายใน cluster โดยทำหน้าที่เป็น layer 7 (HTTP/HTTPS) load balancer และ reverse proxy ช่วยให้สามารถ: cluster

1. **จัดการ HTTP routing** - กำหนดเส้นทางการเข้าถึง services ตาม URL path หรือ subdomainces ตาม URL path หรือ subdomainloud
2. **SSL/TLS termination** - จัดการการเข้ารหัสและถอดรหัส TLS
3. **Name-based virtual hosting** - ให้บริการหลายโดเมนบน IP เดียว3. **Name-based virtual hosting** - ให้บริการหลายโดเมนบน IP เดียว
4. **Load balancing** - กระจายภาระงานไปยัง services ต่างๆrvices ต่างๆ

#### Ingress Controller คืออะไร?

Ingress เป็นเพียงกฎที่กำหนดว่าควรจัดการ traffic อย่างไร แต่ไม่ได้ทำงานด้วยตัวเอง จำเป็นต้องมี **Ingress Controller** ทำหน้าที่อ่านและทำงานตามกฎที่กำหนด ตัวอย่าง Ingress Controller ที่นิยมใช้:จัดการ traffic อย่างไร แต่ไม่ได้ทำงานด้วยตัวเอง จำเป็นต้องมี **Ingress Controller** ทำหน้าที่อ่านและทำงานตามกฎที่กำหนด ตัวอย่าง Ingress Controller ที่นิยมใช้:

- **NGINX Ingress Controller** - สร้างบน NGINX web serverบน NGINX web serverดการการเข้าถึงจากภายนอกไปยัง Services ภายใน cluster โดยทำหน้าที่เป็น layer 7 (HTTP/HTTPS) load balancer และ reverse proxy ช่วยให้สามารถ:
- **Traefik** - ออกแบบมาเพื่อ microservicesvices
- **HAProxy** - High Availability Proxys ตาม URL path หรือ subdomain
- **Kong** - API Gateway ที่สร้างบน NGINX- **Kong** - API Gateway ที่สร้างบน NGINX2. **SSL/TLS termination** - จัดการการเข้ารหัสและถอดรหัส TLS
- **Istio Ingress** - เป็นส่วนหนึ่งของ Istio service mesh
- **AWS ALB Ingress** - ใช้ Application Load Balancer ของ AWS- **AWS ALB Ingress** - ใช้ Application Load Balancer ของ AWS4. **Load balancing** - กระจายภาระงานไปยัง services ต่างๆ

#### ตัวอย่างสถานการณ์การทำงานจริงของ Ingress#### ตัวอย่างสถานการณ์การทำงานจริงของ Ingress#### Ingress Controller คืออะไร?

สมมติว่าคุณมี microservices หลายตัวที่ให้บริการเป็นส่วนหนึ่งของแอปพลิเคชันเว็บไซต์ อีคอมเมิร์ซ:ณมี microservices หลายตัวที่ให้บริการเป็นส่วนหนึ่งของแอปพลิเคชันเว็บไซต์ อีคอมเมิร์ซ:็นเพียงกฎที่กำหนดว่าควรจัดการ traffic อย่างไร แต่ไม่ได้ทำงานด้วยตัวเอง จำเป็นต้องมี **Ingress Controller** ทำหน้าที่อ่านและทำงานตามกฎที่กำหนด ตัวอย่าง Ingress Controller ที่นิยมใช้:

- `web-frontend` - UI ของเว็บไซต์ - UI ของเว็บไซต์s Controller** - สร้างบน NGINX web server
- `api-products` - API ข้อมูลสินค้าcts` - API ข้อมูลสินค้า* - ออกแบบมาเพื่อ microservices
- `api-orders` - API สำหรับการสั่งซื้อารสั่งซื้อility Proxy
- `api-users` - API สำหรับข้อมูลผู้ใช้PI สำหรับข้อมูลผู้ใช้Gateway ที่สร้างบน NGINX
- `admin-dashboard` - ส่วนจัดการสำหรับผู้ดูแลระบบsh
ess** - ใช้ Application Load Balancer ของ AWS
แต่ละส่วนได้ถูก deploy เป็น Deployment และมี Service เป็นของตัวเอง้ถูก deploy เป็น Deployment และมี Service เป็นของตัวเอง

**สถานการณ์ที่ 1: การตั้งค่าเว็บไซต์อีคอมเมิร์ซด้วย path-based routing**ี่ 1: การตั้งค่าเว็บไซต์อีคอมเมิร์ซด้วย path-based routing**
ายตัวที่ให้บริการเป็นส่วนหนึ่งของแอปพลิเคชันเว็บไซต์ อีคอมเมิร์ซ:
1. **การกำหนดค่า Ingress**:ngress**:
   ```yaml
   apiVersion: networking.k8s.io/v1orking.k8s.io/v1API ข้อมูลสินค้า
   kind: Ingressบการสั่งซื้อ
   metadata:ู้ใช้
     name: ecommerce-ingress-ingress- ส่วนจัดการสำหรับผู้ดูแลระบบ
     annotations:
       nginx.ingress.kubernetes.io/rewrite-target: /ployment และมี Service เป็นของตัวเองs.io/rewrite-target: /
   spec:
     rules:ารตั้งค่าเว็บไซต์อีคอมเมิร์ซด้วย path-based routing**
     - host: shop.example.com
       http:
         paths:
         - path: /.io/v1
           pathType: Prefix
           backend:
             service:e-ingresse:
               name: web-frontendfrontend
               port:.io/rewrite-target: /
                 number: 80
         - path: /api/products
           pathType: Prefixom
           backend:
             service:
               name: api-products-products
               port:
                 number: 8080er: 8080
         - path: /api/orders
           pathType: Prefixend
           backend:   port:ackend:
             service:  number: 80rvice:
               name: api-ordersapi/productse: api-orders
               port:
                 number: 8080mber: 8080
         - path: /api/users/users
           pathType: Prefix
           backend:
             service:80
               name: api-users- path: /api/orders      name: api-users
               port:thType: Prefix  port:
                 number: 8080
     - host: admin.example.com
       http:
         paths:         port:   paths:
         - path: /                 number: 8080         - path: /
           pathType: Prefixsersefix
           backend:
             service:
               name: admin-dashboard
               port:
                 number: 80
     tls:                 number: 8080     tls:
     - hosts:ample.com
       - shop.example.com
       - admin.example.com
       secretName: example-tls-secret
   ```           pathType: Prefix   ```

2. **ขั้นตอนการทำงาน**:             service:2. **ขั้นตอนการทำงาน**:
   - ผู้ใช้เข้าชม `https://shop.example.com`
   - DNS ส่ง traffic ไปยัง public IP ของ Ingress Controller
   - Ingress Controller ตรวจสอบ Host header และพบว่าตรงกับ `shop.example.com`่าตรงกับ `shop.example.com`
   - สำหรับเส้นทาง root path (`/`), traffic ถูกส่งไปยัง `web-frontend` service
   - เมื่อผู้ใช้เข้าถึง `/api/products`, Ingress จะส่ง traffic ไปยัง `api-products` service   - เมื่อผู้ใช้เข้าถึง `/api/products`, Ingress จะส่ง traffic ไปยัง `api-products` service     - hosts:
e.com
3. **การจัดการ TLS**:
   - Ingress ใช้ Secret ชื่อ `example-tls-secret` ที่มีใบรับรอง TLS และ private keyet ชื่อ `example-tls-secret` ที่มีใบรับรอง TLS และ private keyample-tls-secret
   - การเข้ารหัส HTTPS จะถูกจัดการที่ Ingress Controller (TLS termination)หัส HTTPS จะถูกจัดการที่ Ingress Controller (TLS termination)
   - การสื่อสารระหว่าง Ingress Controller และ backend services เป็น HTTP ธรรมดา (ปลอดภัยเพราะอยู่ใน cluster)ระหว่าง Ingress Controller และ backend services เป็น HTTP ธรรมดา (ปลอดภัยเพราะอยู่ใน cluster)

**สถานการณ์ที่ 2: การอัพเดตแบบ Blue-Green Deployment** 2: การอัพเดตแบบ Blue-Green Deployment**าชม `https://shop.example.com`
ss Controller
1. **เมื่อต้องการอัพเดต `api-products` เป็นเวอร์ชันใหม่**:มื่อต้องการอัพเดต `api-products` เป็นเวอร์ชันใหม่**:ngress Controller ตรวจสอบ Host header และพบว่าตรงกับ `shop.example.com`
   - Deploy `api-products-v2` เป็น Service ใหม่- Deploy `api-products-v2` เป็น Service ใหม่- สำหรับเส้นทาง root path (`/`), traffic ถูกส่งไปยัง `web-frontend` service
   - ทดสอบ `api-products-v2` ด้วย internal testingวย internal testingroducts`, Ingress จะส่ง traffic ไปยัง `api-products` service
   - อัพเดต Ingress rule เพื่อเปลี่ยน traffic จาก `api-products` ไปที่ `api-products-v2`:-v2`:

   ```yamlkey
   - path: /api/products   - path: /api/products   - การเข้ารหัส HTTPS จะถูกจัดการที่ Ingress Controller (TLS termination)
     pathType: Prefixรมดา (ปลอดภัยเพราะอยู่ใน cluster)
     backend:     backend:
       service:
         name: api-products-v2
         port:         port:1. **เมื่อต้องการอัพเดต `api-products` เป็นเวอร์ชันใหม่**:
           number: 8080y `api-products-v2` เป็น Service ใหม่ number: 8080
   ```api-products-v2` ด้วย internal testing
   ss rule เพื่อเปลี่ยน traffic จาก `api-products` ไปที่ `api-products-v2`:
2. **การ Rollback ถ้าพบปัญหา**:
   - หากพบปัญหาในเวอร์ชันใหม่ สามารถแก้ไข Ingress เพื่อกลับไปใช้เวอร์ชันเดิมได้ทันที
   - เปลี่ยน backend service กลับเป็น `api-products`ปลี่ยน backend service กลับเป็น `api-products`ath: /api/products
   - ผู้ใช้งานไม่ได้รับผลกระทบจากการ rollback   - ผู้ใช้งานไม่ได้รับผลกระทบจากการ rollback     pathType: Prefix

**สถานการณ์ที่ 3: การจัดการ Traffic แบบ Canary**
         name: api-products-v2
1. **การทดลองฟีเจอร์ใหม่กับผู้ใช้บางส่วน**:
   - ใช้ annotations ของ Ingress Controller เพื่อแบ่ง traffic:   - ใช้ annotations ของ Ingress Controller เพื่อแบ่ง traffic:           number: 8080

   ```yaml   ```yaml   
   metadata:
     annotations:
       nginx.ingress.kubernetes.io/canary: "true"
       nginx.ingress.kubernetes.io/canary-weight: "20"   - ผู้ใช้งานไม่ได้รับผลกระทบจากการ rollback       nginx.ingress.kubernetes.io/canary-weight: "20"
   ```

   - ส่ง 20% ของ traffic ไปยังเวอร์ชันใหม่
   - ค่อยๆ เพิ่มค่า weight เมื่อมั่นใจว่าเวอร์ชันใหม่ทำงานได้ดี   - ค่อยๆ เพิ่มค่า weight เมื่อมั่นใจว่าเวอร์ชันใหม่ทำงานได้ดี1. **การทดลองฟีเจอร์ใหม่กับผู้ใช้บางส่วน**:

#### แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Ingress

##### สิ่งที่ควรทำ ✅รทำ ✅

1. **เลือก Ingress Controller ให้เหมาะสม**
   - พิจารณาความต้องการด้าน performance, ฟีเจอร์, และการรองรับจากทีมงานิจารณาความต้องการด้าน performance, ฟีเจอร์, และการรองรับจากทีมงาน nginx.ingress.kubernetes.io/canary-weight: "20"
   - ใช้ Ingress Controller ที่มาพร้อมกับ cloud provider หากเป็นไปได้ เพื่อการบูรณาการที่ดีกว่า   - ใช้ Ingress Controller ที่มาพร้อมกับ cloud provider หากเป็นไปได้ เพื่อการบูรณาการที่ดีกว่า   ```

2. **วางแผนเส้นทาง URL อย่างรอบคอบ**2. **วางแผนเส้นทาง URL อย่างรอบคอบ**   - ส่ง 20% ของ traffic ไปยังเวอร์ชันใหม่
   - ออกแบบโครงสร้าง URL ที่สมเหตุสมผลและสอดคล้องกับโครงสร้าง microservicesงกับโครงสร้าง microservicesนใหม่ทำงานได้ดี
   - ใช้ path prefixes ที่ชัดเจน เช่น `/api/v1/` สำหรับ API เวอร์ชัน 1   - ใช้ path prefixes ที่ชัดเจน เช่น `/api/v1/` สำหรับ API เวอร์ชัน 1
บัติที่ดีและควรหลีกเลี่ยงสำหรับ Ingress
3. **ใช้ Annotations เพื่อปรับแต่งพฤติกรรม**เพื่อปรับแต่งพฤติกรรม**
   - Ingress Controllers ส่วนใหญ่มี annotations เฉพาะที่เพิ่มความสามารถ่มี annotations เฉพาะที่เพิ่มความสามารถ
   ```yaml
   annotations:tions:ก Ingress Controller ให้เหมาะสม**
     nginx.ingress.kubernetes.io/proxy-body-size: "10m"ubernetes.io/proxy-body-size: "10m"การด้าน performance, ฟีเจอร์, และการรองรับจากทีมงาน
     nginx.ingress.kubernetes.io/ssl-redirect: "true"nginx.ingress.kubernetes.io/ssl-redirect: "true"ใช้ Ingress Controller ที่มาพร้อมกับ cloud provider หากเป็นไปได้ เพื่อการบูรณาการที่ดีกว่า
   ```
อบ**
### Network Policiesciesร้าง URL ที่สมเหตุสมผลและสอดคล้องกับโครงสร้าง microservices
es ที่ชัดเจน เช่น `/api/v1/` สำหรับ API เวอร์ชัน 1
Network Policies ช่วยควบคุมการติดต่อระหว่าง pods่วยควบคุมการติดต่อระหว่าง pods
ns เพื่อปรับแต่งพฤติกรรม**
```yamllers ส่วนใหญ่มี annotations เฉพาะที่เพิ่มความสามารถ
# network-policy.yaml
apiVersion: networking.k8s.io/v1ions:: networking.k8s.io/v1
kind: NetworkPolicykubernetes.io/proxy-body-size: "10m"
metadata:ress.kubernetes.io/ssl-redirect: "true"
  name: access-nginx```ame: access-nginx
spec:spec:
  podSelector:
    matchLabels:    matchLabels:
      app: nginx
  ingress:  ingress:
  - from:
    - podSelector:# network-policy.yaml    - podSelector:
        matchLabels:ion: networking.k8s.io/v1 matchLabels:
          access: "true"
    ports:
    - protocol: TCP
      port: 800
```:
atchLabels:
## 💾 การจัดการข้อมูลด้วย Persistent Volumesnginxดการข้อมูลด้วย Persistent Volumes

### Persistent Volume (PV) และ Persistent Volume Claim (PVC)me (PV) และ Persistent Volume Claim (PVC)

PV เป็นทรัพยากรเก็บข้อมูลที่ admin จัดเตรียมไว้ และ PVC เป็นคำขอใช้พื้นที่จากผู้ใช้ยากรเก็บข้อมูลที่ admin จัดเตรียมไว้ และ PVC เป็นคำขอใช้พื้นที่จากผู้ใช้chLabels:
ue"
```yaml ports:yaml
# persistent-volume.yaml    - protocol: TCP# persistent-volume.yaml
apiVersion: v1ort: 80ion: v1
kind: PersistentVolume
metadata:
  name: my-pversistent Volumes
spec:
  capacity: Volume (PV) และ Persistent Volume Claim (PVC)
    storage: 1Gie: 1Gi
  accessModes:รเก็บข้อมูลที่ admin จัดเตรียมไว้ และ PVC เป็นคำขอใช้พื้นที่จากผู้ใช้
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"volume.yamlnt/data"
```
d: PersistentVolume
```yamlmetadata:```yaml
# persistent-volume-claim.yaml my-pvstent-volume-claim.yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:    storage: 1Gimetadata:
  name: my-pvc
spec:eOnce
  accessModes:
    - ReadWriteOnce path: "/mnt/data" - ReadWriteOnce
  resources:```  resources:
    requests:
      storage: 500Mi```yaml      storage: 500Mi
```stent-volume-claim.yaml

```bashntVolumeClaim
kubectl apply -f persistent-volume.yamlpply -f persistent-volume.yaml
kubectl apply -f persistent-volume-claim.yamly-pvcpply -f persistent-volume-claim.yaml

# ตรวจสอบ PV และ PVCessModes:จสอบ PV และ PVC
kubectl get pvteOncev
kubectl get pvc
```
0Mi
### การใช้ PVC กับ Pod

```yaml
# pod-with-pvc.yamlsistent-volume.yaml
apiVersion: v1t-volume-claim.yaml
kind: Pod
metadata:รวจสอบ PV และ PVCadata:
  name: nginx-pvc-podkubectl get pv  name: nginx-pvc-pod
spec:
  containers:```  containers:
  - name: nginx
    image: nginxใช้ PVC กับ Podge: nginx
    volumeMounts:
    - mountPath: "/usr/share/nginx/html"r/share/nginx/html"
      name: nginx-datayamlnx-data
  volumes:n: v1:
  - name: nginx-data
    persistentVolumeClaim:ata:ersistentVolumeClaim:
      claimName: my-pvc
```
ontainers:
### ConfigMaps และ Secrets  - name: nginx### ConfigMaps และ Secrets
nginx
#### ConfigMapumeMounts:nfigMap
```yaml "/usr/share/nginx/html"
# my-configmap.yamlinx-data.yaml
apiVersion: v1
kind: ConfigMap nginx-datafigMap
metadata:eClaim:
  name: app-configame: my-pvcconfig
data:
  database_url: "mysql://db:3306/mydb"
  app_mode: "production"
```
#### ConfigMap
#### Secret
```yaml# my-configmap.yaml```yaml
# my-secret.yaml
apiVersion: v1kind: ConfigMapapiVersion: v1
kind: Secret
metadata:  name: app-configmetadata:
  name: app-secretspp-secrets
type: Opaqueurl: "mysql://db:3306/mydb"e
data:
  username: YWRtaW4=  # base64 encoded "admin"W4=  # base64 encoded "admin"
  password: cGFzc3dvcmQxMjM=  # base64 encoded "password123"dvcmQxMjM=  # base64 encoded "password123"
```

## 🛡️ ความปลอดภัยใน Kubernetes ความปลอดภัยใน Kubernetesecret.yaml

### RBAC (Role-Based Access Control)ntrol)

การควบคุมสิทธิ์การเข้าถึงทรัพยากรใน Kubernetesควบคุมสิทธิ์การเข้าถึงทรัพยากรใน Kubernetesame: app-secrets
type: Opaque
```yaml
# role.yaml=  # base64 encoded "admin"
apiVersion: rbac.authorization.k8s.io/v1ncoded "password123"
kind: Role
metadata:
  namespace: defaultยใน Kubernetesult
  name: pod-reader
rules:(Role-Based Access Control)
- apiGroups: [""]
  resources: ["pods"]ธิ์การเข้าถึงทรัพยากรใน Kubernetes ["pods"]
  verbs: ["get", "watch", "list"]
```

```yamluthorization.k8s.io/v1
# role-binding.yaml
apiVersion: rbac.authorization.k8s.io/v1adata:Version: rbac.authorization.k8s.io/v1
kind: RoleBinding  namespace: defaultkind: RoleBinding
metadata:
  name: read-podsrules:  name: read-pods
  namespace: defaults: [""]e: default
subjects: ["pods"]
- kind: Userwatch", "list"]
  name: jane
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Rolebinding.yaml Role
  name: pod-readerapiVersion: rbac.authorization.k8s.io/v1  name: pod-reader
  apiGroup: rbac.authorization.k8s.iothorization.k8s.io
```

#### แผนภาพสิทธิ์การเข้าถึงด้วย RBACถึงด้วย RBAC

```mermaid Useraid
flowchart LRme: janechart LR
    subgraph Usersrization.k8s.io
        U1[Admin]
        U2[Developer]
        U3[Operator]
    endhorization.k8s.io

    subgraph Rolesoles
        R1[Cluster Admin] แผนภาพสิทธิ์การเข้าถึงด้วย RBAC    R1[Cluster Admin]
        R2[Namespace Admin]]
        R3[Pod Reader]eader]
        R4[Deployment Manager]loyment Manager]
    endUsers
        U1[Admin]
    subgraph Resourceseloper]esources
        POD[Pods]rator]ds]
        DEP[Deployments]ts]
        SVC[Services]
        SEC[Secrets]Rolesecrets]
        CM[ConfigMaps]    R1[Cluster Admin]    CM[ConfigMaps]
    endespace Admin]
     Reader]
    U1 --> R1loyment Manager]
    U2 --> R2
    U2 --> R4
    U3 --> R3subgraph ResourcesU3 --> R3
    ds]
    R1 --> PODployments]
    R1 --> DEP     SVC[Services] R1 --> DEP
    R1 --> SVC        SEC[Secrets]    R1 --> SVC
    R1 --> SEC
    R1 --> CM    end    R1 --> CM
    
    R2 --> POD    U1 --> R1    R2 --> POD
    R2 --> DEP--> R2--> DEP
    R2 --> SVC
    R2 --> SEC
    R2 --> CM
    > POD
    R3 --> POD
    R4 --> DEP1 --> SVC4 --> DEP
```
 CM
### Pod Security Policies
OD
การกำหนดนโยบายความปลอดภัยสำหรับ Pod
 SVC
```yaml
# pod-security-policy.yamlCMity-policy.yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicyyPolicy
metadata:
  name: restricted
spec:
  privileged: falsey Policiesalse
  seLinux:
    rule: RunAsAnyยบายความปลอดภัยสำหรับ PodRunAsAny
  runAsUser:
    rule: MustRunAsNonRootnRoot
  fsGroup:
    rule: MustRunAsVersion: policy/v1beta1 rule: MustRunAs
    ranges:kind: PodSecurityPolicy    ranges:
    - min: 1000
      max: 2000  name: restricted      max: 2000
  supplementalGroups:
    rule: MustRunAs  privileged: false    rule: MustRunAs
    ranges:
    - min: 1000    rule: RunAsAny    - min: 1000
      max: 2000
  volumes:    rule: MustRunAsNonRoot  volumes:
  - 'configMap'
  - 'emptyDir'MustRunAsDir'
  - 'persistentVolumeClaim':stentVolumeClaim'
```in: 1000

## ☁️ การ Deploy Kubernetes บน Digital Ocean

Digital Ocean Kubernetes (DOKS) เป็นบริการที่ให้เราสามารถสร้าง Kubernetes cluster บน cloud ได้อย่างง่ายดาย ranges:ital Ocean Kubernetes (DOKS) เป็นบริการที่ให้เราสามารถสร้าง Kubernetes cluster บน cloud ได้อย่างง่ายดาย
 1000
### ขั้นตอนการ Setup DOKS
mes:
1. **สร้างบัญชี Digital Ocean** (หากยังไม่มี)ap'ญชี Digital Ocean** (หากยังไม่มี)

2. **ติดตั้ง doctl CLI**ersistentVolumeClaim'ิดตั้ง doctl CLI**
   ```bash   ```bash```
   # Linux
   cd ~Deploy Kubernetes บน Digital Ocean
   wget https://github.com/digitalocean/doctl/releases/download/v1.X.X/doctl-1.X.X-linux-amd64.tar.gzean/doctl/releases/download/v1.X.X/doctl-1.X.X-linux-amd64.tar.gz
   tar xf doctl-1.X.X-linux-amd64.tar.gz.gzริการที่ให้เราสามารถสร้าง Kubernetes cluster บน cloud ได้อย่างง่ายดาย
   sudo mv doctl /usr/local/bino mv doctl /usr/local/bin
      ### ขั้นตอนการ Setup DOKS
   # MacOS
   brew install doctlstall doctlบัญชี Digital Ocean** (หากยังไม่มี)
   
   # Windows
   # ดาวน์โหลด MSI installer จาก GitHub releasesler จาก GitHub releases
   ```

3. **เชื่อมต่อกับ Digital Ocean**   wget https://github.com/digitalocean/doctl/releases/download/v1.X.X/doctl-1.X.X-linux-amd64.tar.gz3. **เชื่อมต่อกับ Digital Ocean**
   ```bash-amd64.tar.gz
   doctl auth init doctl /usr/local/binuth init
   # ป้อน API token จาก Digital Ocean
   ```
w install doctl
4. **สร้าง Kubernetes cluster**   4. **สร้าง Kubernetes cluster**
   ```bash
   doctl kubernetes cluster create my-cluster \   # ดาวน์โหลด MSI installer จาก GitHub releases   doctl kubernetes cluster create my-cluster \
     --region sgp1 \
     --size s-2vcpu-4gb \4gb \
     --count 3
   ```
tl auth init
5. **เชื่อมต่อกับ cluster**   # ป้อน API token จาก Digital Ocean5. **เชื่อมต่อกับ cluster**
   ```bash
   doctl kubernetes cluster kubeconfig save my-clustercluster kubeconfig save my-cluster
   kubectl get nodess cluster**
   ```
tes cluster create my-cluster \
### การ Deploy แอปพลิเคชันบน DOKSn sgp1 \oy แอปพลิเคชันบน DOKS
-4gb \
1. **นำ YAML manifest ไปใช้**ount 3YAML manifest ไปใช้**
   ```bash
   kubectl apply -f my-deployment.yamlyaml
   kubectl apply -f my-service.yamlต่อกับ cluster**apply -f my-service.yaml
   ```
luster kubeconfig save my-cluster
2. **ตั้งค่า Load Balancer****
   ```yamlyaml
   # lb-service.yamlb-service.yaml
   apiVersion: v1ploy แอปพลิเคชันบน DOKSion: v1
   kind: Service
   metadata:ปใช้**
     name: nginx-lb
   spec:ectl apply -f my-deployment.yamlc:
     selector:   kubectl apply -f my-service.yaml     selector:
       app: nginx
     ports:     ports:
     - port: 80
       targetPort: 80   ```yaml       targetPort: 80
     type: LoadBalancer
   ```ion: v1
   
   ```bash
   kubectl apply -f lb-service.yaml  name: nginx-lbkubectl apply -f lb-service.yaml
   kubectl get servicess
   # จะได้ IP address จาก Digital Ocean
   ```    app: nginx```

## 🎓 แนวทางการศึกษาต่อ
 targetPort: 80
เมื่อเรียนรู้พื้นฐานของ Kubernetes แล้ว คุณสามารถศึกษาเพิ่มเติมในหัวข้อต่อไปนี้:     type: LoadBalancerเมื่อเรียนรู้พื้นฐานของ Kubernetes แล้ว คุณสามารถศึกษาเพิ่มเติมในหัวข้อต่อไปนี้:

1. **Helm** - Package Manager สำหรับ Kubernetes1. **Helm** - Package Manager สำหรับ Kubernetes   
   ```bash
   # ติดตั้ง Helm apply -f lb-service.yaml้ง Helm
   curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bashw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bashvices
   n
   # เพิ่ม repoพิ่ม repo
   helm repo add stable https://charts.helm.sh/stable   helm repo add stable https://charts.helm.sh/stable
   
   # ติดตั้ง chart
   helm install my-nginx stable/nginx-ingresss แล้ว คุณสามารถศึกษาเพิ่มเติมในหัวข้อต่อไปนี้:ginx-ingress
   ```

2. **CI/CD กับ Kubernetes** - เช่น ArgoCD, Jenkins, GitHub ActionsbashI/CD กับ Kubernetes** - เช่น ArgoCD, Jenkins, GitHub Actions
   # ติดตั้ง Helm
3. **Service Mesh** - เช่น Istio
   ```bash      ```bash
   # ติดตั้ง Istio
   istioctl install --set profile=demo   helm repo add stable https://charts.helm.sh/stable   istioctl install --set profile=demo
   ```
   # ติดตั้ง chart
4. **การ Monitor และ Observability** - เช่น Prometheus, Grafanaservability** - เช่น Prometheus, Grafanax stable/nginx-ingress
   ```bash   ```   ```bash
   # ติดตั้ง Prometheus ด้วย Helm
   helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
   helm install prometheus prometheus-community/kube-prometheus-stack
   ```
   ```bash
5. **CKA (Certified Kubernetes Administrator)** - การสอบรับรองสำหรับ Kubernetes admin5. **CKA (Certified Kubernetes Administrator)** - การสอบรับรองสำหรับ Kubernetes admin   # ติดตั้ง Istio













- [CNCF Learning Path](https://www.cncf.io/certification/training/) - เส้นทางการเรียนรู้จาก CNCF- [Kubernetes Patterns](https://k8spatterns.io/) - แพทเทิร์นการออกแบบสำหรับ Kubernetes- [Kubernetes The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) - สำหรับเรียนรู้การติดตั้งแบบละเอียด- [Kubernetes Documentation](https://kubernetes.io/docs/home/) - เอกสารอย่างเป็นทางการ### แหล่งข้อมูลที่แนะนำ7. **CKS (Certified Kubernetes Security Specialist)** - การสอบรับรองด้านความปลอดภัยของ Kubernetes6. **CKAD (Certified Kubernetes Application Developer)** - การสอบรับรองสำหรับนักพัฒนาบน Kubernetes












- [CNCF Learning Path](https://www.cncf.io/certification/training/) - เส้นทางการเรียนรู้จาก CNCF- [Kubernetes Patterns](https://k8spatterns.io/) - แพทเทิร์นการออกแบบสำหรับ Kubernetes- [Kubernetes The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) - สำหรับเรียนรู้การติดตั้งแบบละเอียด- [Kubernetes Documentation](https://kubernetes.io/docs/home/) - เอกสารอย่างเป็นทางการ### แหล่งข้อมูลที่แนะนำ7. **CKS (Certified Kubernetes Security Specialist)** - การสอบรับรองด้านความปลอดภัยของ Kubernetes








- [CNCF Learning Path](https://www.cncf.io/certification/training/) - เส้นทางการเรียนรู้จาก CNCF

- [Kubernetes Patterns](https://k8spatterns.io/) - แพทเทิร์นการออกแบบสำหรับ Kubernetes- [Kubernetes The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) - สำหรับเรียนรู้การติดตั้งแบบละเอียด- [Kubernetes Documentation](https://kubernetes.io/docs/home/) - เอกสารอย่างเป็นทางการ### แหล่งข้อมูลที่แนะนำ



7. **CKS (Certified Kubernetes Security Specialist)** - การสอบรับรองด้านความปลอดภัยของ Kubernetes
6. **CKAD (Certified Kubernetes Application Developer)** - การสอบรับรองสำหรับนักพัฒนาบน Kubernetes

5. **CKA (Certified Kubernetes Administrator)** - การสอบรับรองสำหรับ Kubernetes admin   ```

   helm install prometheus prometheus-community/kube-prometheus-stack   helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

   # ติดตั้ง Prometheus ด้วย Helm   ```bash4. **การ Monitor และ Observability** - เช่น Prometheus, Grafana6. **CKAD (Certified Kubernetes Application Developer)** - การสอบรับรองสำหรับนักพัฒนาบน Kubernetes   istioctl install --set profile=demo
   ```