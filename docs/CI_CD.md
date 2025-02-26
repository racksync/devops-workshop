# CI/CD Workshop

## 🔹 1. Introduction to CI/CD

### CI/CD คืออะไร? ทำไมสำคัญ?

**Continuous Integration (CI) และ Continuous Delivery/Deployment (CD)** คือแนวทางในการพัฒนาซอฟต์แวร์ที่ช่วยให้ทีมสามารถส่งมอบการเปลี่ยนแปลงไปยังลูกค้าได้อย่างรวดเร็วและปลอดภัยยิ่งขึ้น

**ทำไมสำคัญ?**
- ลดความเสี่ยงในการ deploy
- ตรวจจับ bug ได้เร็วขึ้น
- เพิ่มความเร็วในการพัฒนาและ delivery
- ลดงานที่ซ้ำซ้อนและเพิ่ม automation
- สร้างความมั่นใจในคุณภาพของโค้ด

### การทำงานของ Continuous Integration (CI)

CI เน้นที่การรวมโค้ดจากนักพัฒนาหลายคนเข้าด้วยกันอย่างสม่ำเสมอ:

1. **การ Commit โค้ดบ่อยๆ**: นักพัฒนาควร push โค้ดไปยังระบบควบคุมเวอร์ชัน (เช่น Git) อย่างสม่ำเสมอ
2. **Automated Build**: ระบบจะสร้าง build โปรเจคโดยอัตโนมัติเมื่อมีการ push โค้ด
3. **Automated Tests**: ทดสอบโค้ดที่ถูก push เข้ามาโดยอัตโนมัติ
4. **Fail Fast**: หากมีปัญหาเกิดขึ้น ระบบจะแจ้งเตือนทีมทันที

```mermaid
graph LR
    A[Developer Commits] --> B[Automated Build]
    B --> C[Automated Tests]
    C --> D{Tests Pass?}
    D -- Yes --> E[Ready for CD]
    D -- No --> F[Notify Team]
```

### การทำงานของ Continuous Deployment (CD)

CD เป็นกระบวนการที่ทำให้มั่นใจว่าซอฟต์แวร์พร้อมจะ deploy ได้ตลอดเวลา:

1. **Continuous Delivery**: การเตรียมโค้ดให้พร้อมสำหรับการ deploy โดยอัตโนมัติ แต่ยังคงต้องอนุมัติการ deploy แบบ manual
2. **Continuous Deployment**: ขั้นตอนถัดไปที่โค้ดจะถูก deploy ไปยัง production โดยอัตโนมัติหากผ่านทุกการทดสอบ

```mermaid
graph LR
    A[CI Passed] --> B[Deploy to Test/Staging]
    B --> C[Automated Integration Tests]
    C --> D{Tests Pass?}
    D -- Yes --> E[Deploy to Production]
    D -- No --> F[Notify Team]
```

### DevOps กับ CI/CD

DevOps เป็นวัฒนธรรมและแนวทางที่เน้นการทำงานร่วมกันระหว่างทีม Development และ Operations:

- CI/CD เป็นเครื่องมือสำคัญในการทำ DevOps
- ช่วยให้ทีมสามารถส่งมอบซอฟต์แวร์ได้อย่างรวดเร็ว มีประสิทธิภาพและคุณภาพ
- สนับสนุนค่านิยมหลักของ DevOps: การทำงานร่วมกัน, automation, การวัดผล, และการแบ่งปัน

## 🔹 2. Overview of CI/CD Platforms

### เปรียบเทียบ CI/CD Platforms ยอดนิยม

| Platform | รูปแบบ | ข้อดี | ข้อเสีย |
|----------|--------|-------|---------|
| **GitHub Actions** | Cloud/Self-hosted | - ใช้งานง่าย<br>- รวมกับ GitHub<br>- Marketplace ใหญ่ | - นำมาใช้ใหม่ๆ เมื่อเทียบกับตัวอื่น |
| **GitLab CI/CD** | Cloud/Self-hosted | - All-in-one platform<br>- Built-in container registry | - UI ซับซ้อน<br>- Self-hosted อาจยุ่งยาก |
| **Jenkins** | Self-hosted | - Customizable<br>- Plugin ecosystem ใหญ่มาก | - ต้องการ maintenance สูง<br>- Setup ยาก |
| **CircleCI** | Cloud/Self-hosted | - ใช้งานง่าย<br>- Orbs (reusable configurations) | - ราคาอาจแพงสำหรับทีมขนาดใหญ่ |
| **Travis CI** | Cloud | - Setup ง่าย<br>- เหมาะกับ open source | - จำกัดความสามารถในการ customize |

