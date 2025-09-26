[![Fork Button](https://img.shields.io/github/forks/Hajar-Moumou/Real-Time-Chat-Application?style=social)](https://github.com/Hajar-Moumou/Real-Time-Chat-Application/fork)

# Real-Time Chat Application

Welcome to the **Full Stack Realtime Chat App** project, where we're building a scalable and secure real-time chat experience using the latest technologies. Whether you're a seasoned developer or a beginner, we invite you to contribute and be a part of this exciting journey!

## 📑 Table of Contents

- [Introduction](#-introduction)
- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Getting Started](#-getting-started)
- [Building the Backend](#-building-the-backend)
- [Running the Application](#-running-the-application)
- [Contributing](#-contributing)
- [Future Plans](#-future-plans)
- [License](#-license)

---

## 📝 Introduction

This project provides a **real-time chat application** that is both **scalable** and **secure**. It’s built with modern technologies to ensure a **user-friendly, maintainable, and extensible** platform.

---

## ✨ Features

- **Real-time Messaging**: Instant chat using Socket.io  
- **User Authentication & Authorization**: Secure access with JWT  
- **Scalable & Secure Architecture**: Handles high traffic and data  
- **Modern UI Design**: Built with React + TailwindCSS + DaisyUI  
- **Profile Management**: Users can upload/update profile pictures  
- **Online Status**: Real-time online/offline presence  
- **Future Enhancements**: Planned Kubernetes orchestration and CI/CD  

---

## 🛠️ Tech Stack

- **Backend:** Node.js, Express, MongoDB, Socket.io  
- **Frontend:** React, TailwindCSS, Zustand, DaisyUI  
- **Containerization:** Docker  
- **Orchestration:** Kubernetes (planned)  
- **Web Server:** Nginx  
- **Authentication:** JWT  

---

### 🔧 Prerequisites

- **[Node.js](https://nodejs.org/)** (v14+)  
- **[Docker](https://www.docker.com/get-started)**  
- **[Git](https://git-scm.com/downloads)**  

---

### 📝 Environment Configuration

Create a `.env` file in the root directory:

```env
# Database Configuration
MONGODB_URI=mongodb://root:admin@mongo:27017/chatApp?authSource=admin&retryWrites=true&w=majority

# JWT Configuration
JWT_SECRET=your_jwt_secret_key

# Server Configuration
PORT=5001
NODE_ENV=production

# Clone the repository
git clone https://github.com/Hajar-Moumou/Real-Time-Chat-Application.git
cd Real-Time-Chat-Application

# 1️⃣ Using Docker Compose to build and run all containers
docker-compose up -d --build

# 2️⃣ Manual Docker Setup (if not using docker-compose)
# Create a Docker network
docker network create full-stack

# Build & Run the Frontend container
cd frontend
docker build -t full-stack_frontend .
docker run -d --network=full-stack -p 5173:5173 --name frontend full-stack_frontend:latest

# Run MongoDB container
docker run -d -p 27017:27017 --name mongo mongo:latest

# Build & Run the Backend container
cd ../backend
docker build -t full-stack_backend .
docker run -d --network=full-stack --add-host=host.docker.internal:host-gateway -p 5001:5001 --env-file ../.env full-stack_backend

# ✅ Verify backend ↔ database connection
docker-compose logs -f
