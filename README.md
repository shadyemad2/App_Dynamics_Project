# 🚀 Node.js Application Monitoring with AppDynamics

This project demonstrates how to monitor a **Node.js e-commerce application (ExpressCart)** integrated with **AppDynamics SaaS** to visualize performance metrics across all tiers — Application, Database, and Browser.

---

## 🧩 Project Overview

The goal of this setup is to:
- Deploy and run a Node.js application with a built-in MongoDB.
- Integrate the AppDynamics **Node.js Agent** for backend monitoring.
- Configure **Browser Real User Monitoring (RUM)** via AppDynamics **User Experience**.
- Build dashboards and alerts to track latency, error rates, and database availability.

---

## ⚙️ Environment Setup

1️⃣ **Prepare the Server**

Run the following commands:
```
dnf update -y
dnf install -y nodejs npm git
```
<img width="1179" height="138" alt="image" src="https://github.com/user-attachments/assets/925afbc1-cd3e-4abd-99f5-1b510a7e152d" />
<img width="1183" height="450" alt="image" src="https://github.com/user-attachments/assets/2003d6e1-eaf1-4e4a-8f55-928edd4312c2" />


2️⃣ **Clone and Configure the Application**

```
git clone https://github.com/someuser/expressCart.git
cd expressCart
npm install
```

Then edit your configuration file:
```
vi config/settings.json
```
Adjust the database connection, port, and any required environment variables.

---
<img width="1190" height="543" alt="image" src="https://github.com/user-attachments/assets/7d9dc3f0-3525-42a0-9973-cbcf21699e91" />
<img width="1196" height="554" alt="image" src="https://github.com/user-attachments/assets/f44172c4-58f9-4a8e-80ee-9c092a458b5a" />
<img width="1181" height="561" alt="image" src="https://github.com/user-attachments/assets/75aa5302-2f01-4f23-a59a-9c29283d6ad0" />
<img width="1185" height="594" alt="image" src="https://github.com/user-attachments/assets/6fee77f5-197a-43f8-be9f-a4cdab4f6fd7" />


## 🧠 Step 1: Install and Configure AppDynamics Node.js Agent

1. Download the **AppDynamics Node.js Agent** from your SaaS Controller.
2. Extract it inside your project directory (e.g., `/opt/appdynamics/`).
3. Export required environment variables:
```
export APPDYNAMICS_AGENT_ACCOUNT_NAME="your-account"
export APPDYNAMICS_AGENT_ACCOUNT_ACCESS_KEY="your-access-key"
export APPDYNAMICS_CONTROLLER_HOST_NAME="your-controller.saas.appdynamics.com"
export APPDYNAMICS_CONTROLLER_PORT=443
export APPDYNAMICS_CONTROLLER_SSL_ENABLED=true
export APPDYNAMICS_AGENT_APPLICATION_NAME="ExpressCart-App"
export APPDYNAMICS_AGENT_TIER_NAME="Backend"
export APPDYNAMICS_AGENT_NODE_NAME="Node1"
```
4. Start your Node.js app with the agent:
```
node -r /opt/appdynamics/nodejs/node_modules/appdynamics app.js
```

---

<img width="1181" height="488" alt="image" src="https://github.com/user-attachments/assets/9655a291-f96e-4783-b9a9-cc3a357d5e7c" />
<img width="1178" height="415" alt="image" src="https://github.com/user-attachments/assets/19b186fd-2072-4f53-9c7f-15688961b608" />
<img width="1175" height="482" alt="image" src="https://github.com/user-attachments/assets/76a2ea06-32b4-41ab-8641-9a39598de9f1" />
<img width="1166" height="828" alt="image" src="https://github.com/user-attachments/assets/b46d6e8d-6789-4694-92aa-4ed3c2165c31" />
<img width="1168" height="500" alt="image" src="https://github.com/user-attachments/assets/c971ed0b-608f-46b0-826f-1a848ca983d7" />
<img width="1179" height="509" alt="image" src="https://github.com/user-attachments/assets/b0a1d0c9-3eb8-4e47-859a-40b7befd4b62" />
<img width="1184" height="502" alt="image" src="https://github.com/user-attachments/assets/ae4c998a-5c09-40d5-82a4-1bb9dbde15d8" />
<img width="1188" height="535" alt="image" src="https://github.com/user-attachments/assets/2172c6ff-b09c-40aa-948b-6a223647964f" />
<img width="1187" height="443" alt="image" src="https://github.com/user-attachments/assets/0923f85a-7b97-4d24-ad4d-ef428357a8e5" />
<img width="1186" height="399" alt="image" src="https://github.com/user-attachments/assets/3d626e91-c107-441a-9970-fd82b874a752" />
<img width="1183" height="529" alt="image" src="https://github.com/user-attachments/assets/be160e9b-1edd-4264-81a7-5dfd89b413bc" />
<img width="1191" height="520" alt="image" src="https://github.com/user-attachments/assets/34ee11e9-a088-46bd-ae68-f7e1a4b55a4f" />
<img width="1188" height="517" alt="image" src="https://github.com/user-attachments/assets/bddd8fc1-c65b-4ca6-9fca-b1de1104d7f8" />

## 🌐 Step 2: Enable Browser Real User Monitoring (RUM)

