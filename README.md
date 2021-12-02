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

นอกจากนี้ยังมีบุคคลอื่น ๆ อีกที่ไม่ได้อยู่ในรายชื่อข้างต้นที่ได้ให้ความกรุณาแนะนำในการจัดทำรายงานสหกิจศึกษาฉบับนี้ ข้าพเจ้าจึงขอขอบพระคุณทุกท่านที่ได้มีส่วนร่วมในการให้ข้อมูลและให้ความเข้าใจเกี่ยวกับวิธีการปฏิบัติงานรวมถึงการจัดทำรายงานฉบับนี้จนสมบูรณ์

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

1. ตรวจสอบ, วางแผน และออกแบบระบบ Kubernetes เพื่อรองรับ high availability และค่า mean time to recovery ที่ต่ำ
2. ออกแบบระบบเพื่อรองรับการ Monitoring ของ Infrastructure และ Kubernetes
3. ออกแบบระบบเพื่อรองรับการ Monitoring Application ที่ติดตั้งด้วยเทคโนโลยี Container Platform ซึ่งรองรับการติดตั้งใน Kubernetes
4. ออกแบบและติดตั้ง Dashboard ที่รองรับการแสดงผล Metric จากระบบ Monitoring
5. ออกแบบและติดตั้งระบบ Alerting โดยมีการจัดลำดับการแจ้งเตือน (Severity) ที่เหมาะสมรองรับกับ Infrastructure และ Application
6. ตรวจสอบ Alerting ที่ติดตั้ง เพื่อความถูกต้องของระบบแจ้งเตือน

### 1.4 วิธีดำเนินการวิจัย

**********************************************************

1. กล่าวนำเข้าถึงวัตถุประสงค์ และ หรือ สมมุติฐานของการวิจัย
2. ระบุลำดับขั้นตอนในการรวบรวมข้อมูล
3. บรรยายลักษณะของประชากร กลุ่มเป้าหมาย ของงานวิจัยให้ชัดเจนโดยการอ้างอิง มีการกล่าวถึงเครื่องมือที่ใช้ และอธิบายเหตุผลสำคัญ
4. แสดงวิธีการวิเคราะห์ข้อมูล และการนำเสนอ
5. สรุปวิธีการดำเนินการวิจัย

**********************************************************

### 1.5 ประโยชน์ที่คาดว่าจะได้รับ

Infrastructure ที่ได้รับการปรับปรุงให้ทันสมัย พร้อมกับระบบตรวจสอบและแจ้งเตือนปัญหาก่อนที่จะเกิดขึ้น เพื่อให้มีความ high avalability ที่สูงและสามารถรองรับ wokrload ได้เป็นจำนวนมาก
ได้รับระบบ monitoring ที่สามารถใช้งานได้บน kubernetes
สามารถดูสถานะของ application ที่ติดตั้งแบบ container platform ได้พร้อมกับรองรับการขยายเมื่อเพิ่ม application ขึ้นมาในอนาคต
ได้รับ dashboard แสดงถึงค่าสถานะที่สำคัญของระบบ เพื่อใช้ในการวิเคราะห์ข้อมูลการใช้งานเชิงทรัพยากรและการตรวจสอบปัญหาที่เกิดขึ้นภายในระบบ
ระบบ alerting สามารถแจ้งเตือนปัญหาก่อนที่จะเกิดขึ้นได้ โดยสามารถแบ่งตามระดับความรุนแรงของปัญหานั้นในระบบเพื่อให้ระบบสามารถทำงานได้อย่างเสถียรและคนสามารถเตรียมการรับมือแก้ไขกับปัญหาได้ดียิ่งขึ้น
ได้รับระบบ alerting ที่มี false negative น้อยทำให้เมื่อมีการแจ้งเตือนจากระบบ alerting คนจะให้ความสำคัญกับแจ้งเตือนนั้น

## บทที่2 แนวคิด ทฤษฎีและงานวิจัยที่เกี่ยวข้อง

### 2.1 ทฤษฎีที่เกี่ยวข้อง (หลักตามประเด็นให้ครอบคลุมเรื่องที่วิจัย)

