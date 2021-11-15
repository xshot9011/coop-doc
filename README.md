# find incomplete section <>

# 1. ส่วนนำ

## บทคัดย่อภาษาไทย

ปัจจุบันการพัฒนาซอฟต์แวร์และแอปพลิเคชันต่าง ๆ  ได้มีการนำเทคโนโลยีคอนเทนเนอร์เข้ามาใช้งานร่วมกันเนื่องจากความสามารถในการแก้ปัญหาของรูปแบบการพัฒนาแบบเก่าได้จากการที่เทคโนโลยีคอนเทนเนอร์มีความสามารถในการรองรับการทำงานแบบอัตโนมัติและความไม่ซับซ้อนและง่ายต่อการบริหารจัดการทรัพยากรและสภาพแวดล้อม ทำให้หลายองค์กรได้มีการนำเทคโนโลยีคอนเทนเนอร์เข้ามาใช้งานภายใน ผู้จัดทำได้ทำการออกแบบระบบแจ้งเตือนและตรวจสอบที่สามารถใช้งานคุณลักษณะของเทคโนโลยีคอนเทนเนอร์ที่เหมาะสมและเข้ากันกับระบบเดิมที่มีอยู่ เพื่อให้ระบบ infrastructure นั้นมีความเสถียรจากการแจ้งเตือนก่อนที่จะเกิดปัญหานั้นขึ้น สามารถรักษาตัวเองได้และสามารถขยายขนาดเพื่อรองรับงานในอนาคตที่เพิ่มขึ้นได้

## บทคัดย่อภาษาอังกฤษ

ค่อยทำ

## กิตติกรรมประกาศ

ตามที่ข้าพเจ้า นายเสฎฐวุฒิ ทิพย์กรรภิรมย์ได้เข้ามาปฏิบัติงานสหกิจศึกษา ณ บริษัท ออพซ์ตา (ประเทศไทย) จำกัด ระหว่างวันที่ 1 มิถุนายน 2564 ถึง 30 พฤศจิกายน 2563 ทำให้ข้าพเจ้าได้รับความรู้ความเข้าใจและประสบการณ์มากมายก่ายกองที่ไม่สามารถตีมูลค่าออกมาได้ สำหรับรายงานสหกิจศึกษาฉบับนี้สำเร็จได้ด้วยดี จากความช่วยเหลือและความร่วมมือของหลายฝ่ายดังนี้

1. นายศิวกร ตันติวิริยางกูร Project Manager
2. นายพงษ์ศักดิ์ สงวนวงษ์ DevOps Engineer
3. นายอนุรักษ์ จันนาวัน DevOps Engineer

นอกจากนี้ยังมีบุคคลอื่น ๆ อีกที่ไม่ได้อยู่ในรายชื่อข้างต้นที่่ได้ให้ความกรุณาแนะนำในการจัดทำรายงานสหกิจศึกษาฉบับนี้ ข้าพเจ้าจึงขอขอบพระคุณทุกท่านที่ได้มีส่วนร่วมในการให้ข้อมูลและให้ความเข้าใจเกี่ยวกับวิธีการปฎิบัติงานรวมถึงการจัดทำรายงานฉบับนี้จนสมบูรณ์

# 2. ส่วนเนื้อหา

## บทที่ 1 บทนำ

### 1.1 ความเป็นมาและความสำคัญ

ปัจจุบันการออกแบบสถาปัตยกรรมซอฟต์แวร์แบบ microservice นั้นเป็นที่นิยมเนื่องจากตอบโจทย์ทาง business และ software ได้เป็นอย่างดีโดยการแยก business logic ออกเป็นส่วนของการทำงานต่าง ๆ ที่เรียกว่า service ประกอบกับเทคโนโลยี container platform เช่น kubernetes ที่เข้ามามีส่วนร่วมสำคัญในการพัฒนาระบบ infrastructure ให้มีความเสถียร, สามารถจัดการกับทรัพยากรได้อย่างมีประสิทธิภาพ, มีความสามารถในการทำ self-healing และสามารถขยายขนาดเพื่อรองรับ workload ขนาดมากได้

