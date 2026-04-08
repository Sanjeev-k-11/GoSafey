# 🛡️ GoSafey | Advanced Ride & Parcel Aggregator Platform

![MERN Stack](https://img.shields.io/badge/Stack-MERN-blue?style=for-the-badge&logo=react)
![Socket.io](https://img.shields.io/badge/RealTime-Socket.io-black?style=for-the-badge&logo=socket.io)
![Razorpay](https://img.shields.io/badge/Payments-Razorpay-blue?style=for-the-badge&logo=razorpay)
![Firebase](https://img.shields.io/badge/Notifications-Firebase-orange?style=for-the-badge&logo=firebase)

**GoSafey** is a premium, full-stack ride-hailing and parcel delivery ecosystem. Built with the **MERN stack**, it features a tripartite architecture (User App, Captain Terminal, Admin Console) connected seamlessly via real-time WebSockets, robust geospatial querying, and a highly secure digital wallet system.

---

## 🚀 Project Overview

GoSafey connects users with independent drivers ("Captains") for instant transit and doorstep parcel delivery. The platform operates on a centralized Node.js/Express API that handles real-time driver matching, secure payment gateways, push notifications, and strict safety protocols. 

### 🌟 Core Modules

#### 1. 📱 User Application
* **Multi-Tier Booking:** Instant booking for Moto, Auto, Cab, and parcel delivery.
* **Smart Preferences:** Users can request AC, Silent Rides, or demand a Helmet prior to booking.
* **GoSafey Wallet:** In-app secure wallet integrated with Razorpay for instant top-ups and automatic ride deductions.
* **Safety Center:** One-tap SOS panic button and emergency contact sharing.

#### 2. 🚖 Captain Terminal (Driver App)
* **Live Radar Engine:** Scans active zones and receives instant dispatch alerts.
* **Hardware Link Protocols:** Utilizes OS-level Haptic feedback and Audio Context for ride request alerts.
* **Digital Verification:** Automated workflow for uploading and verifying Aadhar, RC Book, and Driving License.
* **Earnings Hub:** Detailed logging of platform fees, penalties, wallet deductions, and bank payouts.

#### 3. 🛡️ Admin Console
* **Global Monitoring:** Oversee all active rides, available Captains, and system health.
* **Compliance Center:** Dashboard to manually approve/reject Captain KYC documents.
* **Resolution Center:** Manage user trip complaints, refund requests, and platform disputes.

---

## 🧠 Under the Hood (Technical Flow)

GoSafey is engineered to handle real-time data synchronization across thousands of devices efficiently.

* **Real-Time Dispatch (Socket.io):** HTTP polling is too slow for ride-hailing. We use persistent bidirectional WebSocket tunnels. When a user requests a ride, the server instantly emits the request to the specific "rooms" of nearby active Captains.
* **Geospatial Matching (MongoDB GeoJSON):** Driver coordinates are stored as GeoJSON Points. The system uses MongoDB's highly optimized `$nearSphere` and `$maxDistance` indexing to calculate radiuses and match drivers in milliseconds.
* **Secure Financials (Razorpay Webhooks):** To maintain PCI-DSS compliance, no card data touches our database. Payments are processed via Razorpay. The GoSafey backend listens for secure Razorpay Webhooks (`payment.captured`) to safely update user wallet balances.
* **Background Alerts (Firebase FCM):** When WebSockets disconnect (app in background), Node.js triggers Firebase Cloud Messaging (FCM) to push OS-level notifications (e.g., "Your Captain has arrived!") directly to the user's status bar.

---

## 💻 Tech Stack

| Technology | Role |
| :--- | :--- |
| **React.js + Vite** | Frontend Framework (User, Captain, Admin interfaces) |
| **Tailwind CSS** | Premium UI styling (Glassmorphism, Neumorphism) |
| **Node.js & Express** | Centralized Backend API and Server |
| **MongoDB & Mongoose**| NoSQL Database (optimized with 2dsphere indexes) |
| **Socket.io** | Low-latency WebSockets for live maps and radar |
| **Firebase** | Push notifications and OTP authentication |
| **Razorpay API** | Secure payment gateway for Wallet transactions |
| **JWT** | Role-based encrypted authentication (User/Driver/Admin) |

---

## ⚙️ Getting Started

Follow these steps to run the GoSafey ecosystem locally.

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/gosafey.git
cd gosafey
