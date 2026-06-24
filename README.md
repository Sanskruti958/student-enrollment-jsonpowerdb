# 🎓 Student Enrollment Form — JsonPowerDB Micro Project

[![JsonPowerDB](https://img.shields.io/badge/Database-JsonPowerDB-orange?style=flat-square)](https://login2explore.com/jpdb/)
[![HTML5](https://img.shields.io/badge/Frontend-HTML5%20%2F%20CSS3%20%2F%20JS-E34F26?style=flat-square)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![License: MIT](https://img.shields.io/badge/License-MIT-rose?style=flat-square)](https://opensource.org/licenses/MIT)

---

## 📌 Title of the Project

**Student Enrollment Form** — A client-side web form that stores and manages student records in a **STUDENT-TABLE** relation inside the **SCHOOL-DB** database powered by [JsonPowerDB](https://login2explore.com/jpdb/).

---

## 📖 Description

This micro-project is a dynamic HTML form built as part of the **JsonPowerDB V2.0 Assessment**. It allows school administrators to:

- **Register** new student records with a unique Roll No. as the primary key
- **Retrieve and update** existing student records by looking up the Roll No.
- **Reset** the form at any point to start fresh

The form follows a strict UX flow:

| Step | Behaviour |
|------|-----------|
| Page load | Empty form shown; only Roll No. field is active |
| Enter Roll No. → not in DB | Save + Reset enabled; cursor moves to next field |
| Enter Roll No. → found in DB | Record pre-filled; Update + Reset enabled; PK locked |
| Save / Update | Data written to JsonPowerDB; form resets automatically |
| Reset | Clears the form and returns to the initial state |

**Input Fields**

| Field | Type | Notes |
|-------|------|-------|
| Roll-No | Text | **Primary Key** — unique per student |
| Full-Name | Text | Student's full name |
| Class | Select | 1st through 12th |
| Birth-Date | Date | ISO date picker |
| Address | Text | Full postal address |
| Enrollment-Date | Date | Date of enrollment |

**Tech Stack**

- Pure HTML5 / CSS3 / Vanilla JavaScript (no frameworks)
- JsonPowerDB REST API (`/api/irl` for reads, `/api/iml` for writes)
- Warm cream–peach–rose color palette for accessible, pleasant UI

---

## ⚡ Benefits of Using JsonPowerDB

JsonPowerDB (JPDB) is a **real-time, multi-model, high-performance NoSQL database** that makes it extraordinarily simple to build CRUD applications without setting up any backend server.

| Benefit | Details |
|---------|---------|
| 🚀 **Schema-free** | No table schema to define upfront — just send JSON |
| 🔑 **Token-based API** | Secure REST endpoints secured by API token — no SQL injection risk |
| 🌐 **Server-less from the client** | Direct browser → JPDB calls; zero backend code needed |
| ⚡ **In-memory speed** | Powered by PowerIndeX engine for lightning-fast indexing |
| 📦 **Multi-model** | Supports document, key-value, relational, time-series, and geo-spatial data |
| 🛠️ **Easy CRUD** | Simple JSON command objects (`find`, `insert`, `update`, `delete`) |
| 💸 **Free tier** | Login2Explore offers a free developer sandbox — ideal for micro-projects |
| 🔄 **Real-time** | Supports server-sent events for live updates |
| 📊 **Built-in dashboard** | Visual DB explorer at `api.login2explore.com` — no extra tooling needed |
| 🔒 **Data integrity** | Supports primary key enforcement and record-level locking |

---

## 🗂️ Table of Contents

- [Title of the Project](#-title-of-the-project)
- [Description](#-description)
- [Benefits of Using JsonPowerDB](#-benefits-of-using-jsonpowerdb)
- [Scope of Functionalities](#-scope-of-functionalities)
- [Examples of Use](#-examples-of-use)
- [Project Status](#-project-status)
- [Release History](#-release-history)
- [How to Run](#-how-to-run)
- [Sources & References](#-sources--references)

---

## 🔭 Scope of Functionalities

- ✅ **Insert** — Save a brand-new student record to SCHOOL-DB
- ✅ **Retrieve** — Auto-fetch existing record by Roll No.
- ✅ **Update** — Modify and save changes to an existing record
- ✅ **Validation** — All fields checked for empty values before save/update
- ✅ **UX State Machine** — Buttons and fields enable/disable based on DB lookup result
- ✅ **Live Record Count** — Footer shows how many students are in the database
- ✅ **Status Messages** — Color-coded status bar (info / success / warning / error)
- ✅ **Keyboard Support** — Enter key triggers Roll No. lookup
- ✅ **Responsive Design** — Works on mobile and desktop

---

## 💡 Examples of Use

### Registering a new student

1. Open `index.html` in any modern browser.
2. Enter a Roll No. that doesn't exist yet (e.g. `2024001`) and click **Check**.
3. The status bar shows *"Roll No. 2024001 is new"* — Save and Reset buttons activate.
4. Fill in Full Name, Class, Birth Date, Address, and Enrollment Date.
5. Click **Save** — the record is stored in JsonPowerDB and the form resets.

### Updating an existing student

1. Enter a Roll No. that already exists (e.g. `2024001`) and click **Check**.
2. The form is pre-filled with the stored data — Update and Reset buttons activate.
3. Change any field (e.g. update the Address).
4. Click **Update** — the record is updated in JsonPowerDB and the form resets.

### API command used for lookup

```json
{
  "token": "<your-token>",
  "dbName": "SCHOOL-DB",
  "cmd": {
    "find": { "Roll-No": "2024001" },
    "limit": 1
  }
}
```
Sent as POST to `https://api.login2explore.com:5577/api/irl`

### API command used for insert

```json
{
  "token": "<your-token>",
  "dbName": "SCHOOL-DB",
  "cmd": {
    "insert": {
      "rel": "STUDENT-TABLE",
      "jsonStr": "[{\"Roll-No\":\"2024001\",\"Full-Name\":\"Priya Sharma\", ...}]"
    }
  }
}
```
Sent as POST to `https://api.login2explore.com:5577/api/iml`

---

## 🚦 Project Status

**✅ Complete** — All core functionalities are implemented and tested.

| Feature | Status |
|---------|--------|
| Form UI | ✅ Done |
| Roll No. Lookup | ✅ Done |
| Save (Insert) | ✅ Done |
| Update | ✅ Done |
| Reset | ✅ Done |
| Validation | ✅ Done |
| Record Count | ✅ Done |
| Responsive layout | ✅ Done |

---

## 📦 Release History

| Version | Date | Description |
|---------|------|-------------|
| `v1.0.0` | June 2026 | Initial release — Student Enrollment Form with full CRUD via JsonPowerDB REST API. Single-file HTML deliverable with Save, Update, Reset flow, field validation, status bar, and record count footer. |

---

## 🚀 How to Run

1. **Clone or download** this repository.
2. Open `index.html` directly in a browser — no server needed.
3. **Replace** the `JPDB_TOKEN` constant in the `<script>` section with your own token from [Login2Explore](https://login2explore.com/jpdb/docs.html).
   ```js
   const JPDB_TOKEN = "your-connection-token-here";
   ```
4. The **SCHOOL-DB** database and **STUDENT-TABLE** relation will be created automatically by JsonPowerDB the first time you insert a record.

> 💡 Get your free token at [https://login2explore.com](https://login2explore.com) → Sign Up → My Profile → Connection Token.

---

## 📚 Sources & References

- [JsonPowerDB Official Documentation](https://login2explore.com/jpdb/docs.html)
- [JsonPowerDB GitHub (BeAgarwal)](https://github.com/BeAgarwal/JsonPowerDB#readme)
- [Mastering Markdown — GitHub Guides](https://guides.github.com/features/mastering-markdown/)
- [README Template — dbader](https://github.com/dbader/readme-template)
- [electron-markdownify README Example](https://github.com/amitmerchant1990/electron-markdownify#readme)

---

## 👩‍💻 Author

**Sanskruti Anil Pawar**
B.Tech Computer Science Engineering · KDK College of Engineering (2024–2028)

---

*Built as part of the JsonPowerDB V2.0 Micro Project Assessment.*
