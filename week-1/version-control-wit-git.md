---
description: Git Commands Visualized
---

# Version Control wit Git

## Version Control

เมื่อเราเขียนโปรแกรมที่ต้องแก้ไขโค้ดเยอะๆ หรือเขียนโค้ดร่วมกันหลายคน การเซฟไฟล์เป็น code.js cod01.js code\_finale.js ก็จะไม่ตอบโจทย์อีกต่อไป เราจะนิยมเซฟโค้ดโดยใช้ Git ซึ่งมีฟังก์ชัน Version Control ช่วยให้ทำงานง่ายขึ้น เพราะจะทำให้สามารถย้อนกลับโค้ด อัพเดทโค้ด แชร์โค้ดกับทีม สร้างจุดเซฟเพื่อป้องกันโค้ดเสียหาย และยังสามารถเก็บประวัติไฟล์ว่าถูกสร้าง ลบ แก้ไข โดยใคร เมื่อไหร่ อย่างไร&#x20;

โดย Git มีหลายยี่ห้อเช่น Github, Gitlab และ Bitbucket

## Branching Model

คือ การแตกกิ่งก้านสาขาออกมาจากโค้ดหลัก เพื่อเขียนฟีเจอร์บางอย่างเพิ่มเติม หรือทำการแก้ไขบางอย่าง แต่ไม่อยากให้กระทบกับโค้ดหลักและไม่อยากให้วุ่นวายถ้ามีการย้อนเวอร์ชัน โดยจะมีโมเดล Branch หลักๆอยู่สองแบบ

![Github Flow](<../.gitbook/assets/Screen Shot 2565-05-20 at 15.03.51 (2).png>)

**Github Flow**

**จุดเด่น** เหมาะกับ Startup Product ง่าย ไม่ซับซ้อน พัฒนาซอฟแวร์ได้รวดเร็ว

**จุดด้อย** ถ้ามี Bug ในโค้ดแล้ว ย้อนกลับได้ยาก Tester ตรวจงานลำบาก

![Git Flow](<../.gitbook/assets/Screen Shot 2565-05-20 at 15.05.11.png>)

**Git Flow**

**จุดเด่น** เหมาะกับซอฟแวร์ที่ต้องการความถูกต้องสูงก่อนนำไปใช้จริง ทีมพัฒนามีหลายคน หลายทีม Tester สามารถทดสอบได้ง่าย

**จุดด้อย** Release product ได้ช้า เพราะโค้ดต้องถูกตรวจสอบหลายขั้นตอน

และนี่คือตาราง Branch ประเภทต่างๆที่น้องๆต้องพบเจอ

| Branch        | วิธีใช้                                                                                  |
| ------------- | ---------------------------------------------------------------------------------------- |
| main / master | Branch ที่เก็บ source code เวอร์ชั่นหลัก                                                 |
| develop       | Branch ที่ developer เอาโค้ดมารวมกัน โดยโค้ดจะล่าสุดกว่า main                            |
| feature/\*\*  | Branch ที่ developer พัฒนา feature แยกของใครของมัน                                       |
| bugfix/\*\*   | Branch ที่แก้ไข bug ที่โค้ดอยู่ใน main หรือ develop branch                               |
| hotfix/\*\*   | Branch ที่แก้ไข bug เร่งด่วน ที่อยู่บน production แก้แล้วต้องรีบเอาขึ้น production ทันที |
| release/\*\*  | Branch ที่เก็บ source code ที่ขึ้นบน production                                          |

## Development Environment

คือ สภาพแวดล้อมในการพัฒนาซอฟต์แวร์ในแต่ละขั้น โดยจะสอดคล้องกับ Branching model ของ Git โดยแต่ละ Branch จะมี Environment ที่แตกต่างกัน เช่น Feature branch จะมี Environment แบบ Develop Environment และ Main branch จะมี Environment แบบ Production Environment

Environment แบบต่างๆ มีดังนี้