1. From AppDynamics SaaS, go to:
```
User Experience > Browser Apps > Add Application
```
2. Copy the **JavaScript snippet** generated.
3. Paste it inside your main `views/layout.html` file before `</head>`:
```
<!-- AppDynamics Browser RUM Script -->
<script>/* your browser agent snippet */</script>
```
4. Visit your web app to generate real user data in AppDynamics.

---
<img width="1166" height="570" alt="image" src="https://github.com/user-attachments/assets/49c3a28c-2340-4857-b1d4-888abe5d68f5" />
<img width="1158" height="525" alt="image" src="https://github.com/user-attachments/assets/5373472b-bd6f-4461-8a97-849271918ded" />
<img width="1183" height="530" alt="image" src="https://github.com/user-attachments/assets/c7e3d8ee-0de9-4d87-b66e-eb03f008fed8" />
<img width="1178" height="532" alt="image" src="https://github.com/user-attachments/assets/7e9538cb-1966-4f79-919e-2e4f279a7b3f" />
<img width="1194" height="451" alt="image" src="https://github.com/user-attachments/assets/4f5dadb2-0fa7-4e35-ac65-ca2f51ebd823" />
<img width="1059" height="256" alt="image" src="https://github.com/user-attachments/assets/41309b5e-1611-4fc0-9982-63ebb3912317" />
<img width="1193" height="663" alt="image" src="https://github.com/user-attachments/assets/511ddd0f-d50a-4ee6-a466-b39f08930fee" />
<img width="1191" height="359" alt="image" src="https://github.com/user-attachments/assets/adb3ecbf-0ed9-48a5-a7da-47b2345f2f08" />
<img width="1191" height="514" alt="image" src="https://github.com/user-attachments/assets/c0e0071d-09a4-4c86-aad1-ad303f2d7f9d" />
<img width="1196" height="514" alt="image" src="https://github.com/user-attachments/assets/02708380-ab01-4525-999a-e6d5c1fe22d7" />
<img width="1193" height="519" alt="image" src="https://github.com/user-attachments/assets/c1b3a095-63a1-4c2a-98b6-750f470b038c" />
<img width="1186" height="513" alt="image" src="https://github.com/user-attachments/assets/5736e48e-b68a-4d21-ac7f-15cd1eecd7b8" />
<img width="1194" height="520" alt="image" src="https://github.com/user-attachments/assets/00df5057-464c-488c-ae6c-ee0c3fd1da6e" />
<img width="1185" height="521" alt="image" src="https://github.com/user-attachments/assets/3e753b50-b6a5-45e6-9d29-dbf223eee943" />
<img width="1160" height="426" alt="image" src="https://github.com/user-attachments/assets/d0a1d01b-826c-4e96-9fa7-b66fb42c5b1a" />

## 📊 Step 3: Dashboards and Alerts

**Create Dashboards**
Build dashboards for each tier:
- **Backend (Node.js)** → CPU, memory, response time, and error rate.
- **Database (MongoDB)** → Connection count, query time.
- **Browser (User Experience)** → Page load time, first byte, DOM ready.
<img width="598" height="371" alt="image" src="https://github.com/user-attachments/assets/970a5c4c-bf48-4f93-b5e5-15f8d98e6be1" />
<img width="1179" height="517" alt="image" src="https://github.com/user-attachments/assets/4a5a2388-e42d-4b69-90ea-88835475eee0" />
<img width="1190" height="503" alt="image" src="https://github.com/user-attachments/assets/37cb1955-7c81-49be-91d3-426109918fe1" />

**Configure Alerts**
Set alerts on:
- High latency (Response Time > 3s)
- High error rate (>5%)
- Database unavailability

---
<img width="1190" height="503" alt="image" src="https://github.com/user-attachments/assets/ac5803dc-038d-48ce-9fa8-d5ad68381d5d" />
<img width="1096" height="406" alt="image" src="https://github.com/user-attachments/assets/b37e6439-9bb3-4bc2-9858-bd4f90ac165d" />
<img width="698" height="417" alt="image" src="https://github.com/user-attachments/assets/12979a07-be27-474a-8e7f-7c84dd8ab2c5" />

## 🧩 Step 4: Validate Data Flow

Check that all metrics appear in:
- **Application Flow Map**
- **Metric Browser**
- **Dashboards**

You should see live data between the **Node.js app**, **MongoDB**, and **Browser Agent**.

---

## 🧠 Troubleshooting Tips

- If the app doesn’t appear in AppDynamics:
  - Ensure your agent environment variables are correct.
  - Check network connectivity to the Controller.
  - Review agent logs under `/opt/appdynamics/logs/`.

- If browser data doesn’t show:
  - Make sure the RUM snippet is inserted correctly.
  - Reload the web page a few times to generate traffic.

---



## 🏁 Summary

✅ Node.js + MongoDB application deployed  
✅ AppDynamics Node.js Agent integrated  
✅ Browser RUM configured  
✅ Dashboards and alerts created  

This project provides a **complete full-stack monitoring example** that connects AppDynamics with real application metrics across backend, frontend, and database layers.

---

### 👨‍💻 Author
**Shady Emad Wahib Farahat**  
Junior System Administrator | DevOps & Cloud Enthusiast

