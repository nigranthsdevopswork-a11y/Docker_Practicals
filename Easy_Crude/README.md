🌐 STEP 1: NETWORK CREATE
docker network create mynetwork

👉 WHY:
Sab containers ek hi network me rahenge → naam se baat karenge

💾 STEP 2: VOLUME CREATE (IMPORTANT)
docker volume create db_data

👉 WHY:
Database ka data container ke bahar store hoga
👉 container delete ho gaya → data safe

🗄️ STEP 3: DATABASE (MariaDB) RUN
docker run -d \
--name mariadb_count \
--network mynetwork \
-e MYSQL_ROOT_PASSWORD=root \
-e MYSQL_DATABASE=student_db \
-e MYSQL_USER=admin \
-e MYSQL_PASSWORD=admin \
-v db_data:/var/lib/mysql \
-p 3306:3306 \
mariadb:latest
🧠 Explanation
--network mynetwork → backend connect kar sake
-e → DB credentials set
-v db_data:/var/lib/mysql → data persist 🔥
-p 3306:3306 → external access (optional)
☕ STEP 4: BACKEND CONFIG (MOST IMPORTANT ⚠️)

Open:

backend/src/main/resources/application.properties

Replace:

spring.datasource.url=jdbc:mysql://mariadb_count:3306/student_db
spring.datasource.username=admin
spring.datasource.password=admin

spring.jpa.hibernate.ddl-auto=update
spring.jpa.database-platform=org.hibernate.dialect.MySQLDialect
🧠 WHY?

👉 mariadb_count = container name
👉 Docker network me ye DNS ki tarah kaam karta hai

❌ localhost use nahi karna
❌ RDS abhi use nahi karna

🏗️ STEP 5: BACKEND IMAGE BUILD
cd backend
docker build -t backend:latest .

👉 WHY:
Code → image ban raha hai (portable app)

🚀 STEP 6: BACKEND RUN
docker run -d \
--name backend_count \
--network mynetwork \
-p 8080:8080 \
backend:latest
🔍 STEP 7: CHECK
docker ps

👉 Output me hona chahiye:

mariadb_count ✅
backend_count ✅
🧪 STEP 8: TEST BACKEND
curl http://localhost:8080

👉 Agar response aaya → backend working

🌐 Browser me
http://<EC2-PUBLIC-IP>:8080
🎨 STEP 9: FRONTEND RUN
cd ../frontend
docker build -t frontend .
docker run -d -p 80:80 frontend

👉 Browser:

http://<EC2-PUBLIC-IP>
🔗 IMPORTANT (Frontend → Backend connect)

Agar frontend me API URL hardcoded hai:

❌ galat:

http://localhost:8080

✅ sahi:

http://<EC2-PUBLIC-IP>:8080
🔥 FINAL ARCHITECTURE
User → Frontend (80)
        ↓
     Backend (8080)
        ↓
     MariaDB (volume attached)
💥 TU NE KYA SEEKH LIYA
✅ Docker Image + Container
✅ Network (container communication)
✅ Volume (data safe)
✅ Backend-DB connection
✅ Cloud deployment (EC2)