- 2.1.1 Container Technology
  - 2.1.1.1 Container
    - What is Virtual Machine (VM)
      ```txt
      virtual machine คือเครื่องเสมือนที่ทำหน้าที่เป็น computer เพื่อใช้ในการคำนวณงานต่าง ๆ โดยการใช้เทคโนโลยี 
      virtualization ซึ่งเป็นกระบวนการที่ใช้ในสร้าง virtual computer ด้วย central processing unit (CPU), 
      memory และ disk space ที่ถูกแบ่งมาจากคอมพิวเตอร์ของจริงดังนั้น virtual machine นั้นจึงเปรียบเสมือนกับ 
      virtual computer หรือ software-defined computer ทำให้สามารถแยก environment ของเครื่องออกจากกันได้
      ```
      ![vm](./media/VM.png)
    - What is Container
      ```txt
      container คือ เทคโนโลยีที่ใช้ในการแยกและจัดการ environment การทำงานของ application ซึ่งมีความ
      คล้ายคลึงกับแนวคิดของ virtual machine เทคโนโลยี container ทำให้การติดตั้ง application นั้นสามารถ
      ทำในสภาพแวดล้อมแบบไหนก็ได้ขอแค่ให้ OS นั้นสามารถติดตั้ง container engine ได้ก็พอ
      ```
      ![container](./media/container.png)
    - What is the Diffent Between Container and Virtual Machine (VM)
      ```txt
      container กับ virtual machine นั้นถูกใช้ใน use case ที่ต่างกันดังนั้นถ้าจะเปรียบเทียบก็จะสมมุติกรณีที่
      application เดียวกันทำงานด้วย 2 เทคโนโลยีนี้
      ```
      - ส่วนของ virtual machine (VM) จะมี overhead ของการทำงานของ OS ทำให้กิน memory และ disk เพิ่มขึ้นแต่ใน container นั้นต้องการแค่ binary และ libary ที่เกี่ยวข้องเท่านั้นเพื่อให้ application สามารถทำงานได้
        - การที่จะเคลื่อนย้ายหรือเพิ่มจำนวนของ instance ต่าง ๆ นั้น container สามารถทำได้ดีกว่าเนื่องจากไม่เสีย overhead
      - application บางชนิดไม่ได้ออกแบบมาสำหรับการทำงานแบบ container ก็จะไม่สามารถใช้งานความสามารถของ container ได้สุดความสามารถ 
      - ทั้งสองสามารถทำงานแบบแยก environment ได้ในส่วนของ container จะสามารถแยกได้ในระดับ application ในส่วนของ virtual machine จะแยกได้ในระดับ OS
      - ข้อมูลที่ถูกเก็บจาก container โดยแรกเริ่มจะถูกเก็บไว้ที่ writable container layer ดังนั้นเมื่อ container นั้นหายไปข้อมูลภายในก็จะหายไปด้วย
  - 2.1.1.2 Kubernetes
    - What is Kubernetes
      ![kubernetes](./media/kubernetes-logo.png)
      https://pngset.com/images/kubernetes-logo-symbol-sign-road-sign-stopsign-transparent-png-850380.png
      ```txt
      คือ เทคโนโลยีที่ใช้ในการบริหารจัดเทคโนโลยีคอนเทนเนอร์หรือก็คือ container orchestration 
      ที่ถูกคิดค้นโดย Google ซึ่งการที่ระบบสามารถทำ orchestration ได้นั้นหมายความว่าระบบนั้นสามารถจัดการทรัพยากร
      ที่มีหรือที่เพิ่มขึ้นมาได้อย่างอัตโนมัติ รวมไปถึงการดูแล application ที่ทำงานอยู่บน container ได้ตลอดเวลา
      สามารถนำไปใช้งานได้ทั้งบน on-premise หรือ public, private หรือ hybrid cloud ได้
      ```
    - Kubernetes's properties
      1. service discovery and load balancing
          ```txt
          Kubernetes สามารถจัดการการเข้าถึง container ที่อยู่ภายใต้ service เดียวกันได้โดยการทำตัวเป็น load balancer 
          เพื่อกระจาย traffic ออกไปยัง container ที่เกี่ยวข้องได้ ทำให้สามารถเพิ่มหรือลบ container ได้ในขณะที่ 
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
          ข้อผิดพลาดจากการที่แก้ไขสถานะ Kubernetes อนุญาตให้สามารถทำการ rollback กลับไปยังสถานะก่อนแก้ไขได้
          ```
      4. automated bin packing
          ```txt
          Kubernetes มีการบริหารจัดการทรัพยากรให้เพียงพอต่อ application ที่จะมาทำงานใน cluster ได้โดยมี algorithm 
          ที่ใช้ในการคำนวณว่า worker node ไหนที่จะสามารถเอา application ไปทำงานบนนั้นได้ ทำให้สามารถใช้ทรัพยากร
          ได้อย่างคุ้มค่าที่สุด
          ```
      5. self healing
          ```txt
          Kubernetes จะทำการเริ่มใหม่ให้กับ container ที่หยุดทำงานลง สร้าง container ใหม่หรือทำลาย container 
          เดิมทิ้งถ้า container นั้นไม่ตอบสนองต่อการทำ health check เมื่อ container นั้นไม่พร้อมใช้งาน kubernetes 
          จะไม่ forward traffic ไปยัง container เหล่านั้นจนกว่าจะกลับมาทำงานได้โดย user ที่เข้ามาใช้งานจะ
          ไม่เห็นการทำงานเหล่านี้เลย
          ```
      6. secret and configuration management
          ```txt
          Kubernetes สามารถจัดเก็บข้อมูลที่เป็นความลับได้เช่น username, password, token หรือ SSH key 
          และสามารถทำการแก้ไขค่าเหล่านี้ได้โดยไม่ต้องทำการสร้าง container ใหม่
          ```
    - Kubernetes's Components
      ![kubernetes-component](./media/kubernetes-component.svg)
      https://kubernetes.io/docs/concepts/overview/components/
      ```txt
      เมื่อทำการ deploy kubernetes cluster จะได้ kubernetes cluster มาซึ่งประกอบไปด้วยชุดของ 
      worker machines ที่เรียกว่า node ที่ทำหน้าที่จัดการกับ workload ต่าง ๆ ใน cluster
      ```
      1. Control Plane Components
          ```txt
          คือ ส่วนที่ทำหน้าที่ในการตัดสินใจหลักของ Kubernetes cluster และตรวจจับและตอบโต้กับเหตุการณ์ต่าง ๆ 
          ที่เกิดขึ้นกับ cluster
          ```
          - kube-api-server
            ```txt
            คือ ส่วนที่ใช้ในการสื่อสารกับ components อื่น ๆ ของ Kubernetes
            ```
          - etcd
            ```txt
            คือ ที่เก็บข้อมูลของ Kubernetes cluster ในรูปแบบ key: value เช่น ข้อมูลของ Pod, service 
            ที่ทำงานบน cluster เมื่อมีการแก้ไขหรือเพิ่มข้อมูลเข้าไปใน Kubernetes 
            จะมีการมาเขียนข้อมูลที่ ETCD เสมอ
            ```
          - kube-scheduler
            ```txt
            คือ components ที่ใช้ในการระบุ worker node ปลายทางที่เหมาะสมกับ Pods นั้น ๆ 
            โดยการใช้ scheduling algorithm
            ```
          - kube-controller-manager
            ```txt
            คือ ส่วนที่ทำหน้าที่ดูแลสภาวะของ Kubernetes cluster ให้อยู่ในสภาวะที่กำหนดไว้
            ```
      2. Node Components
          - kubelet
            ```txt
            คือ ส่วนที่ทำหน้าที่ดูแลทรัพยากรต่าง ๆ ใน worker node และรอรับคำสั่งจาก kube-api-server
            ```
          - kube-proxy
            ```txt
            คือ ส่วนที่ทำหน้าที่เป็น proxy บนทุก ๆ node ใน cluster และทำหน้าที่ดูแล network rule บน node 
            ที่ proxy อยู่ทำให้สามารถเกิดการเชื่อมต่อจากภายในและภายนอกกับ pod ได้ 
            ```
          - container runtime
            ```txt
            คือ software ที่มีหน้าที่ในการดูแล container ที่ทำงานอยู่
            ```
    - แนวคิดการทำงานของ Kubernetes
      1. Namespace
          ```txt
          เป็นการแยกกลุ่มของทรัพยากรใน Kubernetes cluster เสมือนกับการสร้าง virtual cluster ขึ้นมากอีกอันภายใน
          ```
      2. Workloads
          ```txt
          คือ application ที่ทำงานอยู่ใน Kubernetes cluster โดยจะแบ่งเป็น
          ```
          - Deployments และ ReplicaSet
            ```txt
            ใช้สำหรับ stateless application ได้เป็นอย่างดีเพราะว่าทุก ๆ pod ใน deployment นั้นสามารถแทนที่กันได้ 
            และรองรับการ update ที่ไม่มี downtime
            ```
          - StatefulSet
            ```txt
            ทำให้ pod เป็น stateful ได้โดยการจับคู่ pod เข้ากับ persistent volume เพื่อให้ข้อมูลไม่หายไปเมื่อ pod 
            ถูกทำลาย
            ```
          - DaemonSet
            ```txt
            ทำให้ pod นั้นกระจายไปอยู่ในทุก ๆ node ของ Kubernetes cluster รวมทั้ง node ที่เพิ่มเข้ามาใหม่
            ```txt
          - Job และ CronJob
            ```txt
            เป็น pod ที่ถูกสร้างขึ้นมาทำงานโดยเฉพาะแล้วก็หยุดทำงานไป เช่นการทำ database migration ตอนเริ่ม 
            deploy application ที่ต้องการใช้งาน database
            ```
      3. Services
          ```txt
          คือ การที่จะให้เกิดการเข้าถึงจากภายนอกหรือภายในกับกลุ่มของ pod ใน Kubernetes cluster โดยที่
          ไม่ต้องมีการแก้ไข application ที่ทำงานอยู่ โดยจะแบ่งเป็น
          ```
          - ClusterIP 
            ```txt
            ทำหน้าที่ในการสร้าง virtual IP address เพื่อให้สามารถติดต่อสื่อสารกันภายใน 
            Kubernetes cluster ได้อย่างเดียว
            ```
          - NodePort 
            ```txt
            ทำหน้าที่สร้าง port การเชื่อมต่อจากภายนอกเข้าสู่ node นั้น ๆ ผ่าน ClusterIP อีกที
            ```
          - LoadBalancer 
            ```txt
            ใช้ในการเข้าถึงจากภายนอกโดยอาศัย Load Balancer ของผู้ให้บริการ
            ```
      4. Ingress
          ```txt
          คือ API object ที่ทำหน้าที่ในการจัดการการเข้าถึงจากภายนอกไปถึง service ปลายทางใน 
          Kubernetes cluster ทำให้สามารถใช้ 1 IP address กับหลาย ๆ service ที่ทำงานภายใน 
          Kubernetes cluster โดยสร้าง ingress-controller มาทำการแยก 
          traffic ไปให้กับ service ที่ต้องการผ่าน domain name แทน
          ```
- 2.1.2 Performance Testing
  ```txt
  คือ การจำลองสภาวะต่าง ๆ ของระบบในภาวะที่น่าจะเกิดขึ้นจริงหากมีผู้ใช้งานเข้ามาพร้อมกัน
  ```
  - 2.1.2.1 ชนิดของ Performance Testing
    - Load Testing
      ![load-testing](./media/load-testing.png)
      https://www.radview.com/blog/4-types-of-load-testing-and-when-each-should-be-used/
      ```txt
      คือ การทดสอบประสิทธิภาพของระบบทั่วไปว่าเมื่อมีคนใช้งานจำนวนหนึ่งจะมีเวลาตอบกลับเท่าไหร่
      ```
    - Capacity Testing
      ![capacity-testing](./media/capacity-testing.png)
      https://www.radview.com/blog/4-types-of-load-testing-and-when-each-should-be-used/
      ```txt
      คือ การทดสอบหาความจุสูงสุดที่ระบบสามารถรองรับได้และอยู่ในเวลาตอบกลับที่กำหนด
      ```
    - Stress Testing
      ![stress-testing](./media/stress-testing.png)
      https://www.radview.com/blog/4-types-of-load-testing-and-when-each-should-be-used/
      ```txt
      คือ การทดสอบหาประสิทธิภาพของระบบในสภาวะที่สุดโต่ง เช่น การใช้ระบบที่มีทรัพยากรน้อยที่สุดเพื่อหาพฤติกรรมของระบบ
      ```
    - Soak Testing
      ![soak-testing](./media/soak-testing.png)
      https://www.radview.com/blog/4-types-of-load-testing-and-when-each-should-be-used/

      ```txt
      คือ การทดสอบหาประสิทธิภาพของระบบเมื่อมีการใช้งานอย่างต่อเนื่องเป็นระยะเวลาที่นานขึ้นเพื่อหาปัญหาที่
      อาจจะพบเมื่อไม่ได้ระบบไม่ได้ทำงานระยะเวลาสั้น ๆ 
      ```
  - 2.1.2.2 Scenario of load testing 
    - Standalone
      ```txt
      คือ รูปแบบการทำ testing ที่ใช้เพียงเครื่องคอมพิวเตอร์เพียงเคยเดียวเป็นตัวสร้าง traffic ไปยังระบบปลายทาง
      ```
    - Distributed Testing
      ```txt
      คือ รูปแบบการทำ testing ที่ใช้เครื่องคอมพิวเตอร์หลาย ๆ เครื่องในการสร้าง traffic แล้วส่งไปยังระบบปลายทาง
      ```
  - 2.1.2.3 What is Taurus   
    ![taurus](./media/taurus-logo.png)
    
    https://www.blazemeter.com/taurus-automation
    ```txt
    คือ open source เครื่องมือที่ใช้สำหรับการทำ load test และ functional test 
    โดยทำตัวเป็นตัวที่ห่อหุ้มเครื่องมือสำหรับการทำ load test และ functional test อีกที 
    ทำให้ผู้ใช้งานสามารถเขียน script ได้ในรูปแบบของ YAML/JSON เพื่อไปเรียกใช้เครื่องมืออื่น ๆ 
    ที่ต่างกันได้และง่ายต่อการเก็บใน source control system

    Taurus สามารถนำไปใช้งานได้กับงานอัตโนมัติเนื่องจากไม่ต้องการ UI เพื่อทำงานและสามารถกำหนด 
    Service-Level Objective (SLO) หรือ Service-Level Agreement (SLA) ได้โดยการกำหนด
    pass/fail criteria ขึ้นมา   
    ```
    ตัวอย่าง script ที่ใช้งาน
    ```yaml
    settings:
      default-executor: jmeter
      env:
        URL:  https://<url>
      artifacts-dir: ./%Y-%m-%d_%H-%M-%S.%f
      verbose: false

    scenarios:
      api_capacity_testing:
        data-sources:
        - path: payload.csv
          delimeter: ','
          quoted: 'false'
          loop: True
        requests:
        - url: ${URL}/
          method: GET
          headers:
            Connection: close
            Content-Type: application/json
            apikey: <api-key>
          timeout: 1s
          body: '{
            "companyCode": "${companyCode}",
            "productCode": "${productCode}",
            "branchNo": "${branchNo}",
            "contractNo": "${contractNo}",
            "accountNo": "${accountNo}",
            "requestNo": "${requestNo}"
          }'

    execution:
    - scenario: api_capacity_testing
      concurrency: 1000
      ramp-up: 60m
      hold-for: 10m

    reporting:
    - module: final-stats
      summary: true
      percentiles: true
      summary-labels: true
      failed-labels: true
      test-duration: true 
      dump-xml: stats.xml
      dump-csv: data.csv
    ```
