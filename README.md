# CommBank-Server

![CommBank Logo](https://img.shields.io/badge/Backend-.NET%20Core-blue) ![MongoDB](https://img.shields.io/badge/Database-MongoDB-green)  

---

## 📖 Project Overview

**CommBank-Server** is a **backend service** built with **ASP.NET Core Web API** and **MongoDB**. It manages user banking goals, including savings targets, balances, and target dates.  

**Main Features:**

- Create, read, update, and delete user goals (CRUD)  
- Retrieve goals by user ID  
- Connects and interacts with MongoDB database  
- Provides JSON API for frontend integration  

---

## 🛠 Tech Stack

- **Backend Framework:** ASP.NET Core 7.0  
- **Database:** MongoDB  
- **Language:** C#  
- **Dependencies:**
  - `MongoDB.Driver` for database operations  
  - `Microsoft.AspNetCore.Mvc` for REST API  

---

## 📝 Changelog / Main Modifications

**Version:** 1.1 (Updated by Fiona Jiang)

### 🔹 Key Modifications:

1. **Goal Model Updates**
   - Changed `TargetAmount`, `Balance`, and `TargetDate` fields to nullable types (`ulong?`, `double?`, `DateTime?`) to handle missing values.
   - Added default values in `POST` requests if any fields are missing (`Name`, `TargetAmount`, `Balance`, `TargetDate`).
   - Uncommented previously commented properties to ensure full MongoDB deserialization.

2. **GoalController Enhancements**
   - Updated `POST /api/goal` to automatically set default values when fields are not provided.
   - Improved `PUT /api/goal/{id}` to only overwrite existing values if new values are provided.
   - Added API endpoints for testing MongoDB connection (`GET /api/goal/TestMongo`) and fetching all goal IDs (`GET /api/goal/AllIds`).
   - Fixed deserialization issues causing 404 and missing fields in API responses.

3. **MongoDB Integration Fixes**
   - Ensured MongoDB driver can correctly deserialize documents with the updated Goal model.
   - Fixed `GetAsync` and `GetForUserAsync` methods to correctly retrieve all fields from the database.

4. **General Improvements**
   - Added nullable handling and default assignments to prevent API from returning `null` for essential fields.
   - Cleaned up controller code to be more robust and maintainable.

---