| Environment                                    | รูปแบบการใช้งาน                                                                         |
| ---------------------------------------------- | --------------------------------------------------------------------------------------- |
| prod, production                               | Environment จริงที่เอาโค้ดขึ้นให้ user ใช้งาน                                           |
| preprod, uat (User acceptance test)            | สำหรับทดสอบโค้ด และ Infrastructure ที่คล้ายกับบน Production                             |
| rc (Release candidate), qa (Quality assurance) | สำหรับให้ Tester snapshot โค้ดสำหรับทดสอบหลายๆ ฟีเจอร์สพร้อมกัน มักใช้ร่วมกับการติด Tag |
| dev, development                               | ไว้ใช้สำหรับโค้ดที่อยู่ใน branch develop, main หรือ master                              |
| test                                           | ไว้ใช้สำหรับทดสอบ branch ที่เปิด Pull Request ก่อน merge เข้า branch หลัก               |
| poc (Proof of concept)                         | ไว้ใช้สำหรับ POC โค้ด มักใช้ร่วมกับ branch poc/\*\*                                     |

## Github

คือ Git website ที่สามารถเข้าถึงและอัพโหลดข้อมูลผ่านทางเว็บ [**Github**](https://github.com/) ได้เลย โดยตัวเว็บมีส่วนประกอบดังนี้

![หน้าตาเว็บไซต์ Github](<../.gitbook/assets/Screen Shot 2565-05-20 at 15.12.24.png>)

| ส่วนประกอบ        | ความหมาย                                                                                                                                                      |   |   |   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | - | - | - |
| repository        | ชื่อโปรเจ็ค                                                                                                                                                   |   |   |   |
| clone             | ดาวน์โหลด source code จาก git server มาไว้ที่เครื่องตัวเอง (local)                                                                                            |   |   |   |
| commit            | จุดเซฟ                                                                                                                                                        |   |   |   |
| commit message    | ข้อความอธิบายจุดเซฟ                                                                                                                                           |   |   |   |
| push              | การเอาโค้ดจากจุดเซฟอัพโหลดขึ้น git server                                                                                                                     |   |   |   |
| branch            | การแยกโค้ดจากจุดๆ นึง มาทำต่อ โดยที่แก้ไขแล้วไม่กระทบกับโค้ดหลัก                                                                                              |   |   |   |
| pull              | การอัพเดทโค้ดที่อยู่ในเครื่องตัวเอง กับโค้ดใน git server                                                                                                      |   |   |   |
| pull request (PR) | การขออนุมัติรวมโค้ดจาก branch ที่ทำกับโค้ดใน branch หลัก                                                                                                      |   |   |   |
| merge             | การอนุมัติการรวมโค้ดเข้าสู่ branch หลัก                                                                                                                       |   |   |   |
| conflict          | เมื่อเราเขียนโค้ดร่วมกันหลายๆ คน อาจมีการแก้ไขโค้ดที่ต่างกันในจุดเดียวกัน เมื่อเอาโค้ดมา merge รวมกัน ดังนั้นจึงเกิด conflict ซึ่งเราต้องเลือกว่าจะใช้โค้ดไหน |   |   |   |

## Git Command

| Command      | Examples                                             | วิธีใช้                                                                                                 |
| ------------ | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| git clone    | git clone git@github.com:soAcademy/food-menu-app.git | ดาวน์โหลดโปรเจ็คจาก git server ลงเครื่องตัวเอง                                                          |
| git checkout | git checkout -b feature/sp01-test-git                | สร้าง branch ใหม่ จาก branch หลักที่อยู่                                                                |
| git status   | git status                                           | แสดงรายชื่อและสถานะไฟล์ที่อยู่ใน commit                                                                 |
| git add      | git add . git add file1.js file2.js                  | เพิ่มทุกไฟล์ลงใน commit เพิ่มเฉพาะไฟล์ที่ระบุใน commit                                                  |
| git commit   | git commit -m “add new feature”                      | กำหนดชื่อของ commit ที่จะอัพโหลด                                                                        |
| git push     | git push -u origin feature/sp01-test-git git push    | อัพโหลดโค้ดใน commit ใช้ตอนสร้าง branch ใหม่ อัพโหลดโค้ดใน commit ใช้ตอนเคยอัพโหลดไปแล้ว                |
| git pull     | git pull git pull origin main                        | ดึงโค้ดล่าสุดจาก git server มายัง branch ปัจจุบัน ดึงโค้ดล่าสุดจาก branch main มารวมกับ branch ปัจจุบัน |
| git branch   | git branch git branch -D feature/sp01-temp           | แสดงรายชื่อ branch ทั้งหมดในเครื่องตัวเอง ลบ branch feature/sp01-temp จากในเครื่องตัวเองทิ้ง            |