### จุดเด่นและข้อเสียของแต่ละแพลตฟอร์ม

**GitHub Actions**
- จุดเด่น: ผสานรวมกับ GitHub อย่างลงตัว, ใช้งานง่าย, Community actions จำนวนมาก
- ข้อเสีย: Debugging อาจทำได้ยาก, ตัวเลือกในการ caching ยังจำกัด

**GitLab CI/CD**
- จุดเด่น: ระบบครบวงจร, Built-in registry, ทำงานได้ดีกับ GitLab repositories
- ข้อเสีย: Learning curve สูง, Documentation อาจไม่ครบถ้วน

**Jenkins**
- จุดเด่น: ปรับแต่งได้สูงมาก, มี plugin มากกว่า 1,500 ตัว, Community ใหญ่
- ข้อเสีย: UI ล้าสมัย, ต้องการ maintenance มาก, ไม่เหมาะกับโปรเจคเล็ก

**CircleCI**
- จุดเด่น: Setup ง่าย, มีฟีเจอร์ dockerization ที่ดี
- ข้อเสีย: ราคาอาจสูงเมื่อมีทีมขนาดใหญ่, ปรับแต่งได้น้อยกว่า Jenkins

**Travis CI**
- จุดเด่น: ใช้งานง่าย, เหมาะสำหรับโปรเจค open source
- ข้อเสีย: ไม่ค่อยยืดหยุ่น, อาจมีข้อจำกัดใน free tier

### ทำไมต้องเลือก GitHub Actions?

1. **Native Integration**: ทำงานร่วมกับ GitHub ได้อย่างลงตัวโดยไม่ต้องใช้บริการจากภายนอก
2. **YAML-based Configuration**: ใช้ไฟล์ YAML ที่อ่านง่ายและเข้าใจได้ง่าย
3. **Community Actions**: มี action มากมายที่พร้อมใช้งานจาก marketplace
4. **Free for Public Repositories**: ฟรีสำหรับ public repositories และมี free minutes สำหรับ private repositories
5. **Matrix Builds**: สร้าง matrix builds เพื่อทดสอบในหลาย environment ได้ง่าย
6. **Self-hosted Runners**: สามารถใช้ runner บนเครื่องของตัวเองได้

## 🔹 3. Getting Started with GitHub Actions

### GitHub Actions คืออะไร?

GitHub Actions เป็นแพลตฟอร์ม CI/CD ที่ช่วยให้คุณสามารถสร้าง workflow automation ของคุณเองได้ภายใน repository ของ GitHub คุณสามารถ:

- ทดสอบและ build โค้ดโดยอัตโนมัติ
- Deploy applications
- Automate different parts ของ development workflow

### คำศัพท์สำคัญ

**1. Workflow**
- ไฟล์ YAML ที่กำหนด automation process
- อยู่ในโฟลเดอร์ `.github/workflows`
- ประกอบด้วย job หนึ่งหรือหลาย job
- ทริกเกอร์ด้วย event เช่น push, pull request

**2. Jobs**
- ชุดของ steps ที่รันบน runner เดียวกัน
- Jobs ต่างๆ จะรันแบบขนานโดยค่าเริ่มต้น
- สามารถกำหนดเงื่อนไขการรันได้ เช่น รันต่อเมื่อ job อื่นสำเร็จ

**3. Steps**
- งานย่อยของแต่ละ job
- สามารถรัน commands, scripts หรือ actions
- แต่ละ step รันแบบ sequential
- แต่ละ step แชร์ข้อมูลกันได้

**4. Actions**
- ชุดคำสั่งที่สามารถนำกลับมาใช้ซ้ำได้
- สามารถสร้างเองหรือใช้จาก GitHub Marketplace
- เช่น `actions/checkout@v2` เพื่อ clone repository

**5. Runners**
- เครื่องที่รัน workflow
- มีทั้ง GitHub-hosted runners และ self-hosted runners
- มีหลาย OS ให้เลือก เช่น Ubuntu, Windows, macOS

### โครงสร้างของไฟล์ .yml

```yaml
name: [ชื่อ Workflow]

on: [event ที่ทริกเกอร์ workflow]

jobs:
  job_id:
    runs-on: [runner]
    steps:
      - name: [ชื่อ step]
        uses: [action]  # หรือ
        run: [command]  # คำสั่ง shell
        env:  # ตัวแปรสภาพแวดล้อม (optional)
          KEY: value
```