- 2.1.3 Software Provisioning
  - 2.1.3.1 Ansible

    ![ansible](./media/ansible-logo.png)

    https://commons.wikimedia.org/wiki/File:Ansible_logo.svg

    - What is ansible
      ```txt
      คือ เครื่องมือ open source ที่ใช้ในการทำ software provisioning เช่น 
      การติดตั้งซอฟต์แวร์หรือแอปพลิเคชัน การตั้งค่าของระบบ การตรวจค่าของระบบ 
      และการตรวจสอบการทำงานของระบบบนเครื่องปลายทางได้หลายเครื่องโดยไม่ต้อง
      ติดตั้งเครื่องมืออื่นเพิ่มเติมที่เครื่องปลายทาง

      Ansible ใช้รูปแบบไวยากรณ์การเขียนแบบ YAML โดยรูปแบบการเขียน YAML นั้นจัดอยู่ในตระกูลภาษาที่ใช้สำหรับการ
      ตั้งค่าหรือเก็บค่าข้อมูลของระบบนั้น ๆ ออกมาเป็นไวยากรณ์ที่มนุษย์สามารถเข้าใจได้ง่ายขึ้น

      Ansible ถูกออกแบบมาให้มีการทำงานในรูปแบบของ idempotent นั้นก็คือมีคุณสมบัติที่ไม่ว่าจะทำงานกี่ครั้งก็จะ
      ได้ผลลัพธ์เหมือนเดิมเสมอ
      ```
    - Ansible architecture
      ![ansible-architecture](./media/ansible-architecture.png)
      1. Control Node
          ```txt
          คือ เครื่องคอมพิวเตอร์ที่ใช้รันคำสั่งของ Ansible
          ```
      2. Inventories 
          ```txt
          คือ list ของเครื่องปลายทางที่ต้องการเข้าถึง
          ```
          ```ini
          [platform_monitoring:children]
          monitoring
          k8s_cluster

          [monitoring]
          prometheus ansible_user=ubuntu ansible_host=10.22.1.63

          [k8s_cluster]
          master1 ansible_user=ubuntu ansible_host=10.22.1.64
          worker1 ansible_user=ubuntu ansible_host=10.22.1.59
          worker2 ansible_user=ubuntu ansible_host=10.22.1.54
          ```
          - ตัวอย่าง inventory ในรูปแบบ ini
      3. Playbooks
          ```txt
          คือ ชุดของคำสั่งที่จะเรียกใช้งาน
          ```
          ```yaml
          - name: update and install prometheus
            apt:
              name: prometheus
              state: latest
              update_cache: yes
              cache_valid_time: 3600
          - name: prometheus args
            template:
              src: prometheus.j2
              dest: /etc/default/prometheus
              mode: 0644
              owner: root
              group: root
            notify: restart_prometheus
          ```
          - ตัวอย่าง playbook ที่ใช้ในการติดตั้ง prometheus server
    - Ansible Core Concept
      1. Modules
          ```txt
          ชุดคำสั่งขนาดเล็กที่ถูกเขียนด้วยภาษา python ที่จะถูกส่งไปทำงานอยู่บนเครื่องปลายทางใน inventories ที่กำหนด
          ```
          ```yaml
          - name: Restart and do daemon reload
            ansible.builtin.systemd:
              name: nginx.service
              state: restarted
              daemon_reload: yes
          ```
          - ตัวอย่างของ Task ซึ่งใช้งาน module systemd เพื่อไป restart และ reload nginx service
      2. Tasks
          ```txt
          คือ การกระทำหนึ่งอย่างบน Ansible
          ```
      3. Roles
          ```txt
          คือ การนำ playbooks หลาย ๆ อันมาใช้งานร่วมกัน
          ```
    - How Ansible Work
      ```txt
      Ansbile จะเชื่อมต่อกับเครื่องปลายทางทั้งหมดผ่านวิธีการต่าง ๆ ตามระบบปฏิบัติการของเครื่องปลายทาง 
      โดยต้องการแค่เครื่องที่ใช้ Ansible นั้นสามารถเข้าถึงและใช้งานเครื่องปลายทาง (inventory) เหล่านั้นได้

      หลังจากที่ Ansible สามารถเชื่อมต่อกับเครื่องปลายทางได้แล้ว Ansible จะส่งโปรแกรมภาษา python 
      ขนาดเล็กไปยังเครื่องปลายทางเพื่อใช้ในการ run คำสั่งอัตโนมัติต่าง ๆ และทำการลบออกเมื่อใช้งานเสร็จ
      ```
- 2.1.4 Site Reliability Engineer (SRE) [16]
  - 2.1.4.1 What is SRE
      ```txt
      คือ สิ่งที่เกิดขึ้นเมื่อให้ software enginner นั้นออกแบบ operation team หรือกล่าวอีกนัยหนึ่ง SRE 
      คือทีมที่ใช้ความรู้ความสามารถด้าน software engineer ไปปรับใช้กับปัญหาทางด้าน operation 
      เพื่อให้ระบบนั้นมีความทนทานต่อทุกสถานการณ์
      ```
  - 2.1.4.2 Principle of SRE
      ```txt
      ถึงแม้รูปแบบการทำงาน ลำดับความสำคัญจะแตกต่างกันไปตาม SRE แต่ละทีมแต่ทุกทีมก็ยึดมั่นใน
      หลักการเดียวกันนั้นก็คือทำหน้าที่ดูแลเกี่ยวกับ ความพร้อมใช้งาน, ความล่าช้าในการใช้งาน, ประสิทธิภาพการใช้งาน, 
      ความสามารถในการจัดการเปลี่ยนแปลง, การรับมือกับเหตุการณ์ที่ไม่คาดคิดและความต้องการของระบบ 
      ```
  - 2.1.4.3 Monitoring
      ```txt
      การทำ monitoring เป็นหนึ่งส่วนที่สำคัญกับ service มากเพราะว่าทำให้สามารถติดตามสถานะของระบบและ
      ความพร้อมใช้งานของระบบดังนั้นการจะทำระบบ monitoring ขึ้นมาต้องถูกออกแบบและวางแผนเป็นอย่างดี 
      ระบบ monitoring แบบดั้งเดิมนั้นจะรอจนค่าของอะไรบางอย่างแล้วดูว่ามันเกิดจุด trigger ไหมถ้าเกินก็จะ
      ส่งการแจ้งเตือนไปยังผู้ที่เกี่ยวข้องแต่ถ้ามองระบบแบบนี้ก็จะรู้ได้ว่ายังต้องการคนเพื่อที่จะเปิดอ่านการแจ้งเตือน
      และตัดสินใจว่าจะทำอะไรเมื่อเกิดเหตุการณ์นั้นขึ้น

      ระบบ monitoring ที่ดีนั้นไม่ควรมีมนุษย์เข้ามาเกี่ยวข้องเมื่อมีการแจ้งเตือนแต่ควรมี software 
      ที่เข้ามาจัดการในส่วนนี้แทนและมนุษย์จะมีส่วนร่วมเมื่อต้องใช้มนุษย์จริง ๆ เท่านั้น SRE นั้นต้องดูแลคุณภาพของ 
      service ร่วมกันกับ devloper จากการ monitor และทำการปรับแต่ง service เพื่อปรับปรุงคุณภาพ

      ระบบ monitoring ที่เหมาะสมจะทำให้สามารถตรวจพบปัญหาในระบบได้ไวและทำให้มีค่า MTTR (Mean Time To Recovery) 
      ที่ต่ำได้

      ระบบ monitoring แบ่งออกเป็นสามส่วนหลัก ๆ ด้วยกัน
      ```
    <!-- https://siamchamnankit.co.th/%E0%B9%80%E0%B8%A5%E0%B8%B7%E0%B8%AD%E0%B8%81%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3%E0%B9%83%E0%B8%99%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B8%97%E0%B8%B3-monitoring-%E0%B8%A3%E0%B8%B0%E0%B8%AB%E0%B8%A7%E0%B9%88%E0%B8%B2%E0%B8%87-log-%E0%B8%81%E0%B8%B1%E0%B8%9A-metrics-658cb6efef96 -->
    1. Metrics
        ```txt
        คือ ข้อมูล ณ ช่วงเวลาต่าง ๆ ของระบบนั้นทำให้สามารถทราบถึงภาพรวมของระบบ ณ หนึ่งหน่วยเวลานั้น ๆ
        ```
        ![metrics](./media/metrics.jpg)
        - ตัวอย่างรูปภาพ metrics ของ HAProxy
    2. Logs
        ```txt
        คือ ข้อมูลทุกช่วงเวลาและเหตุการณ์ของระบบนั้นทำให้สามารถมองระบบแบบละเอียดว่าเกิดอะไรขึ้นในระบบนั้นได้

        เป็นข้อมูลที่ไม่มีใครต้องมานั่งอ่านแต่ถูกบันทึกไว้เพื่อสำหรับกรณีของการตรวจพิสูจน์พยานหลักฐาน 
        สิ่งที่เกิดขึ้นก็คือปกติจะไม่มีใครมาอ่าน log ถ้าไม่มีเหตุจำเป็นจริง ๆ

        โดยจะแบ่งเป็น level ต่าง ๆ
        ```
        - Log level
            ```txt
            ALL: เป็น level ที่แสดงทั้งหมดยกเว้นใน OFF level
            TRACE: เป็น level ที่เน้นไปในการใช้งาน debugging และใช้ในการตรวจจับการไหลของโปรแกรม
            DEBUG: เป็น level ที่เอาไว้ debug แสดงถึง input และ output ของโปรแกรม
            INFO: เป็น level ที่ใช้แสดงการทำงานของโปรแกรมคร่าว ๆ
            WARN: เป็น level ที่เหมาะกับการแสดงว่าเหตุการณ์แบบนี้สามารถทำให้เกิด Error ได้
            FATAL: เป็น level ที่ใช้กับเหตุการณ์ที่รุนแรงที่อาจจะทำให้โปรแกรมหยุดทำงานได้
            ERROR: เป็น level ที่ใช้กับกรณีที่โปรแกรมทำงานแล้วเกิด Error ขึ้นมาในโปรแกรม
            OFF: เป็นการที่ปิด level ในการแสดงผลของ log ทั้งหมด
            ``` 
        <!-- https://iamgique.medium.com/log-level-%E0%B8%AA%E0%B8%B3%E0%B8%84%E0%B8%B1%E0%B8%8D%E0%B9%84%E0%B8%89%E0%B8%99-d92b157240c4 -->
        ![logs](./media/logs.png)
        - ตัวอย่างรูปถาพการเก็บ logs ของ prometheus 
    3. Traces
        ```txt
        คือ ข้อบันทึกข้อมูลการทำงานของระบบ
        ```
        ![traces](./media/traces.jpg)
        ตัวอย่างการ call API ของ jaeger
  - 2.1.4.4 Alerting
      ```txt
      เป็นงานที่ต้องการมนุษย์มาทำโดยทันทีเพื่อตอบโต้กับเหตุการณ์ที่เกิดขึ้นหรือเหตุการณ์ที่กำลังจะเกิดขึ้นเพื่อทำให้
      สถานการณ์ดีขึ้น
      ```
  - 2.1.4.5 What is DevOps
      ```txt
      คือ การเอาคำว่า development มารวมกับคำว่า operation จริง ๆ แล้ว DevOps ไม่ใช่ชื่อของอาชีพแต่มันคือ 
      วัฒนธรรม ที่ช่วยให้เป้าหมายของทั้ง developer และ operation ทีมเป็นจริงได้โดยการพัฒนา software 
      ขึ้นมาชุดหนึ่งจะไม่ทำงานแบบต่างคนต่างทำอีกต่อไปแต่จะเป็นการที่ทั้งสองทีมร่วมมือกันทำงานกันตลอดระยะเวลา
      ของแอปพลิเคชันโดยยึดแต่ละขั้นตอนของการพัฒนาและออกแบบระบบนั้นจะใช้ระบบอัตโนมัติมากกว่ามนุษย์เป็นหลัก
      ```
  - 2.1.4.6 How SRE Relates to Devops
          ```txt
          การนำเครื่องมือมาประยุกต์ใช้งานและสร้างระบบอัตโนมัตินั้นสอดคล้องกับแนวคิดของ SRE หลายประการ 
          โดยสามารถมองได้หลายมุมมอง เช่น SRE นั้นคือการนำ DevOps มาใช้งานพร้อมกับเพิ่มรายละเอียดอื่น ๆ ขึ้นมา
          หรือ DevOps คือลักษณะทั่วไปของหลักการใน SRE หลาย ๆ เรื่อง 
          ```
