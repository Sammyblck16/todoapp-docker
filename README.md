# 🐳 TodoApp - Multi-Stage Docker Build (Day 3/40)

This project demonstrates how to use a multi-stage Docker build for a simple Node.js + React web app, following Day 3 of the CKA Full Course 2024.

---

## 📸 Screenshots

### ✅ Cloning the Repository
![Clone Repo](screenshots/Screenshot%202025-06-21%20at%207.21.46%E2%80%AFPM.png)

### 🛠 Writing Dockerfile and Building the Image
![Build Docker](screenshots/Screenshot%202025-06-21%20at%207.22.26%E2%80%AFPM.png)

### 📤 Docker Login, Tag & Push
![Docker Tag & Push](screenshots/Screenshot%202025-06-21%20at%207.23.33%E2%80%AFPM.png)

---

## 🧰 Technologies Used
- Node.js (18-alpine)
- NGINX (for serving production build)
- Docker (multi-stage build)
- DockerHub (for publishing images)

---

## 🏁 Getting Started

### 🔁 Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/todoapp-docker.git
cd todoapp-docker
```

### 🧱 Create Dockerfile
Create a file named `Dockerfile` and paste the following:

```Dockerfile
FROM node:18-alpine AS installer
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx:latest AS deployer
COPY --from=installer /app/build /usr/share/nginx/html
```

---

## 🧪 Build and Run Locally

### 📦 Build Docker Image
```bash
docker build -t todoapp-docker .
```

### ▶️ Run Docker Container
```bash
docker run -dp 3000:80 todoapp-docker
```

Now open your browser and visit: [http://localhost:3000](http://localhost:3000)

---

## 🚀 Push to DockerHub

### 🔐 Login to DockerHub
```bash
docker login
```

### 🏷️ Tag the Image
```bash
docker tag todoapp-docker:latest chimaiberi1990/todoapp-docker:latest
```

### ☁️ Push to DockerHub
```bash
docker push chimaiberi1990/todoapp-docker:latest
```

---

## 🔍 Useful Docker Commands

### Enter the Running Container
```bash
docker exec -it <container_id_or_name> sh
```

### View Container Logs
```bash
docker logs <container_id_or_name>
```

### Clean Up Image
```bash
docker image rm <image_id>
```

---

## 📁 Project Structure

```
todoapp-docker/
├── Dockerfile
├── README.md
├── package.json
├── package-lock.json
├── public/
└── src/
```

---

## 🙌 Author

**Chimaobi Samuel Iberi**  
[DockerHub: chimaiberi1990](https://hub.docker.com/u/chimaiberi1990)

---

## 📝 License

This project is part of a public tutorial and is free to use for learning purposes.
# A sample todo app in react