### ตัวอย่าง Workflow พื้นฐาน

ตัวอย่างพื้นฐานสำหรับ Node.js project:

```yaml
name: Node.js CI

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    
    strategy:
      matrix:
        node-version: [14.x, 16.x, 18.x]
    
    steps:
      - name: Checkout repository
        uses: actions/checkout@v3
        
      - name: Setup Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v3
        with:
          node-version: ${{ matrix.node-version }}
          cache: 'npm'
          
      - name: Install dependencies
        run: npm ci
        
      - name: Run tests
        run: npm test
        
      - name: Build
        run: npm run build --if-present
```

ตัวอย่าง Workflow สำหรับ Docker:

```yaml
name: Docker Build and Push

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
        
      - name: Set up QEMU
        uses: docker/setup-qemu-action@v2
        
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v2
        
      - name: Login to Docker Hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
          
      - name: Build and push
        uses: docker/build-push-action@v3
        with:
          context: .
          push: true
          tags: user/app:latest
```

ตัวอย่างสำหรับการ Deploy ไปยัง Firebase:

```yaml
name: Firebase Deploy

on:
  push:
    branches: [ main ]

jobs:
  build_and_deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'
          
      - name: Install dependencies
        run: npm ci
        
      - name: Build
        run: npm run build
        
      - name: Deploy to Firebase
        uses: w9jds/firebase-action@master
        with:
          args: deploy --only hosting
        env:
          FIREBASE_TOKEN: ${{ secrets.FIREBASE_TOKEN }}
```

## 🔹 4. Core Concepts in GitHub Actions

### Workflow Structure

GitHub Actions ทำงานตามลำดับดังนี้:

**Event → Jobs → Steps → Actions**

1. **Event**: เหตุการณ์ที่ทริกเกอร์ให้ workflow เริ่มทำงาน
2. **Jobs**: งานที่ต้องทำหลังจากเกิด event (รันแบบขนานโดยปกติ)
3. **Steps**: ขั้นตอนย่อยในแต่ละ job (รันแบบลำดับ)
4. **Actions**: คำสั่งที่ใช้ในแต่ละ step

```mermaid
graph TD
    A[Event] --> B[Job 1]
    A --> C[Job 2]
    A --> D[Job 3]
    B --> B1[Step 1.1]
    B --> B2[Step 1.2]
    B1 --> B1a[Action]
    B1 --> B1b[Command]
    C --> C1[Step 2.1]
    C --> C2[Step 2.2]
```

### Types of Events ที่ Trigger Workflow

1. **push**: เมื่อมีการ push โค้ดเข้า repository
   ```yaml
   on:
     push:
       branches: [ main, dev ]
       paths-ignore: [ 'docs/**', '**.md' ]
   ```

2. **pull_request**: เมื่อมีการสร้างหรืออัปเดต Pull Request
   ```yaml
   on:
     pull_request:
       types: [opened, synchronize, reopened]
       branches: [ main ]
   ```

3. **schedule**: รันตามเวลาที่กำหนดด้วยรูปแบบ cron
   ```yaml
   on:
     schedule:
       - cron: '0 0 * * *'  # รันทุกวันตอนเที่ยงคืน
   ```

4. **workflow_dispatch**: รันด้วยตนเองผ่าน UI หรือ API
   ```yaml
   on:
     workflow_dispatch:
       inputs:
         environment:
           description: 'Environment to deploy to'
           required: true
           default: 'staging'
   ```

5. **repository_dispatch**: รันเมื่อ webhook ภายนอกเรียก API
   ```yaml
   on:
     repository_dispatch:
       types: [deploy]
   ```

### Runners และ Execution Environment

Runners คือเซิร์ฟเวอร์ที่รัน workflow ของคุณ มี 2 ประเภท:

#### GitHub-hosted Runners

- GitHub จัดเตรียมให้พร้อมใช้งาน
- มีหลาย OS ให้เลือก: `ubuntu-latest`, `windows-latest`, `macos-latest`
- มีซอฟต์แวร์ติดตั้งไว้แล้วจำนวนมาก
- ฟรีสำหรับ public repositories และมี quotas สำหรับ private repositories

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    # หรือ
    # runs-on: windows-latest
    # runs-on: macos-latest
