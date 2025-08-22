Hướng dẫn cài đặt PGVector với Docker Desktop
Bước 1: Kéo image PostgreSQL có PGVector
docker pull pgvector/pgvector:pg16

Bước 2: Tạo volume lưu dữ liệu
docker volume create pgvector-data

Bước 3: Chạy container PostgreSQL với PGVector
docker run --name pgvector-container -e POSTGRES_PASSWORD=password -p 5432:5432 -v pgvector-data:/var/lib/postgresql/data -d pgvector/pgvector:pg16

Bước 4: Kéo image PGAdmin
docker pull dpage/pgadmin4

Bước 5: Chạy container PGAdmin
docker run --name pgadmin-container -p 5050:80 -e PGADMIN_DEFAULT_EMAIL=user@domain.com -e PGADMIN_DEFAULT_PASSWORD=password -d dpage/pgadmin4

Bước 6: Truy cập PGAdmin
Mở trình duyệt và truy cập:
localhost:5050

Bước 7: Đăng nhập
Đăng nhập với thông tin:

Username: user@domain.com

Password: password

Bước 8: Kết nối tới server PostgreSQL
Ấn chuột phải vào Servers -> Register -> Server...

Tab General:

Name: postgres

Tab Connection:

Host name/address: host.docker.internal

Port: 5432

Database name: postgres

Username: postgres

Password: password