- 2.1.5 Challenging in Monitoring
  - 2.1.5.1 Challenging in Monitoring Metrics kubernetes
      ```txt
      Kubernetes มี components ด้านในที่ซับซ้อนกว่า infrastructure แบบเดิมมากทำให้ยากที่จะตรวจสอบปัญหาว่า
      เกิดขึ้นจากสาเหตุไหนระหว่าง Kubernetes components
      ```
    1. มี metric มากมายใน Kubernetes cluster
        ```txt
        ความซับซ้อนของ component ภายใน เช่น 1 node มีหลาย pods และใน 1 pods อาจจะมีหลาย containers ภายใน
        และแต่ละ pod ก็มีหน้าที่ของมันเองทำให้เกิด metrics ของ pods ขึ้นมาจำนวนมาก หรือใน 1 application ที่ทำการติดตั้ง
        นั้นมีจำนวน pod มากกว่า 1 และอยู่ข้าม node กัน 

        ทุก ๆ ครั้งที่ pod ได้ถูกสร้างโดย kubelet จาก kube-scheduler แต่ละ pod จะมี metrics ของตัวมันเองเสมอทำให้การเก็บข้อมูล
        ของ pod นั้นทำได้ยากขึ้น

        การ monitoring kubernetes เพื่อตรวจสอบปัญหาที่เกิดขึ้นภายในนั้นต้องการความรู้ความเข้าใจเกี่ยวกับด้าน software และ opeartion
        เพื่อหาปัญหาและสาเหตุของปัญหา ดังนั้นการทำ monitoring ต้องรู้ว่า metrics ของ pod นั้น metrics ไหนมีคุณค่าเช่น crash loop, 
        pod restart, CPU utilization, Memory Usage, Deadlock เพื่อแก้ไขไม่ให้มันเกิดขึ้นในอนาคต 
        ```
    2. ความไม่ถาวรของ pod
        ```txt
        ใน Kubernetes component ที่เป็น DaemonSet, Deployments, Jobs และ StatefulSets ที่สามารถสร้าง pod ใหม่ได้ทันที
        เมื่อ pod เก่านั้นเกิดปัญหาขึ้นหรือเมื่อมีการ scale จำนวน pod เพิ่มขึ้นหรือเมื่อมีการ scale จำนวนของ pod ลงก็จะมี pod ที่หายไปตลอดกาล

        Kubernetes สามารถย้าย pod โดยการสร้างใหม่และลบของเก่าทิ้งเพื่อทำให้ node มีทรัพยากรที่มากขึ้นและไปสร้าง pod 
        ที่มีชนิดเดียวกันแต่คนละชื่อและอาจจะอยู่คนละที่ใน node อื่นแทน
        ```
    3. ไม่สามารถดูรูปร่างระบบได้อย่างชัดเจน
        ```txt      
        ในสถาปัตยกรรมแบบ microservice ได้มีการแบ่ง application ออกเป็น service ย่อย ๆ ตาม core function ของระบบดังนั้น 
        service ก็จะถูกออกแบบมาให้ไม่ขึ้นต่อกันโดยเมื่อมีการเปลี่ยนแปลง 1 service จะไม่กระทบต่อ service อื่น
        การเชื่อมต่อภายใน Kubernetes ก็จะวิ่งภายใน virtual network
        
        ใน stateless application ที่ถูกออกแบบใน microservice มีประโยชน์ในการทำ horizontally scaling เป็นอย่างมากเนื่องจาก
        สามารถ scale จำนวนของ pod ขึ้นมาได้เรื่อย ๆ ตามความต้องการและทรัพยากรที่มี
        จากข้อ 2. ความไม่ถาวรของ pod เมื่อต้อง ถ้าต้องการรับ request มากขึ้นก็ทำการ scale ขึ้นและเมื่อไม่มีการใช้งานก็จะ scale ลง
        ทำให้การรู้ภาพรวมของระบบนั้นเป็นทำได้ยากขึ้น
        ```
        <!-- Microservice ไม่จำเป็นต้องเป็น stateless และ stateless ไม่จำเป็นต้องเป็น microservice -->
  - 2.1.5.2 Challenging in Monitoring Logs kubernetes
    1. การทำตามสัญญาเกี่ยวกับ logging service level agreement (SLA)
        ```txt
        application ใน Kubernetes นั้นทำงานอยู่ pod มากกว่าหรือเท่ากับหนึ่งและอาจจะอยู่ในหลาย ๆ node ระบบ logging นั้น
        ต้องมั่นใจว่าสามารถจัดเก็บ log ของ application ในทุก ๆ log ได้
        ```
    2. การทำ namespace logging
        ```txt
        ใน Kubernetes จะสามารถสร้าง namespace เพื่อแยกใช้งานระหว่างทีมหรือโปรเจ็กต์ได้แต่ละ application ใน namespace ก็จะ
        มีรูปแบบการเขียน log ที่แตกต่างกันไปและการเลือกที่เก็บ log ของ namespace นั้น ๆ
        ```
    3. การจัดเก็บ critical log 
        ```txt
        เมื่อ application ทำงานผิดพลาด pod จะถูกลบและสร้างใหม่ด้วยชื่อที่ไม่เหมือนเดิมและ log ที่ถูกเขียนอยู่ใน writable layer 
        ของ pod ก็จะหายไปตาม lifecycle ของ pod ทำให้ log ที่สำคัญหายไปและการหาสาเหตุของปัญหานั้นทำได้ยากขึ้น
        ```
    4. การจัดการกับ log layer ต่าง ๆ 
        ```txt
        ใน Kubernetes มี component มากมายและแต่ละอันก็มี log ที่แตกต่างกันไปดังนั้นต้องทำความเข้าใจเกี่ยวกับ log ของ component
        และวิธีการใช้งานมัน
        ```
