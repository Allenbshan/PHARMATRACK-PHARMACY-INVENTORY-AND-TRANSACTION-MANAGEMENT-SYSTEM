
[README.md](https://github.com/user-attachments/files/25888819/README.md)
# PharmaTrack: Pharmacy Inventory and Transaction Management System

Developed by:
- Shan Allen Dayon (Project Manager / System Builde / System Analyst / System Designer)

Philippine Women's College of Davao | February 2026

---

## Prerequisites

Before running PharmaTrack, make sure you have the following installed:

| Tool | Version | Download |
|------|---------|----------|
| Java JDK | 8 or higher | https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html |
| MySQL Server | 8.0+ | https://dev.mysql.com/downloads/installer/ |
| Apache Maven | 3.6+ | https://maven.apache.org/download.cgi |
| NetBeans IDE | 12+ (optional) | https://netbeans.apache.org/ |

---

## Database Setup

1. Open MySQL (via MySQL Workbench or command line).
2. Run the schema script located at:
   ```
   src/main/resources/schema.sql
   ```
   This will:
   - Create the `pharmatrack_db` database
   - Create all required tables
   - Insert default admin and user accounts

3. **Default Accounts:**
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

Update these lines to match your MySQL setup:
```java
private static final String USER = "root";        // Your MySQL username
private static final String PASSWORD = "";         // Your MySQL password
```

If MySQL is on a different port or host, also update:
```java
private static final String URL = "jdbc:mysql://localhost:3306/pharmatrack_db?...";
```

---

## Running in NetBeans

1. Open NetBeans IDE
2. Go to **File → Open Project**
3. Navigate to the `pharmatrack` folder and open it
4. NetBeans will detect it as a Maven project
5. Right-click the project → **Run** (or press F6)

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
        └── schema.sql              ← Run this in MySQL first!
```

---

## Technology Stack
- **Language:** Java 8+
- **UI Framework:** Java Swing
- **Database:** MySQL 8.0
- **Build Tool:** Apache Maven
- **IDE:** NetBeans (recommended)
- **Architecture:** MVC (Model-View-Controller) with DAO pattern

