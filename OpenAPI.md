# 🌩️ TheraForge CloudBox API Documentation

The **TheraForge CloudBox API** is a Backend-as-a-Service (**BaaS**) designed for managing **IoT-friendly data synchronization, user authentication, and encrypted data storage**.

This API ensures **efficient, secure, and offline-first-capable** data exchanges, making it ideal for **IoT applications and cloud-based systems**.

CloudBox is part of the **TheraForge meta-platform**.

---

## 🚀 **Getting Started**
- **Developers** → Test API endpoints using tools like [Postman](https://www.postman.com/) or [Swagger UI](https://stg.theraforge.org/api/docs).  
- **Businesses** → Contact **TheraForge support** for integration and enterprise solutions.

🌐 **Getting Started with TheraForge**: [GitHub Repository](https://github.com/TheraForge/Getting-Started)

### Quick Setup Guide:
1. **Register for an API key** using `/v1/auth/api-key` endpoint or through our web portal
2. **Create an account** using the signup endpoint
3. **Log in** to obtain an authentication token
4. **Use the token** to access authenticated endpoints

---

## 📌 What Does This API Do?
With **TheraForge CloudBox**, you can:

✅ **Authenticate users** securely with token-based authentication  
✅ **Synchronize data** between devices and the cloud while minimizing bandwidth costs  
✅ **Store and retrieve encrypted data** for high-security applications  
✅ **Enable offline-first functionality** with data sync protocols  
✅ **Manage user accounts** and access controls efficiently  
✅ **Handle doctor-patient relationships** and careplan management  
✅ **Manage tasks** within careplans for healthcare applications  
✅ **Implement file management** with secure attachments  
✅ **Subscribe to real-time notifications** using Server-Sent Events (SSE)  

---

## 🔥 **Why Choose TheraForge CloudBox?**
✨ **Efficient** – Reduces data transfers, saving costs  
🔐 **Secure** – Implements **end-to-end encryption** for sensitive data  
📡 **Offline-First** – Works even with **intermittent connectivity**  
🛠️ **Developer-Friendly** – Simple integration with **detailed API documentation**  
🏥 **Healthcare Ready** – Built-in support for doctor-patient relationships and careplan management  

---

## 🔗 **Live API Playground**
🛠️ **Test the API interactively** with [Swagger UI](https://stg.theraforge.org/api/docs)  
💡 **Try out API requests** without writing any code.

---

## 📖 API Documentation Structure
1. **Introduction** – Overview of the API's purpose  
2. **Authentication** – How to securely access the API  
3. **Endpoints & Features** – List of available API functionalities  
4. **Request & Response Examples** – Sample API interactions  
5. **Error Handling** – Common errors and how to resolve them  
6. **Versioning & Updates** – Information about API improvements  

---

## 🔑 **Authentication Guide**

Most endpoints require **authentication** using a Bearer token.  
Include the token in your HTTP request headers:

```
Authorization: Bearer <your_token_here>
```

### Obtaining An Authentication Token:

1. **Register** using the `/v1/auth/signup` endpoint
2. **Login** using the `/v1/auth/login` endpoint
3. **Copy** the access token from the response (excluding the "Bearer" keyword)
4. **Use** this token in the Authorization header for subsequent requests

### Token Management:
- Token expires after a set period
- Use `/v1/auth/refresh-token` to obtain a new token without re-authentication
- Logout with `/v1/auth/logout` to invalidate the current token

### Social Authentication:
- The API supports social login via `/v1/auth/social-login`

### Security Notes:
- Use HTTPS for all API requests
- Emails are treated as case-insensitive
- Passwords can be reset using the forgot/reset password endpoints
- reCAPTCHA verification is available to prevent abuse

---

## 🔗 API Endpoints & Descriptions

### 🔹 **API Key Management**
| **Endpoint** | **Method** | **Description** |
|---|---|---|
| `/v1/auth/api-key` | POST | Register a new API key |
| `/v1/auth/api-key-logs` | GET | Retrieve all API key transaction logs |
| `/v1/auth/api-keys` | GET | Get all registered API keys |
| `/v1/auth/api-key/{clientId}` | PUT | Update an existing API key |

### 🔹 **User Authentication & Management**
| **Endpoint** | **Method** | **Description** |
|---|---|---|
| `/v1/auth/signup` | POST | Register a new user account |
| `/v1/auth/login` | POST | User login, returns an authentication token |
| `/v1/auth/admin-signup` | POST | Register an administrator account |
| `/v1/auth/admin-login` | POST | Administrator login |
| `/v1/auth/logout` | POST | Logs out the user and invalidates the token |
| `/v1/auth/send-verification-email` | POST | Send email verification to user |
| `/v1/auth/change-password` | PUT | Change user's password |
| `/v1/auth/forgot-password` | POST | Initiate password reset process |
| `/v1/auth/reset-password` | PUT | Reset password with token |
| `/v1/auth/refresh-token` | POST | Refresh the authentication token |
| `/v1/auth/social-login` | POST | Login with social media accounts |
| `/v1/auth/verify-recaptcha` | POST | Verify reCAPTCHA response |

### 🔹 **User Profile Management**
| **Endpoint** | **Method** | **Description** |
|---|---|---|
| `/v1/auth/user-profile/{userId}` | GET | Retrieve user profile data |
| `/v1/auth/user-profile/{userId}` | PUT | Update user profile |
| `/v1/auth/user-profile/{userId}` | DELETE | Delete user profile |
| `/v1/auth/user-profile/json-file/{userId}` | GET | Download user profile as JSON |
| `/v1/auth/user-public-key/{userId}` | POST | Save user's public key |
| `/v1/auth/user-public-key/{userId}` | GET | Retrieve user's public key |
| `/v1/auth/user-public-key/{userId}` | PUT | Update user's public key |
| `/v1/auth/user-public-key/{userId}` | DELETE | Delete user's public key |

### 🔹 **Doctor-Patient Relationship Management**
| **Endpoint** | **Method** | **Description** |
|---|---|---|
| `/v1/auth/patients` | GET | List all patients |
| `/v1/auth/doctor-patients/{doctorId}` | GET | Get doctor's associated patients |
| `/v1/auth/doctor-new-patients/{doctorId}` | GET | Get doctor's newly associated patients |
| `/v1/auth/patient-data/{patientId}` | GET | Get detailed patient information |
| `/v1/auth/request-patient-access` | POST | Request access to patient data |
| `/v1/auth/grant-patient-access/{accessId}` | PUT | Grant care plan access |
| `/v1/auth/grant-patient-access/{accessId}/{viaEmail}` | PUT | Grant access via email notification |
| `/v1/auth/careplan-requests/{patientId}` | GET | Get care plan access requests |
| `/v1/auth/patient-disassociate/{patientId}` | DELETE | Remove doctor-patient association |

### 🔹 **Task Management**
| **Endpoint** | **Method** | **Description** |
|---|---|---|
| `/v1/auth/doctor-task` | POST | Create a new task |
| `/v1/auth/doctor-task/{taskId}` | PUT | Update an existing task |
| `/v1/auth/doctor-task/{taskId}` | DELETE | Delete a task |
| `/v1/auth/doctor-task/{doctorId}` | GET | Get tasks created by a doctor |
| `/v1/auth/patient-task/{patientId}` | GET | Get tasks assigned to a patient |
| `/v1/auth/task/update-status/{taskId}` | PUT | Update task completion status |

### 🔹 **Data Synchronization (DB Proxy)**
| **Endpoint** | **Method** | **Description** |
|---|---|---|
| `/v1/db/_bulk_docs` | POST | Create multiple documents in remote database |
| `/v1/db/_bulk_get` | POST | Get multiple documents from remote database |
| `/v1/db/_revs_diff` | POST | Get revision differences from remote database |
| `/v1/db/_changes` | GET | Retrieve database changes |
| `/v1/db/_all_docs` | GET/POST | Get all documents (with optional filtering) |
| `/v1/db/{docId}` | GET | Get a single document |
| `/v1/db/{docId}` | PUT | Update a single document |
| `/v1/db/_local/{docId}` | GET | Get a local document |
| `/v1/db/_local/{docId}` | PUT | Update a local document |
| `/v1/db/_design/{docId}` | GET | Get a design document |

### 🔹 **File Management**
| **Endpoint** | **Method** | **Description** |
|---|---|---|
| `/v1/auth/file-upload` | PUT | Upload a file attachment |
| `/v1/auth/retrieve-file` | GET | Download a file attachment |
| `/v1/auth/delete-file` | DELETE | Delete a file attachment |
| `/v1/auth/file-info` | GET | Get file metadata |
| `/v1/auth/file-revision` | GET | Get file revision history |
| `/v1/auth/file-rename` | GET | Rename a file |
| `/v1/auth/attachments` | GET | Retrieve multiple attachments |

### 🔹 **Notifications**
| **Endpoint** | **Method** | **Description** |
|---|---|---|
| `/v1/db/_subscribe` | GET | Subscribe to Server-Sent Events notifications |
| `/v1/db/_unsubscribe/{userId}/{client}` | GET | Unsubscribe from SSE notifications |
| `/v1/db/notification-data` | GET | Get user notifications |
| `/v1/db/notification-status` | GET | Mark notifications as read |

---

## 🛠️ **API Request Examples**

### **🖥️ cURL Example: User Registration**
```sh
curl -X POST https://stg.theraforge.org/api/v1/auth/signup \
-H "Content-Type: application/json" \
-d '{
  "email": "user@example.com",
  "password": "securePassword123",
  "firstName": "John",
  "lastName": "Doe",
  "userType": "patient"
}'
```

### **🖥️ cURL Example: User Login**
```sh
curl -X POST https://stg.theraforge.org/api/v1/auth/login \
-H "Content-Type: application/json" \
-d '{"email": "john.doe@example.com", "password": "securepassword123"}'
```

### **🐍 Python Example: Fetch Users**
```python
import requests

url = "https://stg.theraforge.org/api/v1/auth/patients"
headers = {"Authorization": "Bearer your_token_here"}

response = requests.get(url, headers=headers)

if response.status_code == 200:
    print("Patients:", response.json())
else:
    print("Error:", response.json())
```

### **🐍 Python Example: Data Synchronization**
```python
import requests

url = "https://stg.theraforge.org/api/v1/db/_bulk_docs"
headers = {
    "Authorization": "Bearer your_token_here",
    "Content-Type": "application/json"
}
data = {
    "docs": [
        {"_id": "doc1", "title": "Document 1", "content": "Content for document 1"},
        {"_id": "doc2", "title": "Document 2", "content": "Content for document 2"}
    ]
}

response = requests.post(url, headers=headers, json=data)

if response.status_code == 201:
    print("Documents created:", response.json())
else:
    print("Error:", response.json())
```

### **🖥️ JavaScript Example: Upload File**
```javascript
async function uploadFile(file, docId) {
    const token = 'your_token_here';
    const formData = new FormData();
    formData.append('file', file);
    
    const response = await fetch(`https://stg.theraforge.org/api/v1/auth/file-upload?docId=${docId}`, {
        method: 'PUT',
        headers: {
            'Authorization': `Bearer ${token}`
        },
        body: formData
    });
    
    if (response.ok) {
        const data = await response.json();
        console.log('File uploaded:', data);
        return data;
    } else {
        const error = await response.json();
        console.error('Upload failed:', error);
        throw new Error(error.message);
    }
}
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
| `200` | Success |
| `404` | Not Found - Resource unavailable |
| `500` | Internal Server Error |
| `601` | Not Verified - Resource not verified |