- 2.1.6 Key Performance Indicator (KPI) [1]

  https://kpilibrary.com/categories/systems
  
  ```txt
  คือ ดัชนีตัวชี้วัดในงานบริหารงานการซ่อมบำรุง
  ```
  1. Mean Time To Recovery (MTTR)
      ```txt
      คือ ค่าเวลาการซ่อมเฉลี่ยสามารถคำนวณได้จากเวลาที่ใช้ในการซ่อมระบบทั้งหมดหายด้วยจำนวนครั้งที่ซ่อม ค่ายิ่งน้อยยิ่งดี
      กล่าวคือระยะเวลาเฉลี่ยที่ใช้ในการซ่อมระบบต่อการล่ม 1 ครั้ง
      ```
  2. Mean Time To Failure (MTTF)
      ```txt
      คือ ค่าเฉลี่ยก่อนการเสียหายสามารถคำนวณได้จากเวลาที่ระบบสามารถทำงานได้ทั้งหมดหารด้วยจำนวนครั้งที่ระบบหยุดทำงาน
      ค่ายิ่งมากยิ่งดีกล่าวคือเวลาเฉลี่ยที่ระบบทำงานได้ก่อนระบบจะล่ม 1 ครั้ง
      ```  
  3. Mean Time Between Failure (MTBF)
      ```txt
      คือ ค่าเฉลี่ยระหว่างความเสียหายสามารถคำนวณได้จากเวลาทั้งหมดที่ระบบใช้ลบด้วยเวลาที่ระบบพังทั้งหมดหารด้วยจำนวนครั้ง
      ทั้งหมดที่ระบบพัง ค่ายิ่งมากยิ่งดีกล่าวคือค่าเวลาเฉลี่ยที่ระบบจะเสียก่อนล่ม 1 ครั้ง
      ```
  3. Availability
      ```txt
      คือ ค่าความพร้อมใช้งานสามารถคำนวณได้จาก MTBF หารด้วยผลรวมของ MTBF กับ MTTR
      ```

### 2.2 งานวิจัยที่เกี่ยวข้อง

Log-based software monitoring: a systematic mapping study
<!-- https://arxiv.org/pdf/1912.05878.pdf -->
งานวิจัยนี้กล่าวถึง
```txt
การหาเครื่องมือที่เหมาะสมในการทำ logging การประมวลผลและจัดเก็บ log ใน infrastructure และการดึงข้อมูลเชิงลึกของ log ที่เก็บออกมา
จากการรวบรวมการทำ monitoring ใน software จากหลาย ๆ งานวิจัยด้วยกัน
```

งานวิจัยได้ทำการ categorize งานวิจัยเกี่ยวกับ logging ทั้งหมด 108 งานวิจัยออกเป็น 3 แบบ

1. Logging
    ```txt
    การทำให้เก็บ log ได้ดี 
    ```
    <!-- 1. Empirical Studies 
        
        Understanding and insights about how developers conduct logging in general

    2. Log requirements

        Assessment of log conformance given a known requirement

    3. Implementation of log statements 

        Focus on what to log, where to log, and how to log -->
2. Log Infrastructure
    ```txt
    เกี่ยวกับเทคนิคการเก็บ log เพื่อให้สามารถไปใช้ในการวิเคราะห์ได้อย่างมีประสิทธิภาพ
    ```
    <!-- 
    1. Parsing

        Extraction of log templates from raw log data

    2. Storage

        Efficient persistence of large datasets of logs -->
3. Log Analysis
    ```txt
    การดึงข้อมูลเชิงลึกของ log ออกมาเพื่อวิเคราะห์ เช่น การตรวจหา anomaly detection, security and privacy หรือ root cause 
    analysis
    ```

<!-- 1. Anomaly detection

        Detection of abnormal behaviour

    2. Security and privacy

        Intrusion and attack detection

    3. Root cause analysis

        Accurate failure identification and impact analysis

    4. Failure prediction

        Anticipating failures that leads a system to an unrecoverable state

    5. Quality assurance 

        Logs as support for quality assurance activities

    6. Model inference and invariant mining

        Model and invariant checking

    7. Reliability and dependability

        Understand dependability properties of systems (e.g., reliability, performance)

    8. Log platforms 

        Full-fledged log analysis platforms -->

ข้อดีของงานวิจัยนี้คือการที่ผู้จัดทำได้รวบรวมวิธีการ monitoring ประเภท logs ของหลาย ๆ งานวิจัยเข้ามาจัดหมวดหมู่และทำการสรุปผลให้สามารถเข้าใจได้ง่ายยิ่งขึ้นถึงประเภทของการจัดเก็บ logs

ข้อเสียของงานวิจัยนี้คือยังไม่มีการแนะนำรูปแบบการเขียนข้อมูล logs ที่เหมาะสมสำหรับ application และความลึกของเลเวลของ logs ที่จะเขียนว่าควรเป็นอย่างไร

## บทที่ 3 วิธีดำเนินการวิจัย

รายงานสหกิจฉบับนี้เป็นการพัฒนาและปรับปรุงระบบ infrastructure เดิมที่มีอยู่ให้ทันสมัยพร้อมติดตั้งระบบตรวจสอบและแจ้งเตือนปัญหาก่อนที่จะเกิดขึ้นโดยยังคำนึกถึงการใช้งานในอนาคตเมื่อมีแอปพลิเคชันใหม่ ๆ เพิ่มเข้ามาในระบบให้สามารถทำการจัดเก็บข้อมูลของ application ได้อย่างอัตโนมัติ โดยในบทนี้จะกล่าวถึงขั้นตอนการดำเนินงาน การเก็บรวบรวมความต้องการ การออกแบบ สถาปัตยกรรมของระบบและภาพรวมของแอปพลิเคชัน

### 3.1 ขั้นตอนการดำเนิน

1. ศึกษาความต้องการและขอบเขตของโครงงาน
2. วิเคราะห์ความต้องการและวางแผนตารางการพัฒนาโครงงานให้สอดคล้องกับงานเพื่อให้โครงงานเสร็จภายในระยะเวลาที่กําหนด
3. เลือกเทคโนโลยีสําหรับพัฒนาโครงงานให้เหมาะสมกับงาน
4. ศึกษาเทคโนโลยีที่เลือกใช้สําหรับการพัฒนาโครงงาน
5. ศึกษาและทําความเข้าใจเกี่ยวกับกระบวนการทํางานการของระบบ monitoring และ alerting
6. ออกแบบและพัฒนาระบบ monitoring และ alerting ที่เหมาะสม
7. ทดสอบและปรับปรุงการทํางานให้ขั้นตอนการทํางานถูกต้อง เหมาะสมและมีประสิทธิภาพมากยิ่งขึ้น
8. สรุปผลและจัดทําเอกสารอธิบายกระบวนการทํางานและโครงสร้างของโครงงาน

### 3.2 การเก็บรวบรวมความต้องการ

1. นำเทคโนโลยีคอนเทนเนอร์ที่ทันสมัยเข้ามาใช้งานกับองค์กร
2. สามารถรองรับการเพิ่มจำนวนของ node ขึ้นมาได้ในอนาคต
3. สามารถรองรับการทำ high availability ภายใน cluster ได้
4. นำการทำ self-healing เข้ามาปรับใช้งานกับ application เพื่อให้มี MTTR (Mean Time To Recoovery) ที่ต่ำ
5. ปรับปรุง application ให้สามารถรับจำนวนผู้ใช้งานได้ตามเหมาะสม
6. สามารถจัดเก็บข้อมูล metrics ที่ออกมาจาก service ภายใน kubernetes เดิมได้
7. สามารถจัดเก็บข้อมูล metrics ของ service อื่น ๆ ใน infrastructure เดิมได้
8. สามารถรองรับการจัดเก็บข้อมูล metrics ที่ออกมาจาก service ที่เพิ่มใน Kubernetes ในอนาคตได้
9. สามารถนำ metrics ที่เก็บได้จาก Kubernetes และ service ภายในมาแสดงผลผ่าน grafana dashboard ได้อย่างถูกต้องและเหมาะสม
10. สามารถนำ metrics ที่เก็บได้จาก service อื่น ๆ ใน infrastructure เดิมมาแสดงผลผ่าน grafana dashboard ได้อย่างถูกต้องและเหมาะสม
11. สามารถจัดเก็บข้อมูล log ที่ออกมาจาก service ภายใน kubernetes เดิมได้
12. สามารถจัดเก็บข้อมูล log ของ service อื่น ๆ ใน infrastructure เดิมได้
13. สามารถรองรับการจัดเก็บข้อมูล log ที่ออกมาจาก service ที่เพิ่มใน Kubernetes ในอนาคตได้
14. สามารถนำ log ที่เก็บได้จาก Kubernetes และ service ภายในมาแสดงผลผ่าน graylog dashboard ได้อย่างถูกต้องและเหมาะสม
15. สามารถนำ log ที่เก็บได้จาก service อื่น ๆ ใน infrastructure เดิมมาแสดงผลผ่าน graylog dashboard ได้อย่างถูกต้องและเหมาะสม
16. สามารถออกแบบระบบ monitoring ให้กับคอนเทนเนอร์แพลตฟอร์มร่วมกับ service เดิมใน infrastructure ที่มีอยู่
17. สามารถออกแบบระบบ alerting ให้กับคอนเทนเนอร์แพลตฟอร์มร่วมกับ service เดิมใน infrastructure ที่มีอยู่
18. สามารถแจ้งเตือนปัญหาที่อาจจะเกิดขึ้นในระบบได้ผ่าน slack

