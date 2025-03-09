# 🚢 การสร้างและจัดการระบบแบบ Container Orchestration (Kubernetes)

## 📑 สารบัญ

- [🚢 การสร้างและจัดการระบบแบบ Container Orchestration (Kubernetes)](#-การสร้างและจัดการระบบแบบ-container-orchestration-kubernetes)
  - [📑 สารบัญ](#-สารบัญ)
  - [บทนำ](#บทนำ)
  - [🔰 พื้นฐาน Container และ Kubernetes](#-พื้นฐาน-container-และ-kubernetes)
    - [Container คืออะไร?](#container-คืออะไร)
    - [Kubernetes คืออะไร?](#kubernetes-คืออะไร)
    - [สถาปัตยกรรมของ Kubernetes](#สถาปัตยกรรมของ-kubernetes)
      - [แผนภาพสถาปัตยกรรม Kubernetes](#แผนภาพสถาปัตยกรรม-kubernetes)
  - [⚙️ การเตรียมสภาพแวดล้อมสำหรับ Windows User](#️-การเตรียมสภาพแวดล้อมสำหรับ-windows-user)
  - [🏗️ การติดตั้ง Minikube](#️-การติดตั้ง-minikube)
    - [การติดตั้ง Minikube](#การติดตั้ง-minikube)
      - [Windows](#windows)
      - [MacOS](#macos)
      - [Linux](#linux)
    - [เริ่มใช้งาน Minikube](#เริ่มใช้งาน-minikube)
  - [🚀 เริ่มต้นใช้งาน Kubernetes](#-เริ่มต้นใช้งาน-kubernetes)
    - [การตรวจสอบสถานะของ Cluster](#การตรวจสอบสถานะของ-cluster)
    - [Kubernetes YAML Files](#kubernetes-yaml-files)
    - [การใช้งานคำสั่งพื้นฐาน](#การใช้งานคำสั่งพื้นฐาน)
    - [Pod คืออะไร?](#pod-คืออะไร)
      - [หลักการทำงานของ Pod](#หลักการทำงานของ-pod)
      - [คุณลักษณะเฉพาะของ Pod](#คุณลักษณะเฉพาะของ-pod)
      - [ข้อจำกัดของ Pod](#ข้อจำกัดของ-pod)
      - [ข้อควรระวังในการใช้งาน Pod](#ข้อควรระวังในการใช้งาน-pod)
      - [ตัวอย่าง YAML ของ Pod ที่มี Multiple Containers](#ตัวอย่าง-yaml-ของ-pod-ที่มี-multiple-containers)
  - [🔄 การ Deploy แอปพลิเคชันบน Kubernetes](#-การ-deploy-แอปพลิเคชันบน-kubernetes)
    - [Deployment คืออะไร?](#deployment-คืออะไร)
      - [บทบาทและความสำคัญของ Deployment](#บทบาทและความสำคัญของ-deployment)
      - [ตัวอย่างสถานการณ์การทำงานจริงของ Deployment](#ตัวอย่างสถานการณ์การทำงานจริงของ-deployment)
      - [แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Deployment](#แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ-deployment)
        - [สิ่งที่ควรทำ ✅](#สิ่งที่ควรทำ-)
        - [สิ่งที่ควรหลีกเลี่ยง ❌](#สิ่งที่ควรหลีกเลี่ยง-)
      - [แผนภาพกระบวนการ Deployment และ Service](#แผนภาพกระบวนการ-deployment-และ-service)
    - [การสร้าง Deployment](#การสร้าง-deployment)
    - [Service คืออะไร?](#service-คืออะไร)
      - [บทบาทและความสำคัญของ Service](#บทบาทและความสำคัญของ-service)
      - [ประเภทของ Service](#ประเภทของ-service)
      - [ตัวอย่างสถานการณ์การทำงานจริงของ Service](#ตัวอย่างสถานการณ์การทำงานจริงของ-service)
        - [สถานการณ์: แอปพลิเคชันอีคอมเมิร์ซที่มีหลายส่วนประกอบ](#สถานการณ์-แอปพลิเคชันอีคอมเมิร์ซที่มีหลายส่วนประกอบ)
      - [แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Service](#แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ-service)
        - [สิ่งที่ควรทำ ✅](#สิ่งที่ควรทำ--1)
        - [สิ่งที่ควรหลีกเลี่ยง ❌](#สิ่งที่ควรหลีกเลี่ยง--1)
      - [แผนภาพการทำงานของ Service](#แผนภาพการทำงานของ-service)
    - [Service คืออะไร?](#service-คืออะไร-1)
  - [📈 การ Scale และ Update แอปพลิเคชัน](#-การ-scale-และ-update-แอปพลิเคชัน)
    - [การ Scale แอปพลิเคชัน](#การ-scale-แอปพลิเคชัน)
    - [Horizontal Pod Autoscaler (HPA)](#horizontal-pod-autoscaler-hpa)
    - [การ Update แอปพลิเคชัน](#การ-update-แอปพลิเคชัน)
  - [🌐 การทำ Networking ใน Kubernetes](#-การทำ-networking-ใน-kubernetes)
    - [Service Types](#service-types)
    - [Ingress](#ingress)
      - [Ingress คืออะไร?](#ingress-คืออะไร)
      - [Ingress Controller คืออะไร?](#ingress-controller-คืออะไร)
      - [ตัวอย่างสถานการณ์การทำงานจริงของ Ingress](#ตัวอย่างสถานการณ์การทำงานจริงของ-ingress)
      - [แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Ingress](#แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ-ingress)
        - [สิ่งที่ควรทำ ✅](#สิ่งที่ควรทำ--2)
    - [Network Policies](#network-policies)
  - [💾 การจัดการข้อมูลด้วย Persistent Volumes](#-การจัดการข้อมูลด้วย-persistent-volumes)
    - [Persistent Volume (PV) และ Persistent Volume Claim (PVC)](#persistent-volume-pv-และ-persistent-volume-claim-pvc)
    - [การใช้ PVC กับ Pod](#การใช้-pvc-กับ-pod)
    - [ConfigMaps และ Secrets](#configmaps-และ-secrets)
      - [ConfigMap](#configmap)
      - [Secret](#secret)
  - [🛡️ ความปลอดภัยใน Kubernetes](#️-ความปลอดภัยใน-kubernetes)
    - [RBAC (Role-Based Access Control)](#rbac-role-based-access-control)
      - [แผนภาพสิทธิ์การเข้าถึงด้วย RBAC](#แผนภาพสิทธิ์การเข้าถึงด้วย-rbac)
    - [Pod Security Policies](#pod-security-policies)
  - [☁️ การ Deploy Kubernetes บน Digital Ocean](#️-การ-deploy-kubernetes-บน-digital-ocean)
    - [ขั้นตอนการ Setup DOKS](#ขั้นตอนการ-setup-doks)
    - [การ Deploy แอปพลิเคชันบน DOKS](#การ-deploy-แอปพลิเคชันบน-doks)
  - [🎓 แนวทางการศึกษาต่อ](#-แนวทางการศึกษาต่อ)
    - [แหล่งข้อมูลที่แนะนำ](#แหล่งข้อมูลที่แนะนำ)

## บทนำ

Container Orchestration คือการจัดการ containers จำนวนมากให้สามารถทำงานร่วมกันได้อย่างมีประสิทธิภาพ Kubernetes (K8s) เป็นระบบ container orchestration ที่ได้รับความนิยมมากที่สุดในปัจจุบัน เราจะเรียนรู้ตั้งแต่พื้นฐานไปจนถึงการ deploy บน cloud provider อย่าง Digital Ocean

## 🔰 พื้นฐาน Container และ Kubernetes

### Container คืออะไร?

Container เป็นหน่วยของซอฟต์แวร์ที่แพ็กโค้ดและส่วนประกอบทั้งหมดที่จำเป็นเพื่อให้แอปพลิเคชันทำงานได้ในทุกสภาพแวดล้อม ต่างจาก VM ตรงที่ container ใช้ทรัพยากรน้อยกว่า และทำงานบน OS kernel เดียวกัน

### Kubernetes คืออะไร?

Kubernetes เป็นแพลตฟอร์มโอเพนซอร์สที่ออกแบบมาเพื่อจัดการ container จำนวนมากโดยอัตโนมัติ ไม่ว่าจะเป็นการ deploy, การปรับขนาด และการจัดการ

### สถาปัตยกรรมของ Kubernetes

Kubernetes ประกอบด้วยองค์ประกอบหลักดังนี้:

1. **Control Plane (Master Node)**:
   - API Server: จุดศูนย์กลางการติดต่อกับ Kubernetes cluster
   - etcd: ฐานข้อมูลแบบ key-value สำหรับเก็บข้อมูลของ cluster
   - Scheduler: ทำการตัดสินใจว่า pod ควรจะทำงานที่ node ไหน
   - Controller Manager: จัดการสถานะของ cluster ให้ตรงกับที่ต้องการ

2. **Worker Nodes**:
   - Kubelet: เอเจนต์ที่ทำงานบนแต่ละ node เพื่อสื่อสารกับ control plane
   - Kube-proxy: จัดการ network rules และการเชื่อมต่อ
   - Container Runtime: เช่น Docker, containerd

3. **Kubernetes Objects**:
   - Pod: หน่วยพื้นฐานที่เล็กที่สุดที่สามารถ deploy บน Kubernetes
   - Service: การเชื่อมต่อระหว่าง Pods และการเข้าถึงจากภายนอก
   - Volume: การจัดการพื้นที่เก็บข้อมูล
   - Namespace: การแบ่งแยกทรัพยากรในคลัสเตอร์

#### แผนภาพสถาปัตยกรรม Kubernetes

```mermaid
flowchart TB
    subgraph "Control Plane (Master Node)"
        API[API Server] --> ETCD[etcd]
        API --> SCH[Scheduler]
        API --> CM[Controller Manager]
    end
    
    subgraph "Worker Node 1"
        KL1[Kubelet] --> CR1[Container Runtime]
        KP1[Kube-proxy]
        subgraph "Pods"
            P1[Pod 1] --> C1[Container 1]
            P1 --> C2[Container 2]
        end
    end
    
    subgraph "Worker Node 2"
        KL2[Kubelet] --> CR2[Container Runtime]
        KP2[Kube-proxy]
        subgraph "Pods"
            P2[Pod 2] --> C3[Container 3]
        end
    end
    
    API --> KL1
    API --> KL2
    CM --> KL1
    CM --> KL2
    SCH --> KL1
    SCH --> KL2
```

## ⚙️ การเตรียมสภาพแวดล้อมสำหรับ Windows User

สำหรับผู้ใช้ Windows จำเป็นต้องเตรียมสภาพแวดล้อมให้พร้อมก่อนเริ่มใช้งาน Kubernetes:

1. **ติดตั้ง Windows Subsystem for Linux (WSL2)** - ทำให้สามารถรัน Linux บน Windows ได้
   ```bash
   # เปิด PowerShell as Administrator แล้วรันคำสั่ง
   wsl --install
   # รีสตาร์ทเครื่อง
   ```

2. **ติดตั้ง Docker Desktop** - ดาวน์โหลดและติดตั้งจาก [docker.com](https://www.docker.com/products/docker-desktop)
   - ตั้งค่า Docker Desktop ให้ใช้งานกับ WSL2

3. **ติดตั้ง kubectl** - เครื่องมือสำหรับควบคุม Kubernetes cluster
   ```bash
   curl -LO "https://dl.k8s.io/release/stable.txt"
   $version = $(Get-Content stable.txt)
   curl -LO "https://dl.k8s.io/release/$version/bin/windows/amd64/kubectl.exe"
   # ย้ายไปไว้ใน PATH
   ```

4. **ติดตั้ง Windows Terminal** - แนะนำให้ใช้งานเพื่อความสะดวก
   - ดาวน์โหลดจาก Microsoft Store

## 🏗️ การติดตั้ง Minikube

Minikube เป็นเครื่องมือที่ช่วยให้รัน Kubernetes แบบ single-node cluster บนเครื่องของเราได้ เหมาะสำหรับการเรียนรู้และพัฒนา

### การติดตั้ง Minikube

#### Windows
```bash
# ดาวน์โหลด installer จาก https://minikube.sigs.k8s.io/docs/start/
# หรือใช้ chocolatey
choco install minikube
```

#### MacOS
```bash
brew install minikube
```

#### Linux
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

### เริ่มใช้งาน Minikube
```bash
# เริ่มต้น Minikube
minikube start --driver=docker

# ตรวจสอบสถานะ
minikube status

# เปิด Kubernetes Dashboard
minikube dashboard
```

## 🚀 เริ่มต้นใช้งาน Kubernetes

เมื่อติดตั้ง Minikube เรียบร้อยแล้ว เราสามารถเริ่มใช้งาน Kubernetes ได้ทันที

### การตรวจสอบสถานะของ Cluster
```bash
# ดูข้อมูลของ cluster
kubectl cluster-info

# ดูรายการ nodes
kubectl get nodes

# ดูรายการ namespace
kubectl get namespaces
```

### Kubernetes YAML Files

การสร้างและจัดการทรัพยากรใน Kubernetes จะใช้ไฟล์ YAML เป็นหลัก ตัวอย่าง:

```yaml
# ตัวอย่าง Pod
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
    - containerPort: 80
```

### การใช้งานคำสั่งพื้นฐาน
```bash
# สร้าง resource จาก YAML
kubectl apply -f my-pod.yaml

# ดูรายการ pods
kubectl get pods

# ดูรายละเอียดของ pod
kubectl describe pod nginx-pod

# เข้าถึง shell ของ pod
kubectl exec -it nginx-pod -- /bin/bash

# ดูบันทึกของ pod
kubectl logs nginx-pod

# ลบ pod
kubectl delete pod nginx-pod
```

### Pod คืออะไร?

Pod เป็นหน่วยพื้นฐานที่เล็กที่สุดที่สามารถ deploy และจัดการได้ใน Kubernetes โดยมีลักษณะสำคัญดังนี้:

#### หลักการทำงานของ Pod

- **กลุ่มของ Containers**: Pod สามารถประกอบด้วย container หนึ่งตัวหรือหลายตัวที่ทำงานร่วมกัน และแชร์ทรัพยากรระหว่างกัน
- **Shared Namespace**: Containers ในแต่ละ Pod จะแชร์ network namespace, IPC namespace และ UTS namespace ทำให้สามารถสื่อสารกันผ่าน localhost ได้
- **Atomic Unit**: ไม่สามารถแยก deploy containers ในแต่ละ Pod ได้ ทุก container จะถูก schedule ไปยัง node เดียวกันและทำงานหรือล้มเหลวไปพร้อมกัน

#### คุณลักษณะเฉพาะของ Pod

1. **Ephemeral (ชั่วคราว)**: Pods ถูกออกแบบให้เป็นหน่วยแบบใช้แล้วทิ้ง ไม่ควรคาดหวังว่า Pod จะมีอายุยาวนาน
2. **Storage Volume**: สามารถกำหนด volumes ที่จะแชร์ระหว่าง containers ในแต่ละ Pod ได้
3. **Init Containers**: สามารถกำหนด containers พิเศษที่จะทำงานและเสร็จสิ้นก่อนที่ containers หลักจะเริ่มทำงาน
4. **Quality of Service (QoS)**: มีการจัดระดับความสำคัญของการใช้ทรัพยากรเป็น Guaranteed, Burstable และ BestEffort
5. **Pod Lifecycle**: วงจรชีวิตของ Pod ประกอบด้วยหลายสถานะ เช่น Pending, Running, Succeeded, Failed และ Unknown

#### ข้อจำกัดของ Pod

1. **ไม่มี Self-healing**: หาก Pod ล้มเหลวหรือถูกลบ ระบบจะไม่พยายามสร้างใหม่โดยอัตโนมัติ (ต้องใช้ controllers เช่น Deployment)
2. **ไม่มี Auto-scaling**: ไม่สามารถขยายหรือลด Pod โดยอัตโนมัติได้ด้วยตัวเอง
3. **Node Binding**: เมื่อ Pod ถูกกำหนดให้ทำงานบน node ใดแล้ว จะไม่สามารถย้ายไปยัง node อื่นได้
4. **IP Address**: แต่ละ Pod จะมี IP address เฉพาะ แต่ IP นี้จะเปลี่ยนเมื่อ Pod ถูกสร้างใหม่

#### ข้อควรระวังในการใช้งาน Pod

1. **ไม่ควรสร้าง Pod โดยตรง**: ควรใช้ controllers (เช่น Deployment, StatefulSet, DaemonSet) ในการจัดการ Pod แทน
2. **การออกแบบ Multi-container Pods**: ควรใส่เฉพาะ containers ที่ต้องทำงานร่วมกันอย่างใกล้ชิดเท่านั้น
3. **Resource Request และ Limits**: ควรกำหนด resource requests และ limits ให้กับ containers เพื่อป้องกันการใช้ทรัพยากรมากเกินไป
4. **Health Checks**: ควรกำหนด liveness และ readiness probes เพื่อให้ Kubernetes ตรวจสอบสถานะของ application ได้อย่างถูกต้อง
5. **Pod Affinity/Anti-affinity**: พิจารณาใช้กฎการจัดวาง Pod เพื่อกระจายหรือรวมกลุ่ม Pod ตามความเหมาะสม

#### ตัวอย่าง YAML ของ Pod ที่มี Multiple Containers

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: multi-container-pod
  labels:
    app: web
spec:
  containers:
  - name: web
    image: nginx:1.20
    ports:
    - containerPort: 80
    volumeMounts:
    - name: shared-data
      mountPath: /usr/share/nginx/html
    
  - name: content-generator
    image: alpine:3.14
    command: ["/bin/sh", "-c"]
    args:
    - while true; do
        echo "<h1>เวลาปัจจุบัน: $(date)</h1>" > /content/index.html;
        sleep 10;
      done
    volumeMounts:
    - name: shared-data
      mountPath: /content
      
  volumes:
  - name: shared-data
    emptyDir: {}
```

## 🔄 การ Deploy แอปพลิเคชันบน Kubernetes

การ deploy แอปพลิเคชันบน Kubernetes จะใช้ Deployment เป็นหลัก

### Deployment คืออะไร?

Deployment เป็น resource ที่จัดการชุดของ Pods ที่เหมือนกันหลาย ๆ ตัว มีความสามารถในการ:
- จัดการและอัปเดตแอปพลิเคชันอย่างนุ่มนวล
- Roll back ไปยังเวอร์ชันก่อนหน้าได้
- Scale และ autoscale แอปพลิเคชัน

#### บทบาทและความสำคัญของ Deployment

Deployment เป็นหนึ่งในทรัพยากรหลักที่สำคัญที่สุดใน Kubernetes มีหน้าที่ดังนี้:

1. **จัดการวงจรชีวิตของ Pods** - Deployment จะสร้าง ReplicaSet ซึ่งเป็นตัวควบคุมการสร้างและลบ Pods ตามจำนวนที่กำหนด
2. **รับประกันความพร้อมใช้งาน** - หาก Pod ล้มเหลว Deployment จะสร้าง Pod ใหม่ทดแทนโดยอัตโนมัติ
3. **อัพเดตแบบ Rolling Update** - อัพเดตแอปพลิเคชันทีละส่วนโดยไม่ทำให้เกิดการหยุดให้บริการ
4. **ประวัติการ Deploy** - เก็บประวัติการเปลี่ยนแปลงและสามารถย้อนกลับไปใช้เวอร์ชันก่อนหน้าได้

#### ตัวอย่างสถานการณ์การทำงานจริงของ Deployment

สมมติว่าคุณเป็นผู้ดูแลระบบที่ต้องการ deploy แอปพลิเคชัน web server ให้มีความพร้อมใช้งานสูง:

1. **เริ่มต้น Deployment**:
   - คุณสร้าง Deployment ที่มี 3 replicas ของ nginx
   - Kubernetes จะสร้าง ReplicaSet และ 3 Pods กระจายไปยัง nodes ต่างๆ
   - แอปพลิเคชันของคุณเริ่มทำงานและให้บริการผ่าน Service

2. **ระหว่างวัน**:
   - หนึ่งใน node เกิดปัญหาและล่ม ทำให้ Pod ที่ทำงานบน node นั้นหายไป
   - Deployment ตรวจพบว่ามี Pods ที่ทำงานอยู่น้อยกว่าที่กำหนด (3)
   - Deployment สั่ง ReplicaSet ให้สร้าง Pod ใหม่บน node ที่ยังทำงานได้
   - ระบบกลับมาให้บริการเต็มประสิทธิภาพโดยอัตโนมัติ

3. **การอัปเดตแอปพลิเคชัน**:
   - คุณต้องการอัปเดตจาก nginx 1.14 เป็น nginx 1.15
   - คุณรัน `kubectl set image deployment/nginx-deployment nginx=nginx:1.15`
   - Deployment เริ่มทำ Rolling Update โดย:
     - สร้าง ReplicaSet ใหม่สำหรับเวอร์ชัน 1.15
     - ค่อยๆ ลด Pods ในเวอร์ชันเก่าลง พร้อมๆ กับเพิ่ม Pods ในเวอร์ชันใหม่
     - ตรวจสอบสถานะของ Pods ใหม่ว่าพร้อมให้บริการหรือไม่
     - เมื่อเสร็จสิ้น Pods ทั้งหมดจะเป็นเวอร์ชัน 1.15 และยังคงให้บริการได้ต่อเนื่องระหว่างการอัปเดต

4. **เมื่อพบปัญหา**:
   - หลังอัปเดต พบว่ามีบั๊กในเวอร์ชัน 1.15
   - คุณรัน `kubectl rollout undo deployment/nginx-deployment`
   - Deployment จะย้อนกลับไปใช้เวอร์ชัน 1.14 โดยอัตโนมัติ ด้วยกระบวนการ Rolling Update แบบเดียวกัน

#### แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Deployment

##### สิ่งที่ควรทำ ✅

1. **กำหนดค่า Resource Limits และ Requests**
   ```yaml
   resources:
     requests:
       memory: "64Mi"
       cpu: "250m"
     limits:
       memory: "128Mi"
       cpu: "500m"
   ```
   - ช่วยให้ scheduler สามารถจัดสรรทรัพยากรได้เหมาะสม
   - ป้องกันไม่ให้แอปพลิเคชันใช้ทรัพยากรมากเกินไป

2. **กำหนด Liveness และ Readiness Probes**
   ```yaml
   livenessProbe:
     httpGet:
       path: /health
       port: 8080
     initialDelaySeconds: 30
     periodSeconds: 10
   readinessProbe:
     httpGet:
       path: /ready
       port: 8080
     initialDelaySeconds: 5
     periodSeconds: 5
   ```
   - Liveness probes ตรวจสอบว่าแอปทำงานอยู่หรือไม่ ถ้าไม่จะรีสตาร์ท pod
   - Readiness probes ตรวจสอบว่าแอปพร้อมรับรีเควสหรือยัง

3. **ตั้งค่า RollingUpdate Strategy ให้เหมาะสม**
   ```yaml
   strategy:
     type: RollingUpdate
     rollingUpdate:
       maxSurge: 25%
       maxUnavailable: 25%
   ```
   - กำหนดว่าจะมี pod ใหม่เพิ่มได้มากสุดเท่าไร (maxSurge)
   - กำหนดว่าสามารถมี pod ที่ไม่พร้อมใช้งานได้มากสุดเท่าไร (maxUnavailable)

4. **ใช้ Labels และ Selectors อย่างมีความหมาย**
   ```yaml
   labels:
     app: myapp
     tier: frontend
     version: v1.0.0
     environment: production
   ```
   - ช่วยในการจัดระเบียบ, การค้นหา, และการอ้างถึงกลุ่มของ pods

5. **เก็บ YAML ไว้ใน Version Control**
   - ติดตามการเปลี่ยนแปลงของ configuration
   - ทำให้สามารถย้อนกลับไปยังเวอร์ชันที่ทำงานได้ถ้าเกิดปัญหา
   - สนับสนุนแนวทาง GitOps

##### สิ่งที่ควรหลีกเลี่ยง ❌

1. **การแก้ไข Pods โดยตรง**
   - ไม่ควรแก้ไข Pod โดยตรง เพราะเมื่อ Pod ถูกสร้างใหม่ การเปลี่ยนแปลงนั้นจะหายไป
   - ควรแก้ไขที่ Deployment และ apply การเปลี่ยนแปลง

2. **ไม่กำหนด Resource Limits**
   - อาจทำให้ Pod ใช้ทรัพยากรมากเกินไปจนกระทบกับ Pods อื่น
   - อาจถูก kill โดยระบบเมื่อ node มีทรัพยากรไม่เพียงพอ (OOMKilled)

3. **ละเลย Readiness Probes**
   - อาจทำให้ traffic ถูกส่งไปยัง Pod ที่ยังไม่พร้อมให้บริการ
   - ก่อให้เกิดความล้มเหลวในการตอบสนองต่อผู้ใช้

4. **Update หลายการเปลี่ยนแปลงพร้อมกัน**
   - เมื่อเกิดปัญหา จะยากในการระบุว่าการเปลี่ยนแปลงใดเป็นสาเหตุ
   - ควรอัปเดตทีละส่วน เช่น อัปเดต image ก่อน แล้วค่อยเปลี่ยนแปลง configuration

5. **ไม่ทดสอบการ Rollback**
   - ควรมั่นใจว่า rollback สามารถทำได้จริงในกรณีฉุกเฉิน
   - ทดสอบกระบวนการ rollback เป็นประจำ เพื่อให้มั่นใจว่าสามารถกู้คืนระบบได้รวดเร็ว

6. **ใช้ Latest Tag**
   - `image: myapp:latest` ไม่สามารถติดตามได้ว่าใช้ image จริงๆ เวอร์ชันไหน
   - เมื่อต้องการ rollback จะทำได้ยากเพราะไม่รู้ว่า latest คือเวอร์ชันอะไร
   - ควรใช้ tag ที่ระบุเวอร์ชันชัดเจน เช่น `image: myapp:v1.2.3` หรือ SHA hash

7. **ละเลยการวางแผน Update Strategy**
   ```yaml
   # ควรหลีกเลี่ยง
   strategy:
     type: Recreate
   ```
   - การใช้ Recreate ทำให้เกิดการหยุดให้บริการ (downtime)
   - ควรใช้ RollingUpdate ในระบบที่ต้องการความพร้อมใช้งานสูง

#### แผนภาพกระบวนการ Deployment และ Service

```mermaid
sequenceDiagram
    actor User
    participant kubectl
    participant API as API Server
    participant Deploy as Deployment Controller
    participant RS as ReplicaSet Controller
    participant Nodes as Worker Nodes
    participant SVC as Service

    User->>kubectl: kubectl apply -f deployment.yaml
    kubectl->>API: Create Deployment
    API->>Deploy: Notify Deployment creation
    Deploy->>RS: Create ReplicaSet
    RS->>Nodes: Schedule Pods
    Nodes-->>RS: Pods Running
    RS-->>Deploy: ReplicaSet Ready
    Deploy-->>API: Deployment Ready
    API-->>kubectl: Status OK
    kubectl-->>User: Deployment created

    User->>kubectl: kubectl apply -f service.yaml
    kubectl->>API: Create Service
    API->>SVC: Create Service
    SVC->>Nodes: Set up kube-proxy rules
    Nodes-->>SVC: Rules Applied
    SVC-->>API: Service Ready
    API-->>kubectl: Status OK
    kubectl-->>User: Service created

    Note over User,SVC: External traffic can now reach Pods
```

### การสร้าง Deployment

```yaml
# my-deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

```bash
# นำ deployment ไปใช้งาน
kubectl apply -f my-deployment.yaml

# ตรวจสอบสถานะ
kubectl get deployments
kubectl get pods
```

### Service คืออะไร?

Service เป็น resource ที่ใช้เพื่อให้แอปพลิเคชันสามารถติดต่อกันได้ และให้บริการกับภายนอก

#### บทบาทและความสำคัญของ Service

Service เป็นแบบจำลองที่ให้บริการ API แบบคงที่สำหรับชุดของ Pods ที่มีการเปลี่ยนแปลงตลอดเวลา โดยมีบทบาทสำคัญดังนี้:

1. **Service Discovery** - ทำหน้าที่เป็นระบบค้นหาและตั้งชื่อภายใน Kubernetes cluster
2. **Load Balancing** - กระจาย traffic ไปยัง Pods หลายตัวที่ทำหน้าที่เดียวกัน
3. **เสถียรภาพการเชื่อมต่อ** - ให้ IP address และ DNS name ที่คงที่ แม้ Pods จะถูกสร้างหรือลบ
4. **การเข้าถึงจากภายนอก** - อนุญาตให้ traffic จากภายนอกเข้าถึง Pods ในคลัสเตอร์

#### ประเภทของ Service

1. **ClusterIP (ค่าเริ่มต้น)**
   - สร้าง IP ภายในคลัสเตอร์ที่ใช้ได้เฉพาะภายในคลัสเตอร์เท่านั้น
   - เหมาะสำหรับการสื่อสารระหว่างแอปพลิเคชันภายในคลัสเตอร์

2. **NodePort**
   - เปิด port บน nodes ทุกตัวที่มาพร้อมกับ ClusterIP
   - เข้าถึงได้จากภายนอกผ่าน `<NodeIP>:<NodePort>`
   - ช่วง port: 30000-32767 (ค่าเริ่มต้น)
   - เหมาะสำหรับสภาพแวดล้อมการพัฒนา หรือการเข้าถึงชั่วคราว

3. **LoadBalancer**
   - สร้าง external load balancer บน cloud providers
   - จัดสรร IP address ภายนอกที่สามารถเข้าถึงได้จากอินเทอร์เน็ต
   - รวมความสามารถของ NodePort และ ClusterIP
   - เหมาะสำหรับการให้บริการในสภาพแวดล้อมการผลิต

4. **ExternalName**
   - สร้าง CNAME DNS record ที่ชี้ไปยัง external service
   - ไม่มีการ proxy หรือ forwarding
   - ใช้สำหรับการเชื่อมต่อกับบริการภายนอกคลัสเตอร์

#### ตัวอย่างสถานการณ์การทำงานจริงของ Service

##### สถานการณ์: แอปพลิเคชันอีคอมเมิร์ซที่มีหลายส่วนประกอบ

สมมติว่าคุณมีแอปพลิเคชันอีคอมเมิร์ซที่แบ่งเป็นส่วนต่างๆ ดังนี้:
- frontend-service (React)
- product-service (API สำหรับข้อมูลสินค้า)
- cart-service (API สำหรับตะกร้าสินค้า)
- payment-service (API สำหรับการชำระเงิน)
- database-service (PostgreSQL)

**ขั้นตอนการทำงาน:**

1. **การกำหนดค่า Services**
   - ทุก service กำหนด selector ที่ตรงกับ labels ของ pods ที่เกี่ยวข้อง:
     ```yaml
     selector:
       app: product-service
     ```

2. **การเริ่มต้นระบบ**
   - เมื่อ Pod ของ product-service ถูกสร้างขึ้น Kubernetes จะลงทะเบียน endpoints ของ pods ที่มี label ตรงกับ selector ของ service
   - kube-proxy จะสร้าง network rules (iptables หรือ IPVS) บนทุก node เพื่อ route traffic ไปยัง pods ที่เลือก
   - DNS service ภายใน cluster จะลงทะเบียนชื่อ "product-service" ให้ตรงกับ ClusterIP

3. **การเรียกใช้งานระหว่าง Services**
   - cart-service ต้องการข้อมูลสินค้าจะเรียก HTTP request ไปที่ `http://product-service:8080/api/products`
   - การเรียกจะถูกส่งไปยัง IP ของ product-service service ซึ่งจะ route ไปยัง pod ที่พร้อมใช้งาน

4. **การ Scale Up ระหว่างวัน**
   - เมื่อมีผู้ใช้งานมากขึ้น product-service scaling จาก 3 pods เป็น 10 pods
   - Service จะอัปเดท endpoints โดยอัตโนมัติ และกระจาย traffic ไปยัง pods ทั้ง 10 ตัว
   - การเปลี่ยนแปลงนี้เป็นแบบไร้รอยต่อ ไม่มีการเปลี่ยนแปลง service IP หรือ DNS name

5. **เหตุการณ์ Pod ล้มเหลว**
   - หนึ่งใน product-service pods เกิดปัญหาและไม่ผ่าน readiness probe
   - Service จะหยุดส่ง traffic ไปยัง pod นั้นโดยอัตโนมัติ
   - ขณะที่ deployment สร้าง pod ใหม่ traffic จะถูกส่งไปยัง pods ที่เหลือ

6. **การเข้าถึงจากภายนอก**
   - frontend-service ถูกกำหนดเป็น LoadBalancer
   - Cloud provider จัดสรร external IP และตั้งค่า load balancer
   - ผู้ใช้สามารถเข้าถึงแอปผ่าน external IP นี้

#### แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Service

##### สิ่งที่ควรทำ ✅

1. **ใช้ Readiness Probes อย่างเหมาะสม**
   ```yaml
   readinessProbe:
     httpGet:
       path: /health
       port: 8080
     initialDelaySeconds: 5
     periodSeconds: 10
   ```
   - Service จะส่ง traffic ไปยัง pods ที่พร้อมให้บริการเท่านั้น
   - ช่วยป้องกัน traffic ไปยัง pods ที่กำลังเริ่มต้นหรือมีปัญหา

2. **ตั้งชื่อ Service อย่างมีความหมาย**
   - ใช้ชื่อที่สื่อความหมายและสอดคล้องกับบทบาท เช่น `auth-service`, `product-api`
   - หลีกเลี่ยงชื่อที่เปลี่ยนแปลงบ่อย เพราะชื่อ service จะถูกใช้เป็น DNS name

3. **กำหนดค่า Selector ที่เฉพาะเจาะจง**
   ```yaml
   selector:
     app: myapp
     tier: frontend
     version: v1
   ```
   - selector ที่เฉพาะเจาะจงช่วยให้ไม่เกิดความสับสนในการเชื่อมต่อ

4. **ตั้งค่า Session Affinity เมื่อจำเป็น**
   ```yaml
   sessionAffinity: ClientIP
   sessionAffinityConfig:
     clientIP:
       timeoutSeconds: 10800
   ```
   - ใช้เมื่อแอปพลิเคชันต้องการรักษา session กับ client เดิม

5. **ใช้ External Traffic Policy อย่างเหมาะสม**
   ```yaml
   externalTrafficPolicy: Local
   ```
   - `Local`: ส่ง traffic ไปยัง pods บน node เดียวกันเท่านั้น รักษา source IP แต่อาจกระจาย traffic ไม่สม่ำเสมอ
   - `Cluster` (ค่าเริ่มต้น): กระจาย traffic อย่างสม่ำเสมอ แต่อาจไม่รักษา source IP

6. **กำหนด targetPort ให้ชัดเจน**
   ```yaml
   ports:
   - port: 80
     targetPort: http-web
   ```
   - ใช้ชื่อ port แทนเลข port เพื่อความชัดเจน
   - ช่วยให้สามารถเปลี่ยน port ใน container ได้โดยไม่ต้องเปลี่ยน service

7. **ใช้ EndpointSlices สำหรับ Service ที่มี Endpoints จำนวนมาก**
   - เริ่มใช้งานใน Kubernetes 1.17
   - ช่วยเพิ่มประสิทธิภาพและลดเวลาในการอัปเดท endpoints จำนวนมาก

##### สิ่งที่ควรหลีกเลี่ยง ❌

1. **การเปลี่ยนแปลง Service IP หรือ Port บ่อยๆ**
   - แอปพลิเคชันอื่นอาจจดจำ IP ไว้ (hardcode) ทำให้เกิดปัญหาเมื่อมีการเปลี่ยนแปลง
   - ควรใช้ DNS name ของ service แทนการอ้างอิง IP โดยตรง

2. **การใช้ NodePort ในสภาพแวดล้อมการผลิต**
   - ไม่มีความยืดหยุ่นเท่า LoadBalancer
   - ยากในการจัดการเมื่อ nodes มีการเปลี่ยนแปลง
   - ไม่มีการตรวจสอบสุขภาพในระดับ node

3. **วางใจใน kube-proxy mode โดยไม่เข้าใจ**
   - iptables mode: ใช้ random selection แต่มีประสิทธิภาพต่ำกว่าเมื่อมี endpoints จำนวนมาก
   - IPVS mode: มีประสิทธิภาพสูงกว่าแต่ต้องการโมดูล Linux kernel เพิ่มเติม
   - ควรทำความเข้าใจกับ mode ที่คลัสเตอร์ของคุณใช้งานอยู่

4. **ละเลยการตั้งค่า Health Checks**
   - Service จะยังคงส่ง traffic ไปยัง pods ที่มีปัญหาถ้าไม่มี readiness probe
   - ควรกำหนด readiness probe เสมอเพื่อให้ service ส่ง traffic อย่างถูกต้อง

5. **ไม่คำนึงถึงการจำกัดการเข้าถึง Service**
   - ClusterIP services สามารถเข้าถึงได้จากทุก namespace ในคลัสเตอร์
   - ใช้ NetworkPolicy เพื่อจำกัดการเข้าถึง services ที่มีความสำคัญ

6. **ความแออัดของ Service ด้วย multi-port**
   ```yaml
   # ควรหลีกเลี่ยง
   ports:
   - name: http
     port: 80
   - name: admin
     port: 8080
   - name: metrics
     port: 9090
   ```
   - ควรแยก service ตามหน้าที่แทน เช่น web-service, admin-service และ metrics-service

7. **ใช้ externalIPs โดยตรงแทนที่จะใช้ Ingress หรือ Service Type LoadBalancer**
   - externalIPs ต้องจัดการเองและไม่มีการปรับขนาดอัตโนมัติ
   - ไม่ได้รับประโยชน์จากฟีเจอร์ของ cloud provider เช่น automatic failover

#### แผนภาพการทำงานของ Service

```mermaid
graph TB
    Client[External Client] --> LoadBalancer[LoadBalancer Service]
    LoadBalancer --> NodePort[NodePort Service]
    NodePort --> ClusterIP[ClusterIP Service]
    
    subgraph "Kubernetes Cluster"
        ClusterIP --> Pod1[Pod 1]
        ClusterIP --> Pod2[Pod 2]
        ClusterIP --> Pod3[Pod 3]
        
        kube[kube-proxy] -.-> iptables[iptables rules]
        iptables -.-> ClusterIP
        
        dns[CoreDNS] -.-> ClusterIP
    end
    
    Internal[Internal Client] --> dns
```

### Service คืออะไร?

Service เป็น resource ที่ใช้เพื่อให้แอปพลิเคชันสามารถติดต่อกันได้ และให้บริการกับภายนอก

```yaml
# my-service.yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
  - port: 80
    targetPort: 80
  type: NodePort
```

```bash
# สร้าง service
kubectl apply -f my-service.yaml

# ดูรายละเอียด service
kubectl get services
kubectl describe service nginx-service

# เข้าถึง service ใน minikube
minikube service nginx-service
```

## 📈 การ Scale และ Update แอปพลิเคชัน

### การ Scale แอปพลิเคชัน
```bash
# Scale deployment เป็น 5 replicas
kubectl scale deployment nginx-deployment --replicas=5

# หรือแก้ไขไฟล์ YAML แล้ว apply ใหม่
```

### Horizontal Pod Autoscaler (HPA)

HPA จะช่วย scale จำนวน pods อัตโนมัติตามการใช้งานทรัพยากร

```yaml
# my-hpa.yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: nginx-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: nginx-deployment
  minReplicas: 2
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 50
```

```bash
kubectl apply -f my-hpa.yaml
kubectl get hpa
```

### การ Update แอปพลิเคชัน

```bash
# Update image ของ deployment
kubectl set image deployment/nginx-deployment nginx=nginx:1.16.1

# ตรวจสอบประวัติการ roll out
kubectl rollout history deployment/nginx-deployment

# Roll back ไปยังเวอร์ชันก่อนหน้า
kubectl rollout undo deployment/nginx-deployment
```

## 🌐 การทำ Networking ใน Kubernetes

### Service Types

1. **ClusterIP** - เข้าถึงได้เฉพาะภายใน cluster
2. **NodePort** - เปิด port ที่ทุก node สำหรับเข้าถึงจากภายนอก
3. **LoadBalancer** - ใช้ load balancer ของผู้ให้บริการ cloud
4. **ExternalName** - สร้าง CNAME DNS record

### Ingress

Ingress ช่วยจัดการการเข้าถึงจากภายนอกในระดับ HTTP/HTTPS

#### Ingress คืออะไร?

Ingress เป็น Kubernetes resource ที่จัดการการเข้าถึงจากภายนอกไปยัง Services ภายใน cluster โดยทำหน้าที่เป็น layer 7 (HTTP/HTTPS) load balancer และ reverse proxy ช่วยให้สามารถ:

1. **จัดการ HTTP routing** - กำหนดเส้นทางการเข้าถึง services ตาม URL path หรือ subdomain
2. **SSL/TLS termination** - จัดการการเข้ารหัสและถอดรหัส TLS
3. **Name-based virtual hosting** - ให้บริการหลายโดเมนบน IP เดียว
4. **Load balancing** - กระจายภาระงานไปยัง services ต่างๆ

#### Ingress Controller คืออะไร?

Ingress เป็นเพียงกฎที่กำหนดว่าควรจัดการ traffic อย่างไร แต่ไม่ได้ทำงานด้วยตัวเอง จำเป็นต้องมี **Ingress Controller** ทำหน้าที่อ่านและทำงานตามกฎที่กำหนด ตัวอย่าง Ingress Controller ที่นิยมใช้:

- **NGINX Ingress Controller** - สร้างบน NGINX web server
- **Traefik** - ออกแบบมาเพื่อ microservices
- **HAProxy** - High Availability Proxy
- **Kong** - API Gateway ที่สร้างบน NGINX
- **Istio Ingress** - เป็นส่วนหนึ่งของ Istio service mesh
- **AWS ALB Ingress** - ใช้ Application Load Balancer ของ AWS

#### ตัวอย่างสถานการณ์การทำงานจริงของ Ingress

สมมติว่าคุณมี microservices หลายตัวที่ให้บริการเป็นส่วนหนึ่งของแอปพลิเคชันเว็บไซต์ อีคอมเมิร์ซ:

- `web-frontend` - UI ของเว็บไซต์
- `api-products` - API ข้อมูลสินค้า
- `api-orders` - API สำหรับการสั่งซื้อ
- `api-users` - API สำหรับข้อมูลผู้ใช้
- `admin-dashboard` - ส่วนจัดการสำหรับผู้ดูแลระบบ

แต่ละส่วนได้ถูก deploy เป็น Deployment และมี Service เป็นของตัวเอง

**สถานการณ์ที่ 1: การตั้งค่าเว็บไซต์อีคอมเมิร์ซด้วย path-based routing**

1. **การกำหนดค่า Ingress**:
   ```yaml
   apiVersion: networking.k8s.io/v1
   kind: Ingress
   metadata:
     name: ecommerce-ingress
     annotations:
       nginx.ingress.kubernetes.io/rewrite-target: /
   spec:
     rules:
     - host: shop.example.com
       http:
         paths:
         - path: /
           pathType: Prefix
           backend:
             service:
               name: web-frontend
               port:
                 number: 80
         - path: /api/products
           pathType: Prefix
           backend:
             service:
               name: api-products
               port:
                 number: 8080
         - path: /api/orders
           pathType: Prefix
           backend:
             service:
               name: api-orders
               port:
                 number: 8080
         - path: /api/users
           pathType: Prefix
           backend:
             service:
               name: api-users
               port:
                 number: 8080
     - host: admin.example.com
       http:
         paths:
         - path: /
           pathType: Prefix
           backend:
             service:
               name: admin-dashboard
               port:
                 number: 80
     tls:
     - hosts:
       - shop.example.com
       - admin.example.com
       secretName: example-tls-secret
   ```

2. **ขั้นตอนการทำงาน**:
   - ผู้ใช้เข้าชม `https://shop.example.com`
   - DNS ส่ง traffic ไปยัง public IP ของ Ingress Controller
   - Ingress Controller ตรวจสอบ Host header และพบว่าตรงกับ `shop.example.com`
   - สำหรับเส้นทาง root path (`/`), traffic ถูกส่งไปยัง `web-frontend` service
   - เมื่อผู้ใช้เข้าถึง `/api/products`, Ingress จะส่ง traffic ไปยัง `api-products` service

3. **การจัดการ TLS**:
   - Ingress ใช้ Secret ชื่อ `example-tls-secret` ที่มีใบรับรอง TLS และ private key
   - การเข้ารหัส HTTPS จะถูกจัดการที่ Ingress Controller (TLS termination)
   - การสื่อสารระหว่าง Ingress Controller และ backend services เป็น HTTP ธรรมดา (ปลอดภัยเพราะอยู่ใน cluster)

**สถานการณ์ที่ 2: การอัพเดตแบบ Blue-Green Deployment**

1. **เมื่อต้องการอัพเดต `api-products` เป็นเวอร์ชันใหม่**:
   - Deploy `api-products-v2` เป็น Service ใหม่
   - ทดสอบ `api-products-v2` ด้วย internal testing
   - อัพเดต Ingress rule เพื่อเปลี่ยน traffic จาก `api-products` ไปที่ `api-products-v2`:

   ```yaml
   - path: /api/products
     pathType: Prefix
     backend:
       service:
         name: api-products-v2
         port:
           number: 8080
   ```
   
2. **การ Rollback ถ้าพบปัญหา**:
   - หากพบปัญหาในเวอร์ชันใหม่ สามารถแก้ไข Ingress เพื่อกลับไปใช้เวอร์ชันเดิมได้ทันที
   - เปลี่ยน backend service กลับเป็น `api-products`
   - ผู้ใช้งานไม่ได้รับผลกระทบจากการ rollback

**สถานการณ์ที่ 3: การจัดการ Traffic แบบ Canary**

1. **การทดลองฟีเจอร์ใหม่กับผู้ใช้บางส่วน**:
   - ใช้ annotations ของ Ingress Controller เพื่อแบ่ง traffic:

   ```yaml
   metadata:
     annotations:
       nginx.ingress.kubernetes.io/canary: "true"
       nginx.ingress.kubernetes.io/canary-weight: "20"
   ```

   - ส่ง 20% ของ traffic ไปยังเวอร์ชันใหม่
   - ค่อยๆ เพิ่มค่า weight เมื่อมั่นใจว่าเวอร์ชันใหม่ทำงานได้ดี

#### แนวทางปฏิบัติที่ดีและควรหลีกเลี่ยงสำหรับ Ingress

##### สิ่งที่ควรทำ ✅

1. **เลือก Ingress Controller ให้เหมาะสม**
   - พิจารณาความต้องการด้าน performance, ฟีเจอร์, และการรองรับจากทีมงาน
   - ใช้ Ingress Controller ที่มาพร้อมกับ cloud provider หากเป็นไปได้ เพื่อการบูรณาการที่ดีกว่า

2. **วางแผนเส้นทาง URL อย่างรอบคอบ**
   - ออกแบบโครงสร้าง URL ที่สมเหตุสมผลและสอดคล้องกับโครงสร้าง microservices
   - ใช้ path prefixes ที่ชัดเจน เช่น `/api/v1/` สำหรับ API เวอร์ชัน 1

3. **ใช้ Annotations เพื่อปรับแต่งพฤติกรรม**
   - Ingress Controllers ส่วนใหญ่มี annotations เฉพาะที่เพิ่มความสามารถ
   ```yaml
   annotations:
     nginx.ingress.kubernetes.io/proxy-body-size: "10m"
     nginx.ingress.kubernetes.io/ssl-redirect: "true"
   ```

### Network Policies

Network Policies ช่วยควบคุมการติดต่อระหว่าง pods

```yaml
# network-policy.yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: access-nginx
spec:
  podSelector:
    matchLabels:
      app: nginx
  ingress:
  - from:
    - podSelector:
        matchLabels:
          access: "true"
    ports:
    - protocol: TCP
      port: 80
```

## 💾 การจัดการข้อมูลด้วย Persistent Volumes

### Persistent Volume (PV) และ Persistent Volume Claim (PVC)

PV เป็นทรัพยากรเก็บข้อมูลที่ admin จัดเตรียมไว้ และ PVC เป็นคำขอใช้พื้นที่จากผู้ใช้

```yaml
# persistent-volume.yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: my-pv
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
```

```yaml
# persistent-volume-claim.yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 500Mi
```

```bash
kubectl apply -f persistent-volume.yaml
kubectl apply -f persistent-volume-claim.yaml

# ตรวจสอบ PV และ PVC
kubectl get pv
kubectl get pvc
```

### การใช้ PVC กับ Pod

```yaml
# pod-with-pvc.yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pvc-pod
spec:
  containers:
  - name: nginx
    image: nginx
    volumeMounts:
    - mountPath: "/usr/share/nginx/html"
      name: nginx-data
  volumes:
  - name: nginx-data
    persistentVolumeClaim:
      claimName: my-pvc
```

### ConfigMaps และ Secrets

#### ConfigMap
```yaml
# my-configmap.yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  database_url: "mysql://db:3306/mydb"
  app_mode: "production"
```

#### Secret
```yaml
# my-secret.yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secrets
type: Opaque
data:
  username: YWRtaW4=  # base64 encoded "admin"
  password: cGFzc3dvcmQxMjM=  # base64 encoded "password123"
```

## 🛡️ ความปลอดภัยใน Kubernetes

### RBAC (Role-Based Access Control)

การควบคุมสิทธิ์การเข้าถึงทรัพยากรใน Kubernetes

```yaml
# role.yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
- apiGroups: [""]
  resources: ["pods"]
  verbs: ["get", "watch", "list"]
```

```yaml
# role-binding.yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: read-pods
  namespace: default
subjects:
- kind: User
  name: jane
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
```

#### แผนภาพสิทธิ์การเข้าถึงด้วย RBAC

```mermaid
flowchart LR
    subgraph Users
        U1[Admin]
        U2[Developer]
        U3[Operator]
    end

    subgraph Roles
        R1[Cluster Admin]
        R2[Namespace Admin]
        R3[Pod Reader]
        R4[Deployment Manager]
    end
    
    subgraph Resources
        POD[Pods]
        DEP[Deployments]
        SVC[Services]
        SEC[Secrets]
        CM[ConfigMaps]
    end
    
    U1 --> R1
    U2 --> R2
    U2 --> R4
    U3 --> R3
    
    R1 --> POD
    R1 --> DEP
    R1 --> SVC
    R1 --> SEC
    R1 --> CM
    
    R2 --> POD
    R2 --> DEP
    R2 --> SVC
    R2 --> SEC
    R2 --> CM
    
    R3 --> POD
    R4 --> DEP
```

### Pod Security Policies

การกำหนดนโยบายความปลอดภัยสำหรับ Pod

```yaml
# pod-security-policy.yaml
apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: restricted
spec:
  privileged: false
  seLinux:
    rule: RunAsAny
  runAsUser:
    rule: MustRunAsNonRoot
  fsGroup:
    rule: MustRunAs
    ranges:
    - min: 1000
      max: 2000
  supplementalGroups:
    rule: MustRunAs
    ranges:
    - min: 1000
      max: 2000
  volumes:
  - 'configMap'
  - 'emptyDir'
  - 'persistentVolumeClaim'
```

## ☁️ การ Deploy Kubernetes บน Digital Ocean

Digital Ocean Kubernetes (DOKS) เป็นบริการที่ให้เราสามารถสร้าง Kubernetes cluster บน cloud ได้อย่างง่ายดาย

### ขั้นตอนการ Setup DOKS

1. **สร้างบัญชี Digital Ocean** (หากยังไม่มี)

2. **ติดตั้ง doctl CLI**
   ```bash
   # Linux
   cd ~
   wget https://github.com/digitalocean/doctl/releases/download/v1.X.X/doctl-1.X.X-linux-amd64.tar.gz
   tar xf doctl-1.X.X-linux-amd64.tar.gz
   sudo mv doctl /usr/local/bin
   
   # MacOS
   brew install doctl
   
   # Windows
   # ดาวน์โหลด MSI installer จาก GitHub releases
   ```

3. **เชื่อมต่อกับ Digital Ocean**
   ```bash
   doctl auth init
   # ป้อน API token จาก Digital Ocean
   ```

4. **สร้าง Kubernetes cluster**
   ```bash
   doctl kubernetes cluster create my-cluster \
     --region sgp1 \
     --size s-2vcpu-4gb \
     --count 3
   ```

5. **เชื่อมต่อกับ cluster**
   ```bash
   doctl kubernetes cluster kubeconfig save my-cluster
   kubectl get nodes
   ```

### การ Deploy แอปพลิเคชันบน DOKS

1. **นำ YAML manifest ไปใช้**
   ```bash
   kubectl apply -f my-deployment.yaml
   kubectl apply -f my-service.yaml
   ```

2. **ตั้งค่า Load Balancer**
   ```yaml
   # lb-service.yaml
   apiVersion: v1
   kind: Service
   metadata:
     name: nginx-lb
   spec:
     selector:
       app: nginx
     ports:
     - port: 80
       targetPort: 80
     type: LoadBalancer
   ```
   
   ```bash
   kubectl apply -f lb-service.yaml
   kubectl get services
   # จะได้ IP address จาก Digital Ocean
   ```

## 🎓 แนวทางการศึกษาต่อ

เมื่อเรียนรู้พื้นฐานของ Kubernetes แล้ว คุณสามารถศึกษาเพิ่มเติมในหัวข้อต่อไปนี้:

1. **Helm** - Package Manager สำหรับ Kubernetes
   ```bash
   # ติดตั้ง Helm
   curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
   
   # เพิ่ม repo
   helm repo add stable https://charts.helm.sh/stable
   
   # ติดตั้ง chart
   helm install my-nginx stable/nginx-ingress
   ```

2. **CI/CD กับ Kubernetes** - เช่น ArgoCD, Jenkins, GitHub Actions

3. **Service Mesh** - เช่น Istio
   ```bash
   # ติดตั้ง Istio
   istioctl install --set profile=demo
   ```

4. **การ Monitor และ Observability** - เช่น Prometheus, Grafana
   ```bash
   # ติดตั้ง Prometheus ด้วย Helm
   helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
   helm install prometheus prometheus-community/kube-prometheus-stack
   ```

5. **CKA (Certified Kubernetes Administrator)** - การสอบรับรองสำหรับ Kubernetes admin

6. **CKAD (Certified Kubernetes Application Developer)** - การสอบรับรองสำหรับนักพัฒนาบน Kubernetes

7. **CKS (Certified Kubernetes Security Specialist)** - การสอบรับรองด้านความปลอดภัยของ Kubernetes

### แหล่งข้อมูลที่แนะนำ

- [Kubernetes Documentation](https://kubernetes.io/docs/home/) - เอกสารอย่างเป็นทางการ
- [Kubernetes The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) - สำหรับเรียนรู้การติดตั้งแบบละเอียด
- [Kubernetes Patterns](https://k8spatterns.io/) - แพทเทิร์นการออกแบบสำหรับ Kubernetes
- [CNCF Learning Path](https://www.cncf.io/certification/training/) - เส้นทางการเรียนรู้จาก CNCF