การนำระบบ monitoring และ alerting เข้ามา เพื่อตรวจสอบและแจ้งเตือน infrastructure ที่รองรับ container platform เช่น Kubernetes สามารถทำให้วิเคราะห์และเข้าใจถึงการใช้ทรัพยากรถึงระดับ containers หรือ pods เพื่อให้เกิดการใช้งาน resource ได้อย่างคุ้มค่า ตลอดจนตัดสินใจในการ scale application ได้อย่างเหมาะสม นอกจากนี้การมีระบบ alerting ที่ทันสมัยจะช่วยแจ้งเตือนเมื่อระบบมีปัญหา ทำให้สามารถแก้ไขปัญหาได้อย่างรวดเร็วและตรงจุด อีกทั้งการใช้ระบบ monitoring และ alerting ที่ทันสมัยนี้ ยังรองรับการทำ integration กับระบบอื่น ๆ ในอนาคตอีกด้วย

### 1.2 วัตถุประสงค์ของการวิจัย

1. เพื่อศึกษาการใช้งานและติดตั้ง Kubernetes ที่รองรับการลง application แบบ container platform
2. เพื่อปรับปรุง infrastructure ให้มีความสามารถในการซ่อมแซมได้อย่างรวดเร็ว (Mean time to recovery)  และมีความน่าเชื่อถือสูง (high avaliability)
3. เพื่อศึกษาการติดตั้งและการทำงานของระบบ monitoring และ alerting ของระบบ
4. เพื่อศึกษาวิธีการออกแบบ Alerting ให้เหมาะสมกับระดับตามความสำคัญต่างๆ(Severity) ได้อย่างเหมาะสม 
5. เพื่อปรับปรุงระบบ monitoring และ alerting ให้เข้ากับ infrastructure ที่มีอยู่

### 1.3 ขอบเขตของการวิจัย

1. ตรวจสอบ, วางแผน และออกแบบระบบ Kubernetes เพือรองรับ high avaliability และ Mean time to recovery ที่ต่ำ
2. ออกแบบระบบเพื่อรองรับการ Monitoring ของ Infrastructure และ Kubernetes
3. ออกแบบระบบเพื่อรองรับการ Monitoring Application ที่ติดตั้งด้วยเทคโนโลยี Container Platform ซึ่งรองรับการติดตั้งใน Kubernetes
4. ออกแบบและติดตั้ง Dashboard ที่รองรับการแสดงผล Metric จากระบบ Monitoring
5. ออกแบบและติดตั้งระบบ Alerting โดยมีการจัดลำดับการแจ้งเตือน (Severity) ที่เหมาะสมรองรับกับ Infrastructure และ Application
6. ตรวจสอบ Alerting ที่ติดตั้ง เพื่อความถูกต้องของระบบแจ้งเตือน

### 1.4 วิธีดำเนินการวิจัย

### 1.5 ประโยชน์ที่คาดว่าจะได้รับ

Infrastructure ที่ได้รับการปรับปรุงให้ทันสมัย พร้อมกับระบบตรวจสอบและแจ้งเตือนปัญหาก่อนที่จะเกิดขึ้น เพื่อให้มีความ high avalability ที่สูงและสามารถรองรับ wokrload ได้เป็นจำนวนมาก
ได้รับระบบ monitoring ที่สามารถใช้งานได้บน kubernetes
สามารถดูสถานะของ application ที่ติดตั้งแบบ container platform ได้พร้อมกับรองรับการขยายเมื่อเพิ่ม application ขึ้นมาในอนาคต
ได้รับ dashboard แสดงถึงค่าสถานะที่สำคัญของระบบ เพื่อใช้ในการวิเคราะห์ข้อมูลการใช้งานเชิงทรัพยากรและการตรวจสอบปัญหาที่เกิดขึ้นภายในระบบ
ระบบ alerting สามารถแจ้งเตือนปัญหาก่อนที่จะเกิดขึ้นได้ โดยสามารถแบ่งตามระดับความรุนแรงของปัญหานั้นในระบบเพื่อให้ระบบสามารถทำงานได้อย่างเสถียรและคนสามารถเตรียมการรับมือแก้ไขกับปัญหาได้ดียิ่งขึ้น
ได้รับระบบ alerting ที่มี false negative น้อยทำให้เมื่อมีการแจ้งเตือนจากระบบ alerting คนจะให้ความสำคัญกับแจ้งเตือนนั้น

## บทที่2 แนวคิด ทฤษฎีและงานวิจัยที่เกี่ยวข้อง

### 2.1 ทฤษฎีที่เกี่ยวข้อง (หลักตามประเด็นให้ครอบคลุมเรื่องที่วิจัย)

