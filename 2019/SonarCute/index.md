# **"CI/CD We Can"** *by #SonarCute*!
---

![](ScopePresentation.jpg "by Khun Ardnarong Boonkerd")

---

## **CI (continuous integration)**

### **Step 1. Create GigHub Project, Create GitLab CI/CD Project, Develop source code**
* **(Maintainer)**

	* Create GitHub Project
		- สร้าง New repository ชื่อ NEIS0736-Project_CI-CD บน Github ของผม
		- เพิ่ม Collaborators ส่วนของผู้ใช้งานหรือ ที่จะมีสิทธิ์เข้ามาทำอะไรได้บ้าง โดยปกติจะเป็น Dev
		- ทั้งนี้ ที่ได้ปรึกษากับพี่อาจ@การเดินทาง  ให้แอดไว้หมดเผื่อให้เข้ามาดูได้ครับ
	* [Create GitLab CI/CD Project](https://ardnarong.github.io/neis0736-cicd/Using%20GitLab%20CI-CD%20with%20a%20GitHub%20repository/)
		- ทำการเชื่อม gitlab กับ github เพื่อให้ เห็น repo  ที่สร้างไว้แล้ว โดยการ new project>CI/CD for external repo>GitHub
		- เราจะเห็นชื่อ repo ที่สร้างไว้บน GitHub. กด Connectแล้ว Go to Project
		- จะถือว่า GitHub = Repo, GitLab = CI/CD พร้อมใช้งานแล้ว
		- ทำการเตรียม Token ของ GitLab Runner  เพื่อส่งต่อให้กับ Sys Admin นำไปใช้สำหรับลงบน Gitlab Runners onTest Server ต่อไป
* **(Developer)**

	* login GitHub และใช้ sonar lint ในการพัฒนาซอสโค้ด


---

### **Step 2. Send GitLab Runner info, Prepare server and install Gitlab Runner**
* **(Maintainer)**
	* [Send Gitlab Runner info เพื่อให้ system admin ทำการ install Gitlab runner](https://ardnarong.github.io/neis0736-cicd/Maintainer%20send%20GitLab%20runner%20token%20to%20System%20Admin/)

* **(System Admin)**
	* [Prepare Server and install Gitlab Runner](https://ardnarong.github.io/neis0736-cicd/System%20Admin%20Prepare%20Server/)

---

### **Step 3. Connect GitHub กับ Sonar Cloud

* **(Maintainer)**
	* ทำการเชื่อมต่อ GitHub กับ Sonar Cloud


---

### **Step 4. Discusstion process CI stage (Build, Test, Deploy)

* **(Maintainer)(System Admin)(Developer)**
	* Process CI Stage
		- ใช้ Docker(docker-compose.yml) test (Review code ) ใช้ Sonar Cloud ทั้งหมดทำงานด้วย .gitlac-ci.ymlDeveloper จึง Commit และ push code ที่ทำการแก้ไขแล้วเสร็จจากการตรวจของ Sonar Cloud ไปให้ Gitlab CI/CD project


---

### **Step 5. UAT

* **(QA / Tester)**
	* ทำ UAT หลังจาก Develop ผ่านการแก้ไขจะเข้าสู่กระบวนการ Change เพื่อทำการ Deploy production


---
# **CD (continuous deployment)**

### **Step 6. Deploy and Monitoring

* **(System Admin)**
	* Deploy production
	* Monitoring


---
* **Team Member**

	1. xxxx
	1. xxxx
	1. xxxx

---

##### **[Software Security - NEIS0736](../) (2019)**!
