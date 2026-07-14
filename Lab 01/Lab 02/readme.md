# Lab 2: Developing and Deploying a REST API to Store Data on Cloud

## 📌 Objectives

- Launch and configure an AWS EC2 instance.
- Create a Python virtual environment (`venv`).
- Install FastAPI, Uvicorn, and TinyDB.
- Develop REST API endpoints using FastAPI.
- Store temperature and humidity data with timestamps.
- Test the REST API using HTTP GET and POST requests.

---

## 📖 Background Theory

### Cloud Computing in IoT Systems

Cloud computing enables IoT devices to securely store, process, and retrieve data over the internet. It provides scalable infrastructure, high availability, and centralized data management, making it ideal for IoT applications.

### AWS EC2 (Elastic Compute Cloud)

Amazon EC2 provides virtual servers that allow developers to deploy applications in the cloud. It offers flexible computing resources that can be configured according to application requirements.

### REST API Architecture

A REST (Representational State Transfer) API is a web service architecture that enables communication between clients and servers using standard HTTP methods such as **GET**, **POST**, **PUT**, and **DELETE**. REST APIs are lightweight, scalable, and widely used in IoT systems.

### FastAPI Framework

FastAPI is a modern Python framework for building high-performance APIs. It provides automatic API documentation, data validation, and asynchronous request handling.

### TinyDB Database

TinyDB is a lightweight, document-oriented NoSQL database written in Python. It stores data in JSON format, making it suitable for small-scale IoT applications without requiring a separate database server.

### HTTP GET and POST Methods

- **GET:** Retrieves data from the server.
- **POST:** Sends data to the server for storage or processing.

---

## 🛠 Requirements

- AWS Academy Learner Lab (Sandbox)
- Ubuntu EC2 Instance
- Python 3.x
- SSH Client (Terminal or PuTTY)
- FastAPI
- Uvicorn
- TinyDB
- Postman or cURL (for API testing)

---

## 🚀 Procedure

### Step 1: Launch an AWS EC2 Instance

1. Log in to the AWS Console.
2. Launch an Ubuntu EC2 instance.
3. Configure the Security Group:
   - SSH (Port 22)
   - HTTP (Port 80)
   - Custom TCP (Port 8000) for FastAPI
4. Connect to the instance using SSH.

---

### Step 2: Update the System

```bash
sudo apt update
sudo apt upgrade -y
```

---

### Step 3: Install Python and Virtual Environment

```bash
sudo apt install python3-pip python3-venv -y
```

Create a virtual environment:

```bash
python3 -m venv venv
```

Activate it:

```bash
source venv/bin/activate
```

---

### Step 4: Install Required Packages

```bash
pip install fastapi uvicorn tinydb
```

---

### Step 5: Create the REST API

Create a file named `main.py`.

Example:

```python
from fastapi import FastAPI
from tinydb import TinyDB
from datetime import datetime

app = FastAPI()

db = TinyDB("data.json")

@app.get("/")
def home():
    return {"message": "IoT REST API is Running"}

@app.post("/sensor")
def store_data(temperature: float, humidity: float):
    record = {
        "temperature": temperature,
        "humidity": humidity,
        "timestamp": datetime.now().isoformat()
    }
    db.insert(record)
    return {"message": "Data Stored Successfully"}

@app.get("/sensor")
def get_data():
    return db.all()
```

---

### Step 6: Run the API

```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

---

### Step 7: Test the API

#### Home Endpoint

```http
GET /
```

Response:

```json
{
  "message": "IoT REST API is Running"
}
```

---

#### Store Sensor Data

```http
POST /sensor
```

Example:

```json
{
  "temperature": 28.6,
  "humidity": 65.3
}
```

Response:

```json
{
  "message": "Data Stored Successfully"
}
```

---

#### Retrieve Stored Data

```http
GET /sensor
```

Example Response:

```json
[
  {
    "temperature": 28.6,
    "humidity": 65.3,
    "timestamp": "2026-07-14T12:15:30"
  }
]
```

---

## 📂 Project Structure

```text
Lab-2/
│
├── README.md
├── main.py
├── data.json
├── requirements.txt
├── venv/
└── screenshots/
    ├── ec2-instance.png
    ├── fastapi-running.png
    ├── swagger-ui.png
    ├── post-request.png
    ├── get-request.png
    └── terminal-output.png
```

---

## 📸 Output

### EC2 Instance Running

> *(Insert Screenshot)*

---

### FastAPI Server Running

> *(Insert Screenshot)*

---

### Swagger API Documentation

Open in browser:

```
http://<EC2-Public-IP>:8000/docs
```

> *(Insert Screenshot)*

---

### POST Request

> *(Insert Screenshot)*

---

### GET Request

> *(Insert Screenshot)*

---

### Terminal Output

> *(Insert Screenshot)*

---

## ✅ Result

- Successfully launched and configured an AWS EC2 instance.
- Created and activated a Python virtual environment.
- Installed FastAPI, Uvicorn, and TinyDB.
- Developed REST API endpoints for storing and retrieving IoT sensor data.
- Stored temperature and humidity data with timestamps.
- Successfully tested GET and POST API endpoints using FastAPI/Swagger or Postman.

---

## 🎯 Conclusion

This lab demonstrated how to develop and deploy a cloud-based REST API using FastAPI on an AWS EC2 instance. The API successfully stored and retrieved IoT sensor data using TinyDB as the database. The experiment provided practical experience in cloud deployment, RESTful web services, API testing, and cloud-based data storage, which are fundamental concepts in modern IoT application development.

---

