# **"CI/CD We Can"** *by #SonarCute*!
---

![](ScopePresentation.jpg "by Khun Ardnarong Boonkerd")

# **CI/CD Process**
![](https://github.com/c61213oN/c61213on.github.io/blob/master/CICD_Process.png)


---

## **CI (continuous integration)**

### **Step 1. Create GigHub Project, Create GitLab CI/CD Project, Develop source code**
* **(Maintainer)**

	* Create GitHub Project
		- สร้าง New repository บน GitHub
		- เพิ่ม Collaborators ส่วนของผู้ใช้งานหรือ ที่จะมีสิทธิ์เข้ามาทำอะไรได้บ้าง โดยปกติจะเป็น Dev
	* [Create GitLab CI/CD Project](https://ardnarong.github.io/neis0736-cicd/Using%20GitLab%20CI-CD%20with%20a%20GitHub%20repository/)
		- ทำการเชื่อม gitlab กับ github เพื่อให้ เห็น repo  ที่สร้างไว้แล้ว โดยการ new project>CI/CD for external repo>GitHub
		- เราจะเห็นชื่อ repo ที่สร้างไว้บน GitHub. กด Connectแล้ว Go to Project
		- จะถือว่า GitHub = Repo, GitLab = CI/CD พร้อมใช้งานแล้ว
		- ทำการเตรียม Token ของ GitLab Runner  เพื่อส่งต่อให้กับ Sys Admin นำไปใช้สำหรับลงบน Gitlab Runners onTest Server ต่อไป
* **(Developer)**

	* [login GitHub และใช้ sonar lint ในการพัฒนาซอสโค้ด](https://ardnarong.github.io/neis0736-cicd/Improving%20code%20quality%20with%20SonarQube/)


---

### **Step 2. Send GitLab Runner info, Prepare server and install Gitlab Runner**
* **(Maintainer)**
	* [Send Gitlab Runner info เพื่อให้ system admin ทำการ install Gitlab runner](https://ardnarong.github.io/neis0736-cicd/Maintainer%20send%20GitLab%20runner%20token%20to%20System%20Admin/)

* **(System Admin)**
	* [Prepare Server and install Gitlab Runner](https://ardnarong.github.io/neis0736-cicd/System%20Admin%20Prepare%20Server/)

---

### **Step 3. Connect GitHub กับ Sonar Cloud**

* **(Maintainer)**
	* [ทำการเชื่อมต่อ GitHub กับ Sonar Cloud](https://ardnarong.github.io/neis0736-cicd/github-and-sonarcloud/)


---

### **Step 4. Discusstion process CI stage (Build, Test, Deploy)**

* **(Maintainer)(System Admin)(Developer)**
	* Process CI Stage
		- [ใช้ Docker(docker-compose.yml) test (Review code ) ใช้ Sonar Cloud ทั้งหมดทำงานด้วย .gitlac-ci.ymlDeveloper จึง Commit และ push code ที่ทำการแก้ไขแล้วเสร็จจากการตรวจของ Sonar Cloud ไปให้ Gitlab CI/CD project](https://ardnarong.github.io/neis0736-cicd/Improving%20code%20quality%20with%20SonarQube/images/img%20(4).png)


---

### **Step 5. UAT**

* **(QA / Tester)**
	* ทำ UAT หลังจาก Develop ผ่านการแก้ไขจะเข้าสู่กระบวนการ Change เพื่อทำการ Deploy production
		- Test Case-Add User
			- Preconditons :
				1. ระบบที่เปิดให้บริการ
				2. ข้อมูลของ User ที่จะต้องทำการ Add
			- Aciton : 
				1. Login เข้าสู่ระบบ
				2. เข้าเมนู User
				3. กดปุ่ม “+Add New”
				4. กรอกข้อมูลของ User ที่ต้องทำการ Add
				5. กดปุ่ม “Submit” เพื่อเพิ่ม User
			- Input : 
				1. Full name
				2. Email Address
				3. Default Password
				4. Mobile Number
				5. Role
			- Expected Result :
				1. เพิ่มข้อมูลของ User ที่ต้องการ Add
					![](https://github.com/c61213oN/c61213on.github.io/blob/master/CICD_adduser01.png)
				2. สามารถ Add User ได้โดยไม่เกิด Error
					![](https://github.com/c61213oN/c61213on.github.io/blob/master/CICD_adduser01.png)
				3. มี User ที่ทำการเพิ่ม อยู่ในระบบ
					![](https://github.com/c61213oN/c61213on.github.io/blob/master/CICD_adduser01.png)

		- Test Case-Delete User
			- Preconditons :
				1. ระบบที่เปิดให้บริการ
				2. User ในระบบ
			- Aciton : 
				1. Login เข้าสู่ระบบ
				2. เข้าเมนู User
				3. เลือก User ที่ต้องการแก้ไขข้อมูล
				4. กดปุ่ม Delete เพื่อลบ User
			- Input : 
				1. User
			- Expected Result :
				1. [แสดงข้อความ “Are you sure to delete this user ?” ก่อนทำการลบ User](CICD_deluser01.png)
				2. [แสดงข้อความ “User successfully deleted” เพื่อให้ทราบว่าทำการลบ User สำเร็จ](CICD_deluser02.png)
				3. [ในระบบไม่มี User ที่ทำการลบไปแล้ว](CICD_deluser03.png)
		
		- Test Case-Edit User
		
			- Preconditons :
				1. ระบบที่เปิดให้บริการ
				2. ข้อมูลของ User ที่จะต้องทำการ Add
			- Aciton : 
				1. Login เข้าสู่ระบบ
				2. เข้าเมนู User
				3. กดปุ่ม “+Add New”
				4. กรอกข้อมูลของ User ที่ต้องทำการ Add
				5. กดปุ่ม “Submit” เพื่อเพิ่ม User
			- Input : 
				1. Full name
				2. Email Address
				3. Default Password
				4. Mobile Number
				5. Role
			- Expected Result :
				1. [เพิ่มข้อมูลของ User ที่ต้องการ Add](CICD_adduser01.png)
				2. [สามารถ Add User ได้โดยไม่เกิด Error](CICD_adduser02.png)
				3. [มี User ที่ทำการเพิ่ม อยู่ในระบบ](CICD_adduser03.png)
				
		- Test Case-Login Fail
			- Preconditons :
				1. ระบบที่เปิดให้บริการ
				2. ข้อมูลของ User ที่จะต้องทำการ Add
			- Aciton : 
				1. Login เข้าสู่ระบบ
				2. เข้าเมนู User
				3. กดปุ่ม “+Add New”
				4. กรอกข้อมูลของ User ที่ต้องทำการ Add
				5. กดปุ่ม “Submit” เพื่อเพิ่ม User
			- Input : 
				1. Full name
				2. Email Address
				3. Default Password
				4. Mobile Number
				5. Role
			- Expected Result :
				1. [เพิ่มข้อมูลของ User ที่ต้องการ Add](CICD_adduser01.png)
				2. [สามารถ Add User ได้โดยไม่เกิด Error](CICD_adduser02.png)
				3. [มี User ที่ทำการเพิ่ม อยู่ในระบบ](CICD_adduser03.png)
		
		- Test Case-Login Success
			- Preconditons :
				1. ระบบที่เปิดให้บริการ
				2. ข้อมูลของ User ที่จะต้องทำการ Add
			- Aciton : 
				1. Login เข้าสู่ระบบ
				2. เข้าเมนู User
				3. กดปุ่ม “+Add New”
				4. กรอกข้อมูลของ User ที่ต้องทำการ Add
				5. กดปุ่ม “Submit” เพื่อเพิ่ม User
			- Input : 
				1. Full name
				2. Email Address
				3. Default Password
				4. Mobile Number
				5. Role
			- Expected Result :
				1. [เพิ่มข้อมูลของ User ที่ต้องการ Add](CICD_adduser01.png)
				2. [สามารถ Add User ได้โดยไม่เกิด Error](CICD_adduser02.png)
				3. [มี User ที่ทำการเพิ่ม อยู่ในระบบ](CICD_adduser03.png)


---
# **CD (continuous deployment)**

### **Step 6. Deploy and Monitoring**

* **(System Admin)**
	* [Deploy production](https://ardnarong.github.io/neis0736-cicd/deploy/)
	* Monitoring


---
* **Team Member**

	1. คุณ ธนพัฒน์ อ่อนสี 6117810004 หน้าที่รับผิดชอบ : Tester
	1. คุณ พงศ์พัฒน์  เพ็ชรไชย  6117810009 หน้าที่รับผิดชอบ : Tester
	1. คุณ Suparath Suwannakorth 6117670003 หน้าที่รับผิดชอบ : Maintainer
	1. คุณ รักษพล ลีลาฉัตร 6117810001 หน้าที่รับผิดชอบ : System Admin
	1. คุณ ศิริมงคล วงค์ฟู 6117810003 หน้าที่รับผิดชอบ : Tester
	1. คุณ อาจณรงค์ บุญเกิด หน้าที่รับผิดชอบ : Developer
	1. คุณอังคาร ภุมรินทร์ หน้าที่รับผิดชอบ : Secretary

---

##### **[Software Security - NEIS0736](../) (2019)**!
