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

## 📊 Step 3: Dashboards and Alerts

**Create Dashboards**
Build dashboards for each tier:
- **Backend (Node.js)** → CPU, memory, response time, and error rate.
- **Database (MongoDB)** → Connection count, query time.
- **Browser (User Experience)** → Page load time, first byte, DOM ready.

**Configure Alerts**
Set alerts on:
- High latency (Response Time > 3s)
- High error rate (>5%)
- Database unavailability

---

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

## 📸 Screenshots (add later)
- Application Flow Map  
- Node.js Tier Metrics  
- MongoDB Tier Metrics  
- Browser RUM Dashboard  
- Custom Dashboard View  
- Alert Configuration  

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

