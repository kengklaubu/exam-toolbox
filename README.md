1. สร้าง repository บน GitHub  
gh repo create web-project --public --confirm

2. สร้างโฟลเดอร์โปรเจคและเข้าไปที่โฟลเดอร์นั้น  
mkdir web-project
cd web-project

3. เริ่มต้น Git repository  
git init

4. เชื่อมต่อกับ GitHub repository  
git remote add origin https://github.com/kengklaubu/web-project.git

5. สร้างไฟล์ README.md และ .gitignore  
echo "# Web Project" > README.md
echo "node_modules/" > .gitignore

6. เพิ่มไฟล์ไปยัง staging area  
git add .

7. ทำการ commit  
git commit -m "Initial commit"

8. เปลี่ยนชื่อ branch เป็น main  #กรณีไม่มีปัญหาให้ข้ามไปรันขอที่ 13 ได้เลย  
git branch -M main

9. ดึงข้อมูลจาก GitHub (ถ้ามีข้อผิดพลาด "rejected main -> main")  
git pull origin main --allow-unrelated-histories

10. แก้ไขความขัดแย้ง (ถ้ามี) และบันทึกไฟล์  

11. เพิ่มไฟล์ที่ถูกแก้ไขเข้า staging area
git add .

12. ทำการ commit
git commit -m "Resolved conflicts and merged with GitHub"

13. Push โค้ดไปที่ GitHub
git push -u origin main

14. กลับไปที่โฟลเดอร์หลัก (ถ้ามีการย้ายออก)
cd ..

15. ลบ directory และ clone ใหม่  
rmdir /s /q web-project  
git clone https://github.com/kengklaubu/web-project.git

16. สร้าง branches สำหรับฟังก์ชันต่างๆ  
cd web-project  
git checkout -b feature/show_courses  
git checkout -b feature/search_by_code  
git checkout -b feature/search_by_name  
git checkout -b feature/edit_course_by_code  
git checkout -b feature/delete_course_by_code  

18. ทำการ commit และ push ไปที่ GitHub
git add .
git commit -m "Add feature to show courses"

git push -u origin feature/show_courses  
git push -u origin feature/search_by_code  
git push -u origin feature/search_by_name  
git push -u origin feature/edit_course_by_code  
git push -u origin feature/delete_course_by_code


19. สร้าง Dockerfile สำหรับโปรเจค  
echo FROM python:3.9-slim > Dockerfile  
echo WORKDIR /app >> Dockerfile  
echo COPY requirements.txt . >> Dockerfile  
echo RUN pip install -r requirements.txt >> Dockerfile  
echo COPY . . >> Dockerfile  
echo CMD ["python", "app.py"] >> Dockerfile



20. สร้างไฟล์ requirements.txt  
echo flask > requirements.txt  
echo requests >> requirements.txt  
echo gunicorn >> requirements.txt

21. สร้างไฟล์ Python app.py #สามารถใช้ print("Hello world")เฉยๆก็ได้  
echo from flask import Flask, jsonify > app.py  
echo app = Flask(__name__) >> app.py  
echo @app.route('/') >> app.py  
echo def hello_world(): >> app.py  
echo     return jsonify(message='Hello, World!') >> app.py  
echo "" >> app.py  
echo if __name__ == '__main__': >> app.py  
echo     app.run(host='0.0.0.0', port=8000) >> app.py  


22. สร้าง Docker image  
docker build -t web-project .

23. รัน Docker container  
docker run -p 8000:8000 web-project