### 3.3 การออกแบบ (diagram ต่าง ๆ เช่น Use Case, Class, ER พร้อมคำอธิบายอย่างละเอียด)

- 3.3.1 รูป deployment diagram

    ![system-deployment-diagram](./media/system-deployment-diagram.png)

    ในส่วนของ Kubernetes cluster จะมี HAProxy ทำหน้าที่เสมือน load balancer ส่งต่อข้อมูลเข้าไปยัง Kubernetes cluster ที่ Control plane และ worker node โดยใน Kubernetes cluster จะมี component ที่ใช้การเชื่อมต่อเข้ากับ PostgreSQL database

    ในส่วนของ Graylog จะมี HAProxy ทำหน้าที่เหมือน load balancer ส่งต่อข้อมูลไปยัง Graylog Cluster แล้ว Graylog จะทำการส่งข้อมูลที่ได้รับการประมวลผลแล้วเรียบร้อยส่งไปเก็บที่ Elasticsearch

    ในส่วนของเครื่อง Prometheus จะทำหน้าที่ในการรวมและจัดเก็บ metrics ของระบบทั้งหมด

- 3.3.2 รูป network port schematics ของส่วน Kubernetes

    ![system-kubernetes-network-port-schematics](./media/system-kubernetes-network-port-schematics.png)

    ภาพแสดงการใช้งาน port และ protolcol ในส่วนของการเชื่อมต่อกับ Kubernetes cluster

    ในส่วนของ Kubernetes cluster จะมี HAProxy ที่ทำหน้าที่ส่งต่อคำร้องขอไปยังปลายทางจากตัวมันโดยการเชื่อมต่อกับ worker node ภายใน Kubernetes cluster จริง ๆ แล้วสามารถวิ่งเข้าที่ worker node ไหนก็ได้เนื่องจากความสามารถในการทำ network overlay ของ Kubernetes

    การเข้าควบคุม Kubernetes cluster สามารถวิ่งเข้าผ่านทาง port 6443 ของ HAProxy เพื่อให้ HAProxy ส่งต่อคำร้องขอไปยัง kube-api-server เพื่อจัดการ cluster ได้

    ภายใน woker node จะมี ingress-controller ที่ถูกติดตั้งใช้งานแบบ daemon-set ทำหน้าที่ในการจับคู่ domain ที่วิ่งเข้ามาไปยัง service ภายในที่เหมาะสม

- 3.3.3 รูป network port schematics ของส่วน Graylog cluster

    ![system-graylog-network-port-schematics](./media/system-graylog-network-port-schematics.png)

    ภาพแสดงการใช้งาน port และ protolcol ในส่วนของการเชื่อมต่อกับ Graylog cluster

    ในส่วนของ Graylog cluster จะมีการทำเป็น cluster ซึ่งภายในจะประกอบด้วย graylog server ที่คอยรับ logs หรือ request ที่วิ่งเข้ามายัง graylogs ซึ่งแต่ละตัวจะมีการเก็บ configuration ไว้ที่ MongoDB ที่ทำหน้าที่เป็น ReplicaSet ทำให้รองรับการ replicate configuration ไปยัง MongoDB อื่น ๆ ภายในได้

    หลังจากที่ graylog server ได้ทำการจัดการข้อมูลเกี่ยวกับ logs เรียบแล้วก็จะทำการส่งข้อมูลที่ตรงเงื่อนไขเข้าไปเก็บยัง Elasticsearch 1 ใน Elasticsearch cluster

    การประกอบ cluster ของแต่ละเครื่องมือเช่น Graylog, MongoDB และ Elasticsearch ทำให้ระบบมีความสามารถในการทำ High Availability (HA) ที่สูง
  
- 3.3.4 รูป network port schematics ของส่วน Prometheus server

    ![system-prometheus-network-port-schematics](./media/system-prometheus-network-port-schematics.png)

    ภาพแสดงการใช้งาน port และ protolcol ในส่วนของการเชื่อมต่อกับ Prometheus server

    ในส่วนของ Prometheus ที่อยู่นอก Kubernetes cluster จะทำหน้าที่เป็นตัว Centralized Management คือมีการเก็บ Metrics ของ service ทั้งภายในและภายนอก Kubernetes ทั้งหมดไว้ในนี้ เพื่อให้สามารถทำการประมวลผลข้อมูล Metrics ที่มาในรูปแบบ Time-Series และสามารถวิเคราะห์การใช้งานเพื่อรองรับการขยายได้ในอนาคต

### 3.4 สถาปัตยกรรมของระบบ (ภาพรวมของระบบ อธิบายถึงการใช้เทคโนโลยีอะไรบ้าง)

- รูปภาพรวมระบบ

    ![system-architecture](./media/system-architecture.png)

