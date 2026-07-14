# Lab 3: Visualizing IoT Sensor Data Using Interactive Dashboards

## 📌 Objectives

- Retrieve stored sensor data from the REST API developed in **Lab 2**.
- Understand the importance of data visualization in IoT systems.
- Develop a web-based dashboard to display sensor data.
- Create real-time and historical visualizations of temperature and humidity data.
- Deploy the dashboard on an AWS EC2 instance.
- Analyze sensor trends using graphical representations.

---

## 📖 Background Theory

### Data Visualization in IoT

Data visualization transforms raw IoT sensor data into meaningful charts and graphs, allowing users to quickly identify trends, patterns, and anomalies. Effective visualization supports real-time monitoring and informed decision-making in IoT applications.

### API-Oriented Architecture

API-Oriented Architecture enables different software components to communicate through standardized APIs. In this lab, the dashboard retrieves sensor data from the REST API created in **Lab 2**, ensuring a modular and scalable system.

### Dashboard Systems

A dashboard is a web-based interface that displays data in an organized and interactive manner. Dashboards commonly include charts, tables, statistics, and filtering options to help users monitor IoT devices efficiently.

### Designing Data Filters

Data filters allow users to display specific subsets of data based on criteria such as time range, sensor type, or date. Filtering improves usability and enables focused analysis of IoT sensor readings.

---

## 🛠 Requirements

- AWS EC2 Instance
- Ubuntu Server
- Python 3.x
- FastAPI REST API (from Lab 2)
- HTML5
- CSS3
- JavaScript
- Chart.js (or another visualization library)
- Modern Web Browser

---

# 🚀 Procedure

## Step 1: Verify the REST API

Ensure the FastAPI server from **Lab 2** is running.

Example:

```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

Test the API:

```
http://<EC2-Public-IP>:8000/sensor
```

---

## Step 2: Create the Dashboard

Create the following files:

```
dashboard/
│
├── index.html
├── style.css
└── script.js
```

---

## Step 3: Design the User Interface

Develop a dashboard containing:

- Temperature chart
- Humidity chart
- Sensor data table
- Latest sensor values
- Last updated timestamp

---

## Step 4: Retrieve Sensor Data

Use JavaScript `fetch()` to retrieve data from the REST API.

Example:

```javascript
fetch("http://<EC2-Public-IP>:8000/sensor")
```

Parse the JSON response and display the data.

---

## Step 5: Visualize the Data

Create interactive charts using **Chart.js**.

Display:

- Temperature vs Time
- Humidity vs Time

Update the charts whenever new sensor data is received.

---

## Step 6: Deploy the Dashboard

Copy the dashboard files to the Nginx web directory.

Example:

```bash
sudo cp -r dashboard/* /var/www/html/
```

Restart Nginx if necessary.

```bash
sudo systemctl restart nginx
```

---

## Step 7: Access the Dashboard

Open a browser and visit:

```
http://<EC2-Public-IP>
```

Verify that:

- Charts are displayed.
- Sensor values are updated.
- Historical data is visible.

---

## 📂 Project Structure

```text
Lab-3/
│
├── README.md
├── dashboard/
│   ├── index.html
│   ├── style.css
│   └── script.js
├── screenshots/
│   ├── api-response.png
│   ├── dashboard-home.png
│   ├── temperature-chart.png
│   ├── humidity-chart.png
│   ├── sensor-table.png
│   └── deployed-dashboard.png
└── assets/
```

---

## 📊 Dashboard Features

- 📈 Real-time Temperature Graph
- 💧 Real-time Humidity Graph
- 📋 Historical Sensor Data Table
- 🔄 Automatic Data Refresh
- 📱 Responsive Design
- 📊 Interactive Charts
- ⏱ Latest Update Timestamp

---

## 📸 Output
![alt text](image.png)
![alt text](<image copy.png>)

## 📈 Sample Visualization

| Timestamp | Temperature (°C) | Humidity (%) |
|-----------|-----------------:|-------------:|
| 10:00 AM | 28.4 | 64 |
| 10:05 AM | 28.7 | 65 |
| 10:10 AM | 29.0 | 66 |
| 10:15 AM | 28.8 | 65 |

---

## ✅ Result

- Successfully retrieved sensor data from the REST API developed in Lab 2.
- Designed and implemented an interactive web dashboard.
- Displayed temperature and humidity data using graphical visualizations.
- Hosted the dashboard on an AWS EC2 instance.
- Enabled visualization of both real-time and historical IoT sensor data.

---

## 🎯 Conclusion

This lab demonstrated the development of an interactive IoT dashboard by integrating a REST API with modern web technologies. Sensor data was successfully retrieved from the cloud and visualized using interactive charts and tables. Deploying the dashboard on an AWS EC2 instance provided practical experience in cloud-hosted IoT monitoring systems, highlighting the importance of data visualization for analyzing sensor trends and supporting real-time decision-making.

---

## 📚 References

- AWS EC2 Documentation
- FastAPI Documentation
- Chart.js Documentation
- MDN Web Docs
- HTML, CSS, and JavaScript Documentation

---