### Common Error Scenarios:

1. **Authentication Errors**:
   - Invalid credentials
   - Expired token
   - Missing authorization header

2. **Data Validation Errors**:
   - Missing required fields
   - Invalid field format (email, password, etc.)
   - Data type mismatch

3. **Resource Errors**:
   - Document not found
   - Document already exists
   - Revision conflict

4. **Permission Errors**:
   - Insufficient permissions
   - Unauthorized access attempt

---

## 📡 **SSE & Real-time Notifications**

TheraForge CloudBox supports real-time notifications via Server-Sent Events (SSE):

1. Connect to the SSE endpoint: `/v1/db/_subscribe`
2. Listen for events from the server
3. Process notifications in real-time
4. Disconnect using `/v1/db/_unsubscribe/{userId}/{client}` when done

---

## 🏁 **API Versioning**

- Current API version: v1
- All endpoints are prefixed with `/v1/`
- When new versions are released, they will be appropriately versioned

---

## 💻 **Implementation Examples**

### **Doctor-Patient Workflow Example**:
1. Doctor registers with `/v1/auth/signup` specifying `userType: "doctor"`
2. Patient registers with `/v1/auth/signup` specifying `userType: "patient"`
3. Doctor requests access to patient data using `/v1/auth/request-patient-access`
4. Patient grants access via `/v1/auth/grant-patient-access/{accessId}`
5. Doctor creates tasks for patient using `/v1/auth/doctor-task`
6. Patient views assigned tasks via `/v1/auth/patient-task/{patientId}`
7. Patient updates task status using `/v1/auth/task/update-status/{taskId}`

### **Offline-First Implementation**:
1. Cache data locally when online
2. Allow users to work offline
3. When reconnected, use `/v1/db/_revs_diff` to identify differences
4. Synchronize changes with `/v1/db/_bulk_docs`
5. Retrieve updates with `/v1/db/_changes`

---

🚀 **Start building with TheraForge CloudBox today!** 🚀

---