- 3.4.1 ระบบ monitoring

  - 3.4.1.1 ระบบ metrics

    ![system-monitoring-metrics-architecture](./media/system-monitoring-metrics-architecture.png)

    - Prometheus
      - What is prometheus

        ![prometheus-logo](./media/prometheus-logo.png)
        
        https://prometheus.io/

        logo ของ prometheus
        ```txt
        คือ เครื่องมือที่นิยมใช้ในการ monitoring metrics ของ infrastructure หรือ service ถูกออกแบบมาให้สามารถใช้งาน
        กับ infrastructure ที่มีความซับซ้อนเช่น Kubernetes
        ```
      - Prometheus architecture

        ![prometheus-architecture](./media/prometheus-architecture.png)
        
        1. Service
            ```txt
            คือ application ที่ต้องการเก็บข้อมูล metric
            ```
        2. Service Exporter
            ```txt
            คือ software ที่ช่วยในการดึง metrics ให้อยู่ในรูปแบบที่ prometheus สามารถนำมาใช้งานได้
            ```
        3. Push Gateway
            ```txt
            คือ ที่เก็บ metrics สำหรับงานที่ทำในช่วงเวลา ๆ สั้น ๆ แล้วหายไปเนื่องจาก prometheus อาจจะยังไม่มาดึงเอา metrics ไป
            จึงจำเป็นต้องเก็บไว้ใน Push Gateway ก่อน
            ```
        4. Prometheus Server
            ```txt
            ที่รวมการทำงานของ Prometheus component
            ```
        5. ServiceMonitor
            ```txt
            คือ custom resource ของ Kubernetes โดยใช้สำหรับการทำ Auto Discovery หา service ที่เพิ่มขึ้นมาใหม่โดย
            ไม่ต้องทำการแก้ไข Prometheus configuration file
            ```
        6. Alertmanager
            ```txt
            คือ software ทำหน้าที่จัดการการแจ้งเตือนไปยังผู้มีส่วนเกี่ยวข้องกับระบบ โดยจะมี concept การทำงานคือ
            grouping, inhibition, silences, client behavior, high availability
            ``` 
            1. Grouping
                ```txt
                คือ การจัดกลุ่มของ alert ให้เป็นกลุ่มเดียวกัน เช่น application A มี pod1, pod2, pod3 แล้วทั้ง 3 pod ไม่สามารถ
                เชื่อมต่อฐานข้อมูลได้ก็จะมีการยิง alert เพียงแค่ครั้งเดียวคือของ application A
                ```
            2. Inhibition
                ```txt
                คือ การยับยั้งการแจ้งเตือนที่เกี่ยวข้องกัน เช่น กรณีที่ไม่ cluster ไม่สามารถเชื่อมต่อได้ก็จะแจ้งเตือนมา 1 แจ้งเตือนไม่มีแจ้ง
                เตือนอื่น ๆ เกี่ยวกับของใน cluster
                ```
            3. Silences
                ```txt
                คือ การเช็กว่า alert ที่ prometheus ส่งมาให้นั้นเข้ากับเงื่อนไขที่จะส่งการแจ้งเตือนหรือไม่
                ```
            4. Clent Behavior
                ```txt
                คือ การตั้งค่าการแจ้งเตือนกับ request ที่ Prometheus ส่งมา
                ```
            5. High Availability
                ```txt
                คือ ความสามารถทำ Alertmanager ให้เป็น cluster ได้
                ```
            ```yaml
            alertmanager_version: 0.21.0
            alertmanager_config_dir: /etc/alertmanager
            alertmanager_db_dir: /var/lib/alertmanager
            alertmanager_slack_api_url: 'https://hooks.slack.com/services/ABCDEFGH/IJKLMNOPQSTUV/WXYZABCDEFGHIJK'
            alertmanager_template_files: 
              - 'groups/platform_prod_monitoring/template/*.yaml'

            alertmanager_http_config:
              proxy_url: "http://username:password@proxy_address:8080/"

            alertmanager_web_listen_address: 'localhost:9093'
            alertmanager_web_external_url: 'http://localhost:9093/alertmanager'

            alertmanager_smtp: {}

            alertmanager_receivers:
            - name: default
              slack_configs:
              - send_resolved: true 
                title: "{% raw %}{{ if eq .Status \"firing\" }}:warning:{{ else }}:heavy_check_mark:{{ end }} [{{ .Status | toUpper }}]{% endraw %}"
                text: "{% raw %}{{ range .Alerts }}*Priority*: `{{ .Labels.severity | toUpper }}` \n{{ .Annotations.description }}\n{{ end }}{% endraw %}" 

            alertmanager_route:
              group_by: ['alertname', 'env', 'job', 'pod'] 
              group_wait: 60s
              group_interval: 30s
              repeat_interval: 4h
              receiver: default
            ```
            - ตัวอย่าง alertmanager configuration 
            <!-- https://prometheus.io/docs/alerting/latest/alertmanager/ -->
        7. Grafana

            ![grafana-haproxy-dashboard](./media/grafana-haproxy-dashboard.png)

            - ตัวอย่าง grafana-dashboard

            ```txt
            คือ software ที่ใช้สำหรับการทำ Data Visualization จาก metric ที่เก็บไว้ใน Time Series Database
            ```
      ```yaml
      prometheus_web_listen_address: "0.0.0.0:9090"
      prometheus_web_external_url: 'http://localhost:9090/prometheus'

      prometheus_global:
        scrape_interval: 15s
        scrape_timeout: 10s
        evaluation_interval: 15s

      prometheus_scrape_configs:
        - job_name: prometheus
          metrics_path: "{{ prometheus_metrics_path }}"
          static_configs:
            - targets:
                - "{{ ansible_fqdn | default(ansible_host) | default('localhost') }}:9090"
        - job_name: node
          file_sd_configs:
            - files:
                - "{{ prometheus_config_dir }}/file_sd/node.yml"
        - job_name: k8s-prod
          scrape_interval: 15s
          honor_labels: true
          metrics_path: '/prometheus/federate'
          scheme: https
          tls_config:
            insecure_skip_verify: true
          params:
            'match[]':
              - '{job="kube-state-metrics"}'
              - '{job="kubelet"}'
              - '{job="kubernetes-service-endpoints"}'
              - '{job="k8s-blackbox"}'
              - '{job="k8s-blackbox-invoker"}'
          static_configs:
            - targets:
              - "api.co.th"
              labels:
                env: production
                project: project-name
                type: k8s
                service: k8s
          metric_relabel_configs:
            - source_labels: [job]
              regex: 'kubernetes-service-endpoints'
              action: replace
              target_label: job
              replacement: prod-k8s-node-exporter
        - job_name: node-exporter
          metrics_path: /metrics
          static_configs:
          - targets: ['nexus.co.th:9100']
            labels:
              env: production
              project: project-name
              hostname:  nexus.co.th
          - targets: ['jenkins.co.th:9100']
            labels:
              env: production
              project: project-name
              hostname: jenkins.co.th
          - targets: ['pgkong1.co.th:9100']
            labels:
              env: production
              project: project-name
              hostname: pgkong1.co.th
          - targets: ['pgkong2.co.th:9100']
            labels:
              env: production
              project: project-name
              hostname: pgkong2.co.th
          - targets: ['graylog.co.th:9100']
            labels:
              env: production
              project: project-name
              hostname: graylog.co.th
      ```
      - ตัวอย่าง prometheus configuration

  - 3.4.1.2 ระบบ logging

    ![system-monitoring-logs-architecture](./media/system-monitoring-logs-architecture.png)

    - FluentBit
      - What is FluentBit

        ![fluentbit-logo](./media/fluentbit-logo.png)

        - logo ของ fluentbit 
        
        https://fluentbit.io/
        ```
        คือ open source log processor and forwarder โดยสามารถเก็บ log จากหลาย ๆ แหล่งและทำการประมวลผลจัดรูปแบบ log
        ให้เป็นมาตรฐานเดียวกันก่อนจะส่งไปยังที่เก็บเก็บปลายทางโดยไม่ต้องแก้ไข application ที่ติดตั้งไปแล้ว
        ```
      - การทำงานของ Fluentbit

        ![fluentbit-pipeline](./media/fluentbit-pipeline.png)

        1. Input
            ```txt
            คือ สิ่งที่ Fluentbit จะไปเก็บ log
            ```
        2. Parser
            ```txt
            คือ การเปลี่ยน structure ของ log ให้อยู่ในรูปแบบที่กำหนด
            ```
        3. Filter
            ```txt
            คือ การเติมแต่ง log ด้วย metadata ของ Kubernetes
            ```
        4. Buffer
            ```txt
            คือ การจัดเก็บ log ที่ทำการประมวลผลไว้แล้วก่อนจะทำการส่งไปยัง database ที่เกี่ยวข้อง
            ```
        5. Routing
            ```txt
            คือ การจัดการเส้นทางที่จะส่ง log นั้นไปยัง database
            ```
      ```yaml
      [INPUT]
      Name              tail
      Tag               kube.*
      Path              /var/log/containers/*.log
      DB                /var/log/flb_kube.db
      Parser            docker
      Docker_Mode       On
      Mem_Buf_Limit     100MB
      Skip_Long_Lines   On
      Refresh_Interval  1

      [FILTER]
      Name                kubernetes
      Match               kube.*
      Kube_URL            https://organiztion-production.cluster.local:443
      Kube_CA_File        /var/run/secrets/kubernetes.io/serviceaccount/ca.crt
      Kube_Token_File     /var/run/secrets/kubernetes.io/serviceaccount/token
      Merge_Log           On
      Buffer_Size         0
      Use_Kubelet         true
      Kubelet_Port        10250
      ```
      - ตัวอย่างการกำหนดค่าทำงานของ Fluentbit ในส่วนของ Input และ Filter
    - Graylog

      ![graylog-logo](./media/graylog-logo.png)
      
      https://www.graylog.org/
      - What is Graylog
          ```txt
          คือ เป็นเครื่องมือที่ใช้ในการเก็บและวิเคราะห์ log แบบรวมไว้ที่ศูนย์กลาง
          ```
      - Graylog architecture

        ![graylog-production-architecture](./media/graylog-production-architecture.png)

        1. Graylog Server
            ```txt
            คือ เครื่องมือที่ใช้ในการจัดการข้อมูลชุดตัวอักษรและนำมาคัดแยกแลกวิเคราะห์ตามที่ผู้ใช้งานเป็นคนกำหนดและยังสามารถ
            เปิดใช้เครื่องมือการค้นหาแบบกำหนดเองทำให้สามารถวิเคราะห์พฤติกรรมของแอปพลิเคชันได้
            ```
        2. MongoDB

            ![monogodb-logo](./media/mogodb-logo.jpg)

            https://www.glurgeek.com/education/mongodb-%E0%B8%AD%E0%B8%B5%E0%B8%81%E0%B8%AB%E0%B8%99%E0%B8%B6%E0%B9%88%E0%B8%87%E0%B9%81%E0%B8%99%E0%B8%A7%E0%B8%97%E0%B8%B2%E0%B8%87%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%80%E0%B8%81%E0%B9%87%E0%B8%9A/

            ```txt
            คือ NoSQL database ที่ใช้ในการจัดเก็บข้อมูล metadata ของ graylog server
            ```
        3. Elasticsearch
            ```txt
            คือ database ที่ถูกใช้งานในการเก็บข้อมูลชุดตัวอักษรและมีความสามารถในการทำ search engine ในตัว
            ถูกใช้ในการเก็บข้อมูลที่ถูกส่งมาจาก graylog
            ```
      ![graylog-web-page](./media/graylog-web-page.png)
      - รูปหน้าต่าง UI ของ graylog
  
  - 3.4.1.3 ระบบ Tracing

    ![system-monitoring-traces-architecture](./media/system-monitoring-traces-architecture.png)

    - Jaeger
      ![jaeger-logo](./media/jaeger-logo.png)

      <!-- https://www.jaegertracing.io/docs/1.28/architecture/#:~:text=The%20Jaeger%20agent%20is%20a,collectors%20away%20from%20the%20client. -->

      <!-- Jaeger instead of AWS X-RAY
      https://life.wongnai.com/%E0%B8%A3%E0%B8%B5%E0%B8%94-microservice-performance-%E0%B8%9A%E0%B8%99-aws-%E0%B8%95%E0%B8%AD%E0%B8%99%E0%B8%97%E0%B8%B5%E0%B9%88-1-9a5581ba0c02 -->

      - What is Jaeger
          ```txt
          เป็นเครื่องมือที่ใช้สำหรับการเก็บข้อมูลทางสถิติของ request ตั้งแต่เริ่มวิ่งเข้ามายังระบบจนวิ่งกลับไปหาผู้ใช้งานที่ถูกออกแบบมาให้สามารถใช้งานร่วมกับ Microservice ได้ดี
          ```
      - Jaeger architecture

        ![jaeger-architecture](./media/jaeger-architecture.png)

        1. Jaeger-client
            ```txt
            เป็นส่วนที่ทำหน้าที่สร้าง Trace และจัดการ span ภายในก่อนส่งไปให้ Jaeger-agent
            ```
        2. Jaeger-agent
            ```txt
            เป็นส่วนที่ service ของระบบจะทำการยิง Traces ไปให้
            ```
        3. Jaeger collector
            ```txt
            เป็นส่วนที่ทำหน้าที่เก็บรวมรวม Traces data ก่อนจะนำไปเก็บใน datastore
            ```
        4. Database
            ```txt
            เป็นที่เก็บข้อมูล Traces data ของ service ภายในระบบ
            ```
        5. Jaeger-query
            ```txt
            เป็นเครื่องมือที่ใช้ในการดึงเอา tracing data ไปแสดงผลในหน้าต่าง user interface (UI)
            ```
      
      ![jaeger-web-page](./media/traces.jpg)  