- 2.1.1 Container Technology [4]
  - Container
    - What is Virtual Machine (VM) ?
      ```txt
      virtual machine คือเครื่องเสมือนที่ทำหน้าที่เป็น computer เพื่อใช้ในการคำนวณงานต่าง ๆ โดยการใช้เทคโนโลยี 
      virtualization ซึ่งเป็นกระบวนการที่ใช้ในสร้าง virtual computer ด้วย central processing unit (CPU), 
      memory และ disk space ที่ถูกแบ่งมาจากคอมพิวเตอร์ของจริงดังนั้น virtual machine นั้นจึงเปรียบเสมือนกับ 
      virtual computer หรือ software-defined computer ทำให้สามารถแยก environment ของเครื่องออกจากกันได้
      ```
      ![vm](./media/VM.png)
    - What is Container ?
      ```txt
      container คือ เทคโลโลยีที่ใช้ในการแยกและจัดการ environment การทำงานของ application ซึ่งมีความ
      คล้ายคลึงกับแนวคิดของ virtual machine เทคโนโลยี container ทำให้การติดตั้ง application นั้นสามารถ
      ทำในสภาพแวดล้อมแบบไหนก็ได้ขอแค่ให้ OS นั้นสามารถติดตั้ง container engine ได้ก็พอ
      ```
      ![container](./media/container.png)
    - What is the diffent between container and virtual machine ?
      ```txt
      container กับ virtual machine นั้นถูกใช้ใน use case ที่ต่างกันดังนั้นถ้าจะเปรียบเทียบก็จะสมุติกรณีที่่รัน 
      application เดียวกันบนทั้ง 2 เทคโนโลยีนี้
      ```
      - ส่วนของ virtual machine จะมี overhead ของการทำงานของ OS ทำให้กิน memory และ disk เพิ่มขึ้นแต่ใน container นั้นต้องการแค่ binary และ libary ที่เกี่ยวข้องเท่านั้นเพื่อให้ application สามารถทำงานได้
        - การที่จะเคลื่อนย้ายหรือเพิ่มจำนวนของ instance ต่าง ๆ นั้น container สามารถทำได้ดีกว่าเนื่องจากไม่เสีย overhead
      - application บางชนิดไม่ได้ออกแบบมาสำหรับการทำงานแบบ container ก็จะไม่สามารถใช้งานความสามารถของ container ได้สุดความสามารถ 
      - ทั้งสองสามารถทำงานแบบแยก environment ได้ในส่วนของ container จะสามารถแยกได้ในระดับ application ในส่วนของ virtual machine จะแยกได้ในระดับ OS
      - ข้อมูลที่ถูกเก็บจาก container โดยแรกเริ่มจะถูกเก็บไว้ที่ writable container layer ดังนั้นเมื่อ container นั้นหายไปข้อมูลภายในก็จะหายไปด้วย
  - Kubernetes
    - What is Kubernetes ?
      ![kubernetes](./media/kubernetes-logo.png)
      ```txt
      Kubernetes คือ เทคโนโลยีที่ใช้ในการบริหารจัดเทคโนโลยีคอนเทนเนอร์หรือก็คือ container orchestration 
      ที่ถูกคิดค้นโดย Google ซึ่งการที่ระบบสามารถทำ orchestration ได้นั้นหมายความว่าระบบนั้นสามารถจัดการทรัพยากร
      ที่มีหรือที่เพิ่มขึ้นมาได้อย่างอัติโนมัติ รวมไปถึงการดูแล application ที่ทำงานอยู่บน container ได้ตลอดเวลา
      สามารถนำไปใช้งานได้ทั้งบน on-premise หรือ public, private หรือ hybrid cloud ได้
      ```
    - คุณสมบัติของ Kubernetes
      1. service discovery and load balancing
        ```txt
        Kubernetes สามารถจัดการการเข้าถึง container ที่อยู่ภายใต้ service เดียวกันได้โดยการทำตัวเป็น load balancer 
        เพื่อกระจาย traffic ออกไปยัง container ที่เกี่ยวข้องได้ ทำให้เราสามารถเพิ่มหรือลบ container ได้ในขณะที่ 
        application สามารถทำงานได้เหมือนเดิม 
        ```
      2. storage orchestration
        ```txt
        Kubernetes สามารถเชื่อมต่อกับ storage system อื่น ๆ ได้ตามที่ต้องการเพื่อให้ข้อมูลนั้นไม่หายไปเมื่อ container 
        นั้นจบการทำงาน
        ```
      3. automated rollouts and rollbacks
        ```txt
        Kubernetes สามารถกำหนดสถานะที่ต้องการให้กับ container ได้และยังสามารถทำการแก้ไขสถานะที่ต้องการได้หากเกิด
        ข้อผิดพลาดจากการที่แก้ไขสถานะ Kubernetes อนุญาติให้สามารถทำการ rollback กลับไปยังสถานะก่อนแก้ไขได้
        ```
      4. automated bin packing
        ```txt
        Kubernetes มีการบริหารจัดการทรัพยากรให้เพียงพอต่อ application ที่จะมาทำงานใน cluster ได้โดยมี algorithm 
        ที่ใช้ในการคำนวณว่า worker node ไหนที่จะสามารถเอา application ไปทำงานบนนั้นได้ ทำให้สามารถใช้ทรัพยากรได้อย่างคุ้มค่าที่สุด
        ```
      5. self healing
        ```txt
        Kubernetes จะทำการเริ่มใหม่ให้กับ container ที่หยุดทำงานลง สร้าง container ใหม่หรือทำลาย container 
        เดิมทิ้งถ้า container นั้นไม่ตอบสนองต่อการทำ health check เมื่อ container นั้นไม่พร้อมใช้งาน kubernetes 
        จะไม่ forward traffic ไปยัง container เหล่านั้นจนกว่าจะกลับมาทำงานได้โดย user ที่เข้ามาใช้งานจะไม่เห็นการทำงานเหล่านี้เลย
        ```
      6. secret and configuration management
        ```txt
        Kubernetes สามารถจัดเก็บข้อมูลที่เป็นความลับได้เช่น username, password, token หรือ SSH key 
        และสามารถทำการแก้ไขค่าเหล่านี้ได้โดยไม่ต้องทำการสร้าง container ใหม่
        ```
    - องค์ประกอบ Kubernetes
      ![kubernetes-component](./media/kubernetes-component.svg)
      1. Control Plane Components
      - kube-api-server
      - etcd
      - kube-scheduler
      - kube-controller-manager
      - cloud-controller-manager
      2. Node Components
      - kubelet
      - kube-proxy
      - container runtime
      3. Addons
      - DNS
      - Web UI (Dashboard)
      - Container Resource Monitoring
