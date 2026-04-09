## C. CẤU HÌNH DOCKER COMPOSE

---

### 1. TẠO THƯ MỤC: ~/myapp

`mkdir -p ~/myapp`

<img width="365" height="43" alt="{09CEBFB8-D719-4DD4-8C7A-A3002522E165}" src="https://github.com/user-attachments/assets/8edf652d-341d-4f59-9b66-65b13f63e722" /></p>

### 2. CHUYỂN ĐẾN THƯ MỤC ~/myapp

`cd ~/myapp`

<img width="331" height="33" alt="{E9969C2A-5628-429C-B983-6B942A44F863}" src="https://github.com/user-attachments/assets/789abcbd-20f0-4502-ab7b-1252e8fc8151" /></P>

### 3. TẠO THƯ MỤC: ./myweb

`mkdir -p myweb nginx nodered`

<img width="479" height="37" alt="{64DC43BB-B147-4371-B446-51546F7BA798}" src="https://github.com/user-attachments/assets/6c30c849-0a76-4e93-8d18-6a388518a0fc" /></p>

### 4. TẠO FILE: ./myweb/index.html

<img width="598" height="525" alt="{D779D714-F35B-45A9-8A4F-900CCAB7AD73}" src="https://github.com/user-attachments/assets/56e694b7-89e5-406b-a278-2bbb645efa73" /></p>

### 5. TẠO FILE: docker-compose.yml

<img width="585" height="506" alt="{7B216452-8CA6-4E0D-B32C-7998EB13AFBD}" src="https://github.com/user-attachments/assets/d7dc0c16-1080-411d-adc1-288eab472a97" /></p>

### 6. EDIT FILE: ./nginx/nginx.conf

- Cấu hình web server cổng 80

- server_name là sub-domain (sub-domain tuỳ ý)

- location / trỏ tới root là thư mục /myweb

- location /api dùng proxy_pass trỏ tới 1 (hoặc nhiều) node http_in của nodered

<img width="721" height="550" alt="{33A11438-4CE9-42D2-B368-D27AECA22216}" src="https://github.com/user-attachments/assets/53b50f44-58a6-4e89-809e-8c56e5e34cdd" /></p>

### 7. EDIT FILE: ./nodered/settings.js để nodered bắt buộc đăng nhập

Bước 1: Chạy lệnh 

`cd ~/myapp`

`docker compose up -d`

Bước 2: Kiểm tra container

`docker compose ps`

<img width="1100" height="160" alt="{124CF543-6CFE-4717-A010-84B62C9687A7}" src="https://github.com/user-attachments/assets/86d55da1-c89a-41e5-80b6-fdbad414e604" /></p>

Bước 3: Sửa ./nodered/settings.js để Node-RED bắt buộc đăng nhập

a) Tạo password hash

`node-red-admin hash-pw`

<img width="689" height="82" alt="{1FED348F-E5C2-4A23-A4E0-C5D421536AA5}" src="https://github.com/user-attachments/assets/e04f28bf-3ce5-47d4-826a-256c6aaf6614" /></p>

b) Mở file settings.js

`nano ~/myapp/nodered/settings.js`

<img width="1176" height="713" alt="{17727E90-07EB-4E5C-8003-7294873526B9}" src="https://github.com/user-attachments/assets/62a38bc9-4aab-480d-8c02-af6e8be98b8c" />,/p>

- Tìm phần module.exports = { }, sửa PASSWORD

c) kiểm tra 

- Nodered: `http://172.24.250.160:1880`

<img width="1916" height="1080" alt="image" src="https://github.com/user-attachments/assets/15d53d33-9b98-4a60-9614-21598c1ba3f9" /></p>

- Nginx: `http://172.24.250.160`

<img width="1920" height="1080" alt="{C1356B06-2377-4E57-B42F-190847747391}" src="https://github.com/user-attachments/assets/197d38af-a702-47d4-956b-21b9f7a2baa2" /></p>
