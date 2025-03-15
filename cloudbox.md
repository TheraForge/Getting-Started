# **🌩️ TheraForge CloudBox - API Documentation**

---

## **📌 Overview**  
**TheraForge CloudBox** is an advanced **Backend-as-a-Service (BaaS)** platform designed for:  
✅ **Offline-First Applications** – Enables data access even when offline  
✅ **TLS 1.3 Secure Connections** – Ensures encrypted communication  
✅ **Class-Based End-to-End Encryption** – High-security encrypted data storage  
✅ **Seamless Data Synchronization** – Only syncs changes to minimize bandwidth usage  
✅ **Cloud-Based Backend Services** – Ideal for **IoT, mobile, and web applications**  

---

## **🛠 Key Features**  
💡 **Strict TLS 1.3 Support** – Encrypted data in transit  
💡 **Authentication** – Secure API key & JWT-based authentication  
💡 **Data Syncing** – Efficient **offline-first** storage with CouchDB  
💡 **Class-Based End-to-End Encryption** – Protects **different data types separately**  
💡 **Real-Time Notifications** – Secure **event-driven** architecture  
💡 **Secure File Uploads** – AWS S3 storage with encryption  

---

## **🔒 Security Architecture & TLS 1.3 Support**  
CloudBox **only supports TLS 1.3** for **all API communication** to ensure **maximum security**.  
- **Mitigates downgrade attacks**  
- **Perfect Forward Secrecy (PFS)** for all connections  
- **Elliptic Curve Cryptography (ECC)** for strong security  
- **No support for TLS 1.2 or earlier**  

**Example of enforcing TLS 1.3 in API requests:**  
🔹 **JavaScript (Node.js with Axios)**  
```js
const https = require("https");
const axios = require("axios");

const agent = new https.Agent({
    secureProtocol: "TLSv1_3"
});

axios.post("https://stg.theraforge.org/api/v1/auth/login", {
    email: "user@example.com",
    password: "securepassword123"
}, {
    httpsAgent: agent,
    headers: { "Content-Type": "application/json" }
}).then(response => console.log(response.data))
.catch(error => console.error(error));
```

🔹 **Python (Requests with TLS 1.3 Enforcement)**  
```python
import requests

session = requests.Session()
session.mount("https://", requests.adapters.HTTPAdapter())

response = session.post(
    "https://stg.theraforge.org/api/v1/auth/login",
    json={"email": "user@example.com", "password": "securepassword123"},
    headers={"Content-Type": "application/json"},
)

print(response.json())
```

🔹 **Kotlin (Android, OkHttp TLS 1.3)**  
```kotlin
val client = OkHttpClient.Builder()
    .sslSocketFactory(SSLContext.getInstance("TLSv1.3").socketFactory)
    .build()

val request = Request.Builder()
    .url("https://stg.theraforge.org/api/v1/auth/login")
    .post("{\"email\": \"user@example.com\", \"password\": \"securepassword123\"}"
        .toRequestBody("application/json".toMediaType()))
    .build()

client.newCall(request).execute().use { response -> println(response.body?.string()) }
```

🔹 **Swift (iOS, TLS 1.3 enforced)**  
```swift
let url = URL(string: "https://stg.theraforge.org/api/v1/auth/login")!
var request = URLRequest(url: url)
request.httpMethod = "POST"
request.setValue("application/json", forHTTPHeaderField: "Content-Type")

let json = ["email": "user@example.com", "password": "securepassword123"]
request.httpBody = try? JSONSerialization.data(withJSONObject: json)

URLSession.shared.dataTask(with: request) { data, response, error in
    if let data = data {
        print(String(data: data, encoding: .utf8)!)
    }
}.resume()
```

---

## **📂 Data Syncing & Offline-First Architecture**  

CloudBox **minimizes data exchanges** by keeping data **locally stored** and **synchronizing only changes**.

### **🔧 How Offline-First Sync Works**
1️⃣ **Device works offline** – Stores data **locally** in encrypted format  
2️⃣ **Syncs only changes** – When back online, only **modified records** sync  
3️⃣ **Conflict Resolution** – Uses a **revision-based** system  

---

### **🖼️ CloudBox Architecture Diagram**
![CloudBox Architecture](https://user-images.githubusercontent.com/123456789/CloudBox_architecture.png)

---

## **📌 API Endpoints**  
### **🛡 Authentication**  
| Endpoint | Method | Description |
|----------|--------|-------------|
| `/auth/signup` | `POST` | Register a new user |
| `/auth/login` | `POST` | Authenticate user and get token |
| `/auth/logout` | `POST` | Logout and invalidate token |

### **📂 File Management**  
| Endpoint | Method | Description |
|----------|--------|-------------|
| `/auth/file-upload` | `PUT` | Upload a file to AWS S3 |
| `/auth/retrieve-file` | `GET` | Download file |

---

## **📌 Error Handling**
| **Error Code** | **Message** |
|--------------|------------|
| `400` | Bad Request - Invalid input |
| `401` | Unauthorized - Invalid token |
| `403` | Forbidden - No permission |
| `404` | Not Found - Resource unavailable |

---