```

#### Self-hosted Runners

- คุณติดตั้งและดูแลเอง
- เหมาะสำหรับสภาพแวดล้อมพิเศษหรือต้องการ performance สูง
- สามารถเป็นเครื่องจริง, VM หรือ container

```yaml
jobs:
  build:
    runs-on: self-hosted
    # หรือระบุ labels เพิ่มเติม
    # runs-on: [self-hosted, linux, x64]
```

## 🔹 5. GitHub Actions Marketplace

### ใช้ Actions สำเร็จรูปจาก Marketplace

GitHub Actions Marketplace คือแหล่งรวม actions สำเร็จรูปที่สามารถนำมาใช้ในโปรเจกต์ของคุณได้ทันที โดยส่วนใหญ่:
- พัฒนาโดย GitHub, องค์กรชั้นนำ, หรือชุมชน
- มีวิธีใช้งานและเอกสารประกอบชัดเจน
- มีการอัปเดตสม่ำเสมอ

### วิธีค้นหาและใช้งาน Actions

1. **การค้นหา Actions**:
   - เข้าไปที่ [GitHub Marketplace](https://github.com/marketplace?type=actions)
   - ใช้คำค้นเพื่อหา action ที่ต้องการ
   - อ่านรีวิวและดูจำนวนดาวเพื่อประเมินความนิยม

2. **วิธีเพิ่ม Action ในไฟล์ workflow**:
   ```yaml
   steps:
     - name: ชื่อขั้นตอน
       uses: ชื่อ-action@version
       with:
         parameter-1: value-1
         parameter-2: value-2
   ```

3. **การระบุเวอร์ชัน**:
   - `@v1`: ใช้เวอร์ชันหลักล่าสุด (เช่น v1.x.x)
   - `@v1.2`: ใช้เวอร์ชันรองล่าสุด (เช่น v1.2.x)
   - `@v1.2.3`: ใช้เวอร์ชันแน่นอน
   - `@main`: ใช้จากบรานช์หลัก (อาจไม่เสถียร)
   - `@5a4ac9bb22`: ใช้ commit hash แน่นอน (ปลอดภัยที่สุด)

### ตัวอย่าง Actions ยอดนิยม

#### 1. actions/checkout
ใช้สำหรับโคลน repository ไปยัง runner

```yaml
- name: Checkout code
  uses: actions/checkout@v3
  with:
    # รองรับ 
    fetch-depth: 0  # โคลนประวัติทั้งหมด
    ref: feature-branch  # ระบุ branch หรือ tag
```

#### 2. actions/setup-node
ตั้งค่าสภาพแวดล้อม Node.js

```yaml
- name: Setup Node.js
  uses: actions/setup-node@v3
  with:
    node-version: '16'
    # หรือใช้ version range
    # node-version: '14.x'
    
    cache: 'npm'  # เปิดใช้การแคช npm dependencies
    registry-url: 'https://registry.npmjs.org'  # สำหรับ publish packages
```

#### 3. docker/build-push-action
สร้างและส่ง Docker image ไปยัง registry

```yaml
- name: Build and push Docker image
  uses: docker/build-push-action@v3
  with:
    context: .
    push: true
    tags: |
      username/image:latest
      username/image:v1
    build-args: |
      ARG1=value1
      ARG2=value2
    cache-from: type=registry,ref=username/image:latest
    cache-to: type=inline
```

#### 4. actions/cache
แคชไฟล์เพื่อเร่งความเร็วในการรัน workflow

```yaml
- name: Cache dependencies
  uses: actions/cache@v3
  with:
    path: ~/.npm
    key: ${{ runner.os }}-npm-${{ hashFiles('**/package-lock.json') }}
    restore-keys: |
      ${{ runner.os }}-npm-
```

#### 5. JamesIves/github-pages-deploy-action
สำหรับ deploy เว็บไปยัง GitHub Pages

```yaml
- name: Deploy to GitHub Pages
  uses: JamesIves/github-pages-deploy-action@v4
  with:
    branch: gh-pages
    folder: build
    clean: true
```

## 🔹 6. Secrets, Security & Permissions

### การใช้ Secrets & Environment Variables

Secrets คือตัวแปรที่เข้ารหัสซึ่งใช้เก็บข้อมูลที่มีความอ่อนไหว โดยจะไม่แสดงในล็อก:

#### Environment Variables ทั่วไป

```yaml
jobs:
  example-job:
    runs-on: ubuntu-latest
    env:
      # ตัวแปรระดับ job
      API_URL: https://api.example.com
    
    steps:
      - name: Step with env variable
        env:
          # ตัวแปรระดับ step
          DEBUG_MODE: true
        run: echo $API_URL $DEBUG_MODE
