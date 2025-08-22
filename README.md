Ở đây sẽ hướng dẫn cách tải PGVector về dựa trên docker Desktop
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

Bước 6: Vô localhost:5050
Bước 7: đăng nhập với username: user@domain.com, password: password
Bước 8: Ấn vô Servers chuột phải -> Register ->
    General:
        name: postgres
    Connection:
        Host name/address: host.docker.internal
        port: 5432
        database name: postgres
        username: postgres
        password: password