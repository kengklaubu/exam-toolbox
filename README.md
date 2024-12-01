# 1. สร้าง repository บน GitHub
gh repo create web-project --public --confirm

# 2. สร้างโฟลเดอร์โปรเจคและเข้าไปที่โฟลเดอร์นั้น
mkdir web-project
cd web-project

# 3. เริ่มต้น Git repository
git init

# 4. เชื่อมต่อกับ GitHub repository
git remote add origin https://github.com/kengklaubu/web-project.git

# 5. สร้างไฟล์ README.md และ .gitignore
echo "# Web Project" > README.md
echo "node_modules/" > .gitignore

# 6. เพิ่มไฟล์ไปยัง staging area
git add .

# 7. ทำการ commit
git commit -m "Initial commit"

# 8. เปลี่ยนชื่อ branch เป็น main  #กรณีไม่มีปัญหาให้ข้ามไปรันขอที่ 13 ได้เลย
git branch -M main

# 9. ดึงข้อมูลจาก GitHub (ถ้ามีข้อผิดพลาด "rejected main -> main")
git pull origin main --allow-unrelated-histories

# 10. แก้ไขความขัดแย้ง (ถ้ามี) และบันทึกไฟล์

# 11. เพิ่มไฟล์ที่ถูกแก้ไขเข้า staging area
git add .

# 12. ทำการ commit
git commit -m "Resolved conflicts and merged with GitHub"

# 13. Push โค้ดไปที่ GitHub
git push -u origin main