- 2.1.2 Load Testing [4]
  - Type of loadtesting
    - Capacity ...
    - Stress ...
    ...
  - Scenario of load testing 
    - Type of host
      - Standalone
      - Distributed Testing
    - Success and Fail scenario
  - What is Taurus
    - Jmeter
- 2.1.3 Software Provisioning [3]
  - Ansible
    - What is ansible
      - Ansible architecture
      - How Ansible Work
  - Kubespray
    - What is kubespray
    - Long term maintainance
- 2.1.4 CI/CD Pipeline [4]
  - What is CI/CD
  - Jenkins
    - What is Jenkins
    - Jenkins Architecture
    - Jenkins Pipeline
- 2.1.5 Site Reliability Engineer (SRE) [16]
	- SRE Foundation
		- How SRE Relates to Devops
		- Monitoring
		- Alerting
  - Monitoring Tool
    - Challenging in Monitoring kubernetes
    - Prometheus
		- Grafana
  - Logging Tool
    - Challenging in Logging kubernetes
		- Fluentbig
		- Graylog
  - Alerting Tool
		- Alertmanager

### 2.2 งานวิจัยที่เกี่ยวข้อง (รีวิวงานที่ใกล้เคียงกัน ข้อดีข้อเสียของงานที่รีวิว)

## บทที่ 3 วิธีดำเนินการวิจัย

### 3.1 ขั้นตอนการดำเนิน

### 3.2 การเก็บรวบรวมความต้องการ

### 3.3 การออกแบบ (diagram ต่าง ๆ เช่น Use Case, Class, ER พร้อมคำอธิบายอย่างละเอียด)

### 3.4 สถาปัตยกรรมของระบบ (ภาพรวมของระบบ อธิบายถึงการใช้เทคโนโลยีอะไรบ้าง)

### 3.5 ภาพรวมของแอพพลิเคชั่น

## 4 ผลการวิจัย

(รายละเอียดของผลการทำงานของระบบ ดีขึ้นจากแต่เดิมอย่างไร ด้วยตัวเลขเท่าไหร่ นำข้อมูลมาเปรียบเทียบกัน สำเร็จกี่เปอร์เซ็นต์ ล้มเหลวกี่เปอร์เซ็นต์)

### 5 สรุปผลการวิจัยและข้อเสนอแนะ

(วิเคราะห์ระบบที่สร้าง ข้อดี ข้อเสีย สาเหตุ การแก้ไข ข้อเสนอแนะ)

# 3. ส่วนอ้างอิง