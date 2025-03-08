# 🌩️ TheraForge CloudBox API Documentation

The **TheraForge CloudBox API** is a Backend-as-a-Service (**BaaS**) designed for managing **IoT-friendly data synchronization, user authentication, and encrypted data storage**.

This API ensures **efficient, secure, and offline-first-capable** data exchanges, making it ideal for **IoT applications and cloud-based systems**.

CloudBox is part of the **TheraForge meta-platform**.

---

## 🚀 **Getting Started**
- **Developers** → Test API endpoints using tools like [Postman](https://www.postman.com/) or [Swagger UI](https://stg.theraforge.org/api/docs).  
- **Businesses** → Contact **TheraForge support** for integration and enterprise solutions.

🌐 **Geeting Started with TheraForge**: (https://github.com/TheraForge/Getting-Started)

---

## 📌 What Does This API Do?
With **TheraForge CloudBox**, you can:

✅ **Authenticate users** securely with token-based authentication  
✅ **Synchronize data** between devices and the cloud while minimizing bandwidth costs  
✅ **Store and retrieve encrypted data** for high-security applications  
✅ **Enable offline-first functionality** with data sync protocols  
✅ **Manage user accounts** and access controls efficiently  

---

## 🔥 **Why Choose TheraForge CloudBox?**
✨ **Efficient** – Reduces data transfers, saving costs  
🔐 **Secure** – Implements **end-to-end encryption** for sensitive data  
📡 **Offline-First** – Works even with **intermittent connectivity**  
🛠️ **Developer-Friendly** – Simple integration with **detailed API documentation**  


---

## 🔗 **Live API Playground**
🛠️ **Test the API interactively** with [Swagger UI](https://stg.theraforge.org/api/docs)  
💡 **Try out API requests** without writing any code.

---

## 📖 API Documentation Structure
1. **Introduction** – Overview of the API’s purpose  
2. **Authentication** – How to securely access the API  
3. **Endpoints & Features** – List of available API functionalities  
4. **Request & Response Examples** – Sample API interactions  
5. **Error Handling** – Common errors and how to resolve them  
6. **Versioning & Updates** – Information about API improvements  

---

## 🔗 API Endpoints & Descriptions

### 🔹 **User Authentication & Management**
| **Endpoint**                  | **Description** |
|--------------------------------|----------------|
| `POST /auth/login`             | User login, returns an authentication token. |
| `POST /auth/register`          | Registers a new user account. |
| `POST /auth/logout`            | Logs out the user and invalidates the token. |
| `GET /users`                   | Retrieves a list of all registered users. |
| `GET /users/{userId}`          | Fetches details of a specific user. |
| `DELETE /users/{userId}`       | Removes a user from the system. |

### 🔹 **Data Syncing**
| **Endpoint**                  | **Description** |
|--------------------------------|----------------|
| `POST /sync`                   | Synchronizes data between the client and the cloud. |
| `GET /sync/status`             | Retrieves the latest sync status and timestamps. |

### 🔹 **Secure Data Storage & Encryption**
| **Endpoint**                  | **Description** |
|--------------------------------|----------------|
| `POST /encryption/test`        | Tests encryption by encrypting sample data. |
| `POST /data/store`             | Stores user data in an encrypted format. |
| `GET /data/{dataId}`           | Retrieves encrypted data from storage. |

---

## 🔑 **Authentication Guide**

Most endpoints require **authentication** using a Bearer token.  
Include the token in your HTTP request headers:


Authorization: Bearer <your_token_here>


---

## 🛠️ **API Request Examples**

### **🖥️ cURL Example: User Login**
```sh
curl -X POST https://stg.theraforge.org/api/v1/auth/login \
-H "Content-Type: application/json" \
-d '{"email": "john.doe@example.com", "password": "securepassword123"}'
```

### **🐍 Python Example: Fetch Users**
```python
import requests

url = "https://stg.theraforge.org/api/v1/users"
headers = {"Authorization": "Bearer your_token_here"}

response = requests.get(url, headers=headers)

if response.status_code == 200:
    print("Users:", response.json())
else:
    print("Error:", response.json())
```

---

## 🚨 **Error Handling**

If something goes wrong, the API will return a structured error message.  
For example, if an authentication token is missing:

#### **Response:**
```json
{
  "error": "Unauthorized",
  "message": "You must provide a valid authentication token."
}
```

| **Error Code** | **Meaning** |
|--------------|------------|
| `400` | Bad Request - Invalid input data |
| `401` | Unauthorized - Authentication required |
| `403` | Forbidden - Access denied |
| `404` | Not Found - Resource unavailable |
| `500` | Internal Server Error |


---

🚀 **Start building with TheraForge CloudBox today!** 🚀
```

---