```

#### การเรียกใช้ Secrets

```yaml
jobs:
  publish:
    runs-on: ubuntu-latest
    steps:
      - name: Use secret
        env:
          # เรียกใช้ secret จาก repository settings
          API_TOKEN: ${{ secrets.API_TOKEN }}
        run: |
          echo "Using API token to authenticate"
          curl -H "Authorization: Bearer $API_TOKEN" https://api.example.com
```

### วิธีตั้งค่า Secrets

1. ไปที่ repository ของคุณ > **Settings** > **Secrets and variables** > **Actions**
2. คลิกปุ่ม **New repository secret**
3. ใส่ชื่อ secret (เช่น `API_TOKEN`) และค่า
4. คลิก **Add secret**

![GitHub Secrets UI](https://docs.github.com/assets/cb-34427/mw-1440/images/help/settings/actions-add-secret.webp)

**ประเภทของ Secrets**:
- **Repository secrets**: ใช้ได้เฉพาะ repository หนึ่ง
- **Environment secrets**: ใช้ได้เฉพาะ environment ที่กำหนด
- **Organization secrets**: ใช้ได้ทุก repository ในองค์กร

### การจำกัดสิทธิ์ (GITHUB_TOKEN, Fine-grained permissions)

#### GITHUB_TOKEN

GitHub สร้าง token พิเศษสำหรับแต่ละ workflow run โดยอัตโนมัติ:

```yaml
jobs:
  job1:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - name: Create issue using REST API
        run: |
          curl -X POST \
          -H "Authorization: Bearer ${{ secrets.GITHUB_TOKEN }}" \
          -H "Accept: application/vnd.github.v3+json" \
          https://api.github.com/repos/${{ github.repository }}/issues \
          -d '{"title":"Automated issue"}'
```

#### จำกัดสิทธิ์ของ GITHUB_TOKEN

```yaml
permissions:
  # จำกัดสิทธิ์ทั้งหมด
  contents: read
  issues: write
  pull-requests: write
  # จะมีสิทธิ์เฉพาะ contents:read, issues:write, pull-requests:write เท่านั้น
```

หรือปิดการใช้งานทั้งหมด:
```yaml
permissions: {}  # ไม่มีสิทธิ์ใดๆ
```

### วิธีป้องกันข้อมูลรั่วไหล

1. **อย่าแสดง Secret โดยตรง**:
   ```yaml
   # BAD - secrets จะถูกแสดงในล็อก
   run: echo "My secret is ${{ secrets.MY_SECRET }}"
   
   # GOOD - ไม่แสดง secret ในล็อก
   run: |
     echo "Using secret for authentication..."
     # ใช้ secret โดยไม่แสดง
   ```

2. **จำกัดสิทธิ์**:
   - ใช้หลักการ "least privilege" โดยให้สิทธิ์เท่าที่จำเป็น
   - กำหนด `permissions` อย่างชัดเจน

3. **ระวัง Workflow จาก Pull Request**:
   ```yaml
   # จำกัด secret เมื่อ workflow ถูกเรียกจาก pull request
   if: github.event_name != 'pull_request'
   env:
     TOKEN: ${{ secrets.TOKEN }}
   ```

4. **ใช้ Environment Protection Rules**:
   ```yaml
   jobs:
     deploy:
       runs-on: ubuntu-latest
       environment: production  # สภาพแวดล้อมที่มีการป้องกัน
   ```

5. **ตรวจสอบ Dependencies**:
   - ใช้ `actions/checkout@` ด้วยเวอร์ชันแน่นอน
   - ระวัง action ที่ไม่น่าเชื่อถือ
   - พิจารณาใช้ action hash แทนเวอร์ชัน

**ตัวอย่างการตั้งค่า Environment Protection Rules**:

1. ไปที่ repository > Settings > Environments
2. สร้าง environment ใหม่หรือคลิก environment ที่มีอยู่
3. ตั้งค่า "Required reviewers" เพื่อจำเป็นต้องมีการอนุมัติ
4. จำกัด branches ที่สามารถ deploy ได้

```yaml
name: Deploy to Production

on:
  push:
    branches: [ main ]

jobs:
  deploy:
    runs-on: ubuntu-latest
    environment: production  # ต้องมีการอนุมัติก่อนทำงาน
    steps:
      - uses: actions/checkout@v3
      - name: Deploy
        run: ./deploy.sh
        env:
          DEPLOY_KEY: ${{ secrets.PRODUCTION_DEPLOY_KEY }}
```