- 3.4.2 ระบบ alerting

    ![system-monitoring-alerting-architecture](./media/system-monitoring-alerting-architecture.png)

  - อยู่ในส่วนของ Alertmanager ที่อยู่ภายในเครื่อง Prometheus โดยการกำหนดกฎที่จะใช้แจ้งเตือนได้

    ```yaml
    groups:
      - name: node-exporter
        rules:
        - alert: HostHighCpuLoad
          expr: 100 - ((irate(node_cpu_seconds_total{mode="idle"}[10m])) * 100) >= 90
          for: 30m
          labels:
            severity: warning
            alertType: infra-service
          annotations:
            description: "CPU load is > 90%\n {{ $labels.hostname }} : {{ $labels.instance }}"
            summary: "Host high CPU load (instance {{ $labels.instance }})"
        - alert: HostHighCpuLoad
          expr: 100 - ((irate(node_cpu_seconds_total{mode="idle"}[10m])) * 100) >= 95
          for: 20m
          labels:
            severity: critical
            alertType: infra-service
          annotations:
            description: "CPU load is > 95%\n {{ $labels.hostname }} : {{ $labels.instance }}"
            summary: "Host high CPU load (instance {{ $labels.instance }})"
        - alert: HostHighMemoryUsage
          expr: 100 - (node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes * 100) >= 95
          for: 10m
          labels:
            severity: critical
            alertType: infra-service
          annotations:
            description: "Node memory is > 90%\n {{ $labels.hostname }} : {{ $labels.instance }}"
            summary: "Host out of memory (instance {{ $labels.instance }})"
        - alert: HostHighDiskUsage 
          expr: 100 - (node_filesystem_avail_bytes{mountpoint !~ "/mnt.*|/run.*|/boot.*|/snap.*|/var/lib/lxcfs"}  * 100) / node_filesystem_size_bytes{mountpoint !~ "/mnt.*|/run.*|/boot.*|/snap.*|/var/lib/lxcfs"} >= 90
          for: 10m
          labels:
            severity: critical
            alertType: infra-service
          annotations:
            description: "Disk is > 90%\n {{ $labels.hostname }} : {{ $labels.instance }}\n Mountpoint: {{ $labels.mountpoint}}"
            summary: "Host out of disk space (instance {{ $labels.instance }})"
        - alert: HostDown 
          expr: up{hostname!~"gke.*"} == 0
          for: 1m
          labels:
            severity: critical
            alertType: infra-service
          annotations:
            description: "{{ $labels.hostname }} : {{ $labels.instance }} is down"
            summary: "Host down (instance {{ $labels.instance }})"
    ```
    - ตัวอย่างการกำหนดค่าการแจ้งเตือน Alert Rule ในส่วนของ Node Exporter

    โดยเมื่อระบบมีสภาพแวดล้อมที่ตรงเงื่อนไขการแจ้งเตือนก็จะทำการส่ง alert ไปให้ Alertmanager เพื่อทำการส่ง notification เข้าไปยัง application ที่กำหนด

    ![alertmanager-slack-pic-3](./media/alertmanager-slack-pic-3.png)
    - รูปตัวอย่างแสดงการแจ้งเตือนสถานะ RESOLVED ของ API ในระบบ

- 3.4.3 ระบบ visualization

  - grafana

      ![system-monitoring-grafana-architecture](./media/system-monitoring-grafana-architecture.png)

  จะมีการเขียน PromQL เพื่อดึงเอาข้อมูล Metrics ออกมาแสดงผลแบบกราฟ

  ![grafana-haproxy-setting-dashboard](./media/grafana-haproxy-setting-dashboard.png)
  - รูปตัวอย่าง dashboard ของ grafana ใน 1 panel

## 4 ผลการวิจัย

ผลของการทำงานระบบนั้นสามารถตรวจจับปัญหาที่กำลังเกิดขึ้นและจะเกิดขึ้นได้จากระบบ monitoring ที่ได้ทำการออกแบบทั้ง service ภายใน Kubernetes และ service เดิมของระบบที่มีอยู่

### 4.1 สามารถตรวจกับการทำงานของ Application ภายใน Kubernetes cluster ได้และปรับให้เหมาะสม

- 4.1.1 ปรับการทำงานของ Application จากการทำ Monitoring Tracs

    - 4.1.1.1 ก่อนปรับการทำงานของ Application

        ![traces](./media/traces.jpg)
        - ภาพการทำ tracing ของ service ใน Kubernetes

        ภาพแสดงการเรียกใช้งาน API ของตัวหลักจะเห็นได้ว่าใน 1 ในการทำงานที่เข้ามาในระบบจะมีการเรียกใช้งาน service อื่น ๆ ภายใน Kubernetes อีกเป็นจำนวนหลายครั้งและมีรูปแบบการ Query ดึงข้อมูลแบบเดิม

        ระบบมีเวลา response time เฉลี่ยที่ 0.02 6.82 17.48 21.04 27.25 45.12 วินาที ที่เปอร์เซ็นต์ไทล์ที่ 0 50 90 95 99 และ 100 ตามลำดับโดยมีเวลาเฉลี่ยที่ 8.33 วินาที

        ![loadtest-1000c-before-optimization](./media/loadtest-1000c-before-optimization.png)

        จากผลการทำงานของตารางที่ใช้ Invoker 5 ตัว Loan 4 และ service อื่น ๆ อีก 2 ในแถวสุดท้ายของ[*** ชื่อตาราง ***] จะเห็นได้ว่ามี success อยู่ที่ 45,xxx ถึง 49,xxx ครั้ง และ success rate อยู่ที่ประมาณ 83% - 88% ที่ใช้ 1000 concurrency 

    - 4.1.1.2 หลังจากปรับการทำงานของ Application

        ![traces-version2](./media/traces-version2.png)

        เปลี่ยนเป็นการเรียกใช้งาน API ครั้งเดียวจาก service อื่น ๆ

        ![loadtest-1000c-after-optimization](./media/loadtest-1000c-after-optimization.png)

        จากผลการทำงานของตารางที่ใช้ Invoker 5 ตัว Loan 4 และ service อื่น ๆ อีก 2 ในแถวสุดท้ายของ[*** ชื่อตาราง ***] จะเห็นได้ว่ามี success อยู่ที่ 60,xxx ถึง 77,xxx ครั้ง และ success rate อยู่ที่ประมาณ 90% - 98% ที่ใช้ 1000 concurrency

        ระบบมีเวลา response time ที่ 0.03 4.77 14.21 17.71 25.28 55.68 วินาที ที่เปอร์เซ็นต์ไทล์ที่ 0 50 90 95 99 และ 100 ตามลำดับโดยมีเวลาเฉลี่ยที่ 6.34 วินาที

- 4.1.2 ตรวจพบคอขวดภายในระบบจากการทำ Monitoring Metrics

    - 4.1.2.1 พบคอขวดการทำงานของระบบ

        ![node-bandwidth-usage-2000c](./media/node-bandwidth-usage-2000c.png)
        - ภาพกาใช้งาน network bandwidth ที่ 2000 concurrency

        จากภาพ[*** ชื่อภาพด้านบน ***]จะเห็นได้ว่าระบบมีการใช้งาน bandwidth ที่คงที่ตามจำนวน concurrency ที่ 2000

        ![node-bandwidth-usage-3000c](./media/node-bandwidth-usage-3000c.png)
        - ภาพกาใช้งาน network bandwidth ที่ 3000 concurrency

        เป็นการทดลองทำ capacity test ด้วย concurrency ที่ 3000 จากภาพ[*** ชื่อภาพด้านบน ***]จะเห็นได้ว่าเมื่อระบบทำงานไปได้สักระยะหนึ่ง bandwidth ของระบบจะน้อยลงหรือเทียบเท่าเมื่อมีการใช้งานที่ 2000 concurrency ถึงแม้ว่าจะมีผู้ใช้งานในระบบที่มากขึ้นกว่า 2000 concurrency ก็ตามแสดงให้เห็นถึงความสามารถในการรองรับของระบบ ณ เวลานั้น

## 4.2 ภาพรวมระบบ Monitoring Metrics

สามารถสร้างระบบจัดเก็บ Metrics อื่น ๆ ภายในระบบของ Kubernetes และ service เดิมนอก Kubernetes ไว้ในที่เดียวกันได้เพื่อใช้สำหรับการนำไปวิเคราะห์และประมวลผลได้

![prometheus-centralized-metrics.png](./media/prometheus-centralized-metrics.png)
- รูปภาพการรวม Metrics ไว้ศูนย์กลางเพื่อใช้ในการวิเคราห์และประมวลผล

## 4.3 ภาพรวมระบบ Monitoring Logs

![graylog-centralized-logs.png](./media/graylog-centralized-logs.png)

## 4.4 ภาพรวมระบบ Monitoring Traces

![prometheus-centralized-metrics.png](./media/prometheus-centralized-metrics.png.png)

## 4.5 ภาพรวมระบบ visualization

![grafana-centralized-dashboard.png](./media/grafana-centralized-dashboard.png)

## 4.6 ภาพรวมระบบ alerting

![alertmanager-slack-pic-1.png](./media/alertmanager-slack-pic-1.png)
![alertmanager-slack-pic-2.png](./media/alertmanager-slack-pic-2.png)

(รายละเอียดของผลการทำงานของระบบ ดีขึ้นจากแต่เดิมอย่างไร ด้วยตัวเลขเท่าไหร่ นำข้อมูลมาเปรียบเทียบกัน สำเร็จกี่เปอร์เซ็นต์ ล้มเหลวกี่เปอร์เซ็นต์)

## 5 สรุปผลการวิจัยและข้อเสนอแนะ

(วิเคราะห์ระบบที่สร้าง ข้อดี ข้อเสีย สาเหตุ การแก้ไข ข้อเสนอแนะ)

# 3. ส่วนอ้างอิง