## 🧩 System Overview

A centralized system that records employee attendance through different check-in methods:

* Normal login (username/password or punch button)
* Wi-Fi–based clock-in (detects user near an approved router)
* Face-match check-in (via camera & biometric match)

---

## ⚙️ Functional Requirements
1. User Management
   - Register, update, or deactivate employees. 
   - Assign unique employee IDs and roles (admin, employee, HR).

2. Authentication & Authorization
   - Secure login (username/password). 
   - Role-based access control for HR/admins.

3. Check-In / Check-Out Methods
   - Normal Check-in: User logs in via web/app. 
   - Wi-Fi Check-in: System detects device connected to approved routers and auto-checks in. 
   - Face-match Check-in: Capture image → run facial recognition → record attendance if matched.

4. Attendance Recording
   - Save timestamp, user ID, check-in type, device ID, and location. 
   - Prevent duplicate check-ins within a time threshold.

5. Attendance Reporting
   - Daily/weekly/monthly reports per user or department. 
   - Export to CSV/PDF.

6. Notifications
   - Notify user of successful check-in/out. 
   - Alert admin if check-in attempts fail or unauthorized access is detected.

7. Admin Dashboard
   - View, filter, and edit attendance records. 
   - Manage Wi-Fi routers and camera devices.

## 🧠 Non-Functional Requirements

| Category            | Description                                                                          |
| ------------------- | ------------------------------------------------------------------------------------ |
| **Scalability**     | System should support thousands of concurrent check-ins.                             |
| **Availability**    | 99.9% uptime using load-balanced servers and redundant DB.                           |
| **Security**        | Encrypted data (SSL/TLS), secure password storage (bcrypt), face data anonymization. |
| **Performance**     | Each check-in operation < 2 seconds (including face recognition).                    |
| **Reliability**     | Data integrity maintained even during network failures.                              |
| **Maintainability** | Modular architecture (Microservices / SOA for check-in methods).                     |
| **Auditability**    | All actions logged for compliance and audits.                                        |
| **Usability**       | Simple web and mobile UI for employees.                                              |
| **Compliance**      | GDPR-compliant for biometric data handling.                                          |

## 🏗️ High-Level Architecture
1. **Frontend**: (Web/Mobile App)
   - User interface for employees to check in/out.
   - Admin dashboard for HR and admins.

2. **Backend**: RESTful API
3. **Database**: Relational DB (e.g., PostgreSQL/MySQL)
   - Tables: Users, AttendanceRecords, WiFiRouters, Devices, Logs.

4. **Authentication Service**: OAuth2/JWT for secure login.

5. **Check-In Services**:
   - Normal Check-in Service
   - Wi-Fi Check-in Service (integrates with router APIs)
   - Face-Match Service (integrates with facial recognition API)
    
6. Redis for caching
7. API Gateway for routing requests
8. Message Queue (e.g., RabbitMQ) for async tasks (e.g., sending notifications, generating reports)
9. Notification Service (Email/SMS)
10. Logging & Monitoring (ELK Stack, Prometheus/Grafana)
11. Optional: LDAP or company SSO for user sync.
