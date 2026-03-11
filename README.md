[README.md](https://github.com/user-attachments/files/25889363/README.md)
# PharmaTrack: Pharmacy Inventory and Transaction Management System

Developed by:
- Shan Allen Dayon (Project Manager / System Builder / System Analyst / System Designer)

Philippine Women's College of Davao | February 2026

---

## Prerequisites

Before running PharmaTrack, make sure you have the following installed:

| Tool | Version | Download |
|------|---------|----------|
| Java JDK | 8 or higher | https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html |
| XAMPP | Latest | https://www.apachefriends.org |
| Apache Maven | 3.6+ | https://maven.apache.org/download.cgi |
| NetBeans IDE | 12+ (optional) | https://netbeans.apache.org/ |

---

## Database Setup (XAMPP)

1. **Start XAMPP:**
   - Open the **XAMPP Control Panel**
   - Click **Start** next to **Apache**
   - Click **Start** next to **MySQL**

2. **Open phpMyAdmin:**
   - Click the **Admin** button next to MySQL in the XAMPP Control Panel, **or**
   - Open your browser and go to: `http://localhost/phpmyadmin`

3. **Run the schema script:**
   - In phpMyAdmin, click the **SQL** tab at the top
   - Open the schema file from your project: `src/main/resources/schema.sql`
   - Copy and paste the entire contents into the SQL tab
   - Click **Go** to execute

   This will:
   - Create the `pharmatrack_db` database
   - Create all required tables
   - Insert default admin and user accounts

4. **Default Accounts:**
   | Role | Username | Password |
   |------|----------|----------|
   | Admin | admin | admin123 |
   | User | user | user123 |

---

## Configure Database Connection

Open the file:
```
src/main/java/com/pharmatrack/db/DatabaseConnection.java
```

Update these lines to match your XAMPP MySQL setup:
```java
private static final String URL = "jdbc:mysql://localhost:3306/pharmatrack_db?useSSL=false&serverTimezone=UTC";
private static final String USER = "root";   // XAMPP default MySQL username
private static final String PASSWORD = "";    // XAMPP default MySQL password is empty — leave blank
```

> ⚠️ **Note:** XAMPP's MySQL default username is `root` with **no password**. Do not add a password unless you manually set one in phpMyAdmin.

---

## Running in NetBeans

1. Open NetBeans IDE
2. Go to **File → Open Project**
3. Navigate to the `pharmatrack` folder and open it
4. NetBeans will detect it as a Maven project
5. Right-click the project → **Run** (or press F6)

> ✅ Make sure XAMPP's Apache and MySQL are both **running** before launching the app.

---

## Running from Command Line (Maven)

```bash
# Step 1: Navigate to project folder
cd pharmatrack

# Step 2: Compile and package
mvn clean package

# Step 3: Run the application
java -jar target/pharmatrack-1.0-SNAPSHOT.jar
```

> ✅ Make sure XAMPP's Apache and MySQL are both **running** before executing these commands.

---

## Troubleshooting

| Problem | Solution |
|--------|----------|
| `Communications link failure` | Make sure MySQL is started in XAMPP Control Panel |
| `Access denied for user 'root'` | Leave the password field blank in `DatabaseConnection.java` |
| `Unknown database 'pharmatrack_db'` | Re-run the `schema.sql` script in phpMyAdmin |
| Port conflict on 3306 | In XAMPP, go to **Config → my.ini** and change the port, then update the URL in `DatabaseConnection.java` |

---

## System Features

### For All Users (Admin + User)
- **Product Management** — Add, view, update, and delete medicines
- **Stock Management** — Track and manage stock levels
- **Transaction Management** — Create and view sales transactions

### Admin-Only Features
- **Update Transactions** — Modify existing transaction records
- **Daily Report** — Generate Sales Report and Stock Report by date
- **User Management** — Add, update, and delete system users

---

## Project Structure

```
pharmatrack/
├── pom.xml                         ← Maven build config
├── README.md
└── src/main/
    ├── java/com/pharmatrack/
    │   ├── Main.java               ← App entry point
    │   ├── db/
    │   │   └── DatabaseConnection.java
    │   ├── model/
    │   │   ├── User.java
    │   │   ├── Product.java
    │   │   ├── Stock.java
    │   │   └── Transaction.java
    │   ├── dao/
    │   │   ├── UserDAO.java
    │   │   ├── ProductDAO.java
    │   │   ├── StockDAO.java
    │   │   └── TransactionDAO.java
    │   └── gui/
    │       ├── UITheme.java
    │       ├── SplashScreen.java
    │       ├── LoginScreen.java
    │       ├── RegisterScreen.java
    │       ├── UserDashboard.java
    │       ├── AdminDashboard.java
    │       └── panels/
    │           ├── ProductPanel.java
    │           ├── StockPanel.java
    │           ├── TransactionPanel.java
    │           ├── DailyReportPanel.java
    │           └── UserManagementPanel.java
    └── resources/
        └── schema.sql              ← Run this in phpMyAdmin first!
```

---

## Technology Stack
- **Language:** Java 8+
- **UI Framework:** Java Swing
- **Database:** MySQL 8.0 (via XAMPP)
- **Build Tool:** Apache Maven
- **IDE:** NetBeans (recommended)
- **Architecture:** MVC (Model-View-Controller) with DAO pattern
