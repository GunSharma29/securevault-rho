# 🔐 SecureVault – Hybrid Cryptography File Storage

A full-stack secure cloud file storage application that combines **Hybrid Cryptography**, **LSB Steganography**, and **JWT Authentication** to provide secure file encryption, storage, sharing, and recovery.

---

## 🌐 Live Demo

**Live Application:**  
https://YOUR-VERCEL-LINK.vercel.app

> Replace the above URL with your deployed Vercel application.

---

## 📖 Overview

SecureVault is a full-stack secure file storage system developed to protect sensitive digital files using multiple layers of security.

Unlike traditional cloud storage systems that rely on a single encryption algorithm, SecureVault follows a **Hybrid Cryptography** approach. Every uploaded file is divided into three independent blocks, and each block is encrypted using a different cryptographic algorithm. This significantly improves security by reducing the risk associated with a single point of failure.

To provide an additional layer of protection, the generated encryption key is hidden inside a user-selected image using **Least Significant Bit (LSB) Steganography**. During decryption, only the correct stego image can recover the hidden key, ensuring that encrypted files remain inaccessible even if the encrypted data is obtained by an unauthorized user.

The application also provides secure user authentication, encrypted file sharing, role-based access control, and an administrator dashboard for monitoring system activity.

---

## 🎯 Key Features

### Security

- Hybrid cryptography using multiple encryption algorithms
- AES-256-CBC encryption
- Triple-DES encryption
- Blowfish encryption
- PBKDF2-SHA512 key derivation
- HMAC-SHA256 integrity verification
- LSB Steganography for secure key hiding
- JWT-based authentication
- Password hashing and secure login
- Role-based access control

### File Management

- Upload files securely
- Automatic file splitting before encryption
- Encrypt and store files
- Download encrypted files
- Secure decryption using the correct stego image
- View and manage uploaded files

### File Sharing

- Share encrypted files with registered users
- Accept or reject shared files
- Download associated stego images
- Decrypt files after successful verification

### Administrator Features

- User management
- File statistics
- Encryption statistics
- Sharing analytics
- Dashboard with interactive charts

### User Features

- User registration
- Secure login
- Personal dashboard
- My Files
- Received Files
- Secure logout

---

## 🔐 Encryption Workflow

1. User uploads a file.
2. The file is divided into three separate blocks.
3. Each block is encrypted using a different algorithm:
   - Block 1 → AES-256-CBC
   - Block 2 → Triple-DES
   - Block 3 → Blowfish
4. A secure encryption key is generated.
5. The key is hidden inside a user-selected image using LSB Steganography.
6. Encrypted blocks and the stego image are stored securely.
7. During decryption, the correct stego image is required to recover the hidden key.
8. All decrypted blocks are merged to reconstruct the original file.

---

## 📌 Why SecureVault?
SecureVault demonstrates the integration of cryptography, steganography, secure authentication, database management, and full-stack web development in a single application. It was built to showcase secure file storage techniques while providing a practical and user-friendly interface for encrypted file management and sharing.
---

# 🛠️ Technology Stack

## Frontend
- HTML5
- CSS3
- JavaScript (ES6)
- Chart.js

## Backend
- Node.js
- Express.js

## Database
- MySQL 8

## Authentication & Security
- JWT Authentication
- PBKDF2-SHA512 Password Hashing
- HMAC-SHA256 Integrity Verification

## Cryptography
- AES-256-CBC
- Triple-DES
- Blowfish
- LSB Steganography

## Development Tools
- Git & GitHub
- VS Code
- MySQL Workbench
- Postman

## Deployment
- Vercel

---

# 🏗️ System Architecture

```
                    User
                      │
                      ▼
              Frontend Interface
          (HTML • CSS • JavaScript)
                      │
             REST API Requests
                      │
                      ▼
          Node.js + Express Backend
                      │
      ┌───────────────┼────────────────┐
      │               │                │
      ▼               ▼                ▼
 Authentication   Crypto Engine    File Sharing
      │               │                │
      └───────────────┼────────────────┘
                      │
                      ▼
              MySQL Database
                      │
                      ▼
            Encrypted File Storage
```

The frontend communicates with the backend through REST APIs. The backend authenticates users, processes file uploads, performs hybrid encryption and decryption, manages file sharing, and stores metadata in the MySQL database.

---

# 📂 Project Structure

```text
securevault/
│
├── backend/
│   ├── src/
│   │   ├── server.js               # Express application entry point
│   │   ├── routes/                 # REST API routes
│   │   │   ├── auth.js             # User authentication
│   │   │   ├── files.js            # File management
│   │   │   ├── hybrid.js           # Encryption & decryption
│   │   │   ├── sharing.js          # File sharing
│   │   │   ├── admin.js            # Admin dashboard
│   │   │   └── keys.js             # Key generation
│   │   │
│   │   ├── crypto/
│   │   │   └── cryptoEngine.js     # Cryptographic algorithms
│   │   │
│   │   ├── middleware/
│   │   │   ├── auth.js             # JWT middleware
│   │   │   └── validate.js         # Request validation
│   │   │
│   │   ├── services/
│   │   │   └── localDB.js          # Database service
│   │   │
│   │   └── utils/
│   │       └── logger.js           # Logging
│   │
│   ├── tests/
│   │   └── cryptoEngine.test.js
│   │
│   ├── seedUsers.js
│   ├── package.json
│   ├── .env.example
│   └── Dockerfile
│
├── frontend/
│   ├── auth.html
│   └── index.html
│
├── database/
│   └── setup.sql
│
├── uploads/
│   ├── blocks/
│   ├── stego/
│   └── files/
│
└── README.md
```

---

# ⚙️ Installation

## Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/securevault.git

cd securevault
```

---

## Backend Setup

```bash
cd backend

npm install
```

Copy the environment file.

```bash
copy .env.example .env
```

Update the environment variables inside `.env`.

```env
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=YOUR_PASSWORD
DB_NAME=securevault

JWT_SECRET=YOUR_SECRET_KEY
PORT=3000
```

---

## Database Setup

1. Open **MySQL Workbench**.
2. Connect to your local MySQL server.
3. Open `database/setup.sql`.
4. Execute the script to create the required database and tables.

---

## Start the Backend

```bash
npm run dev
```

Expected output:

```
SecureVault API running on port 3000
MySQL connected successfully
```

---

## Start the Frontend

Open the `frontend` folder using **Live Server** or any local web server.

```
frontend/
    ├── auth.html
    └── index.html
```

The application is now ready to use.
---

# 🚀 Getting Started

Once the backend server and frontend are running, you can start using SecureVault by following these steps.

## 1. Register or Login

- Create a new account using the registration page.
- Existing users can log in using their email and password.
- Upon successful authentication, a JWT token is generated to securely access protected APIs.

---

## 2. Upload & Encrypt a File

1. Navigate to the **Upload File** section.
2. Select a file (PDF, image, document, etc.).
3. Enter a secret encryption key.
4. Select a PNG/JPG image to be used for steganography.
5. Click **Encrypt & Upload**.

The application will:

- Split the uploaded file into three independent blocks.
- Encrypt each block using a different cryptographic algorithm.
- Generate a secure encryption key.
- Hide the key inside the selected image using LSB Steganography.
- Store the encrypted blocks securely.

---

## 3. Share an Encrypted File

1. Open **My Files**.
2. Select the uploaded file.
3. Click **Share**.
4. Enter the recipient's email address.
5. Send the sharing request.

The recipient will receive a secure sharing request in their dashboard.

---

## 4. Accept & Decrypt a Shared File

The recipient can:

- View received files.
- Accept or reject the sharing request.
- Download the associated stego image.
- Upload the correct stego image.
- Decrypt and recover the original file.

Only the correct stego image can reveal the hidden encryption key.

---

# 👤 Demo Accounts

After running the seed script, the following demo users are available.

| Name | Email | Password |
|------|-------|----------|
| Arjun Kumar | arjun@example.com | Arjun@secure123 |
| Priya Sharma | priya@example.com | Priya@secure123 |
| Rahul Verma | rahul@example.com | Rahul@secure123 |
| Sneha Patel | sneha@example.com | Sneha@secure123 |
| Vikram Singh | vikram@example.com | Vikram@secure123 |
| Anjali Nair | anjali@example.com | Anjali@secure123 |
| Karthik Raj | karthik@example.com | Karthik@secure123 |
| Divya Menon | divya@example.com | Divya@secure123 |
| Rohan Gupta | rohan@example.com | Rohan@secure123 |
| Meera Iyer | meera@example.com | Meera@secure123 |

---

## Administrator Account

Register through the application and then execute the following SQL query:

```sql
UPDATE users
SET role = 'admin'
WHERE email = 'admin@vault.com';
```

---

# 📡 API Endpoints

## Authentication

| Method | Endpoint | Description |
|---------|----------|-------------|
| POST | `/api/v1/auth/register` | Register a new user |
| POST | `/api/v1/auth/login` | Authenticate user |

---

## File Operations

| Method | Endpoint | Description |
|---------|----------|-------------|
| GET | `/api/v1/files` | Retrieve user files |
| POST | `/api/v1/hybrid/upload` | Encrypt & upload a file |
| POST | `/api/v1/hybrid/:id/decrypt` | Decrypt a selected file |
| GET | `/api/v1/hybrid/:id/stego` | Download the associated stego image |

---

## File Sharing

| Method | Endpoint | Description |
|---------|----------|-------------|
| POST | `/api/v1/sharing/send` | Share a file |
| GET | `/api/v1/sharing/received` | View received files |
| POST | `/api/v1/sharing/:id/accept` | Accept a sharing request |

---

## Administrator

| Method | Endpoint | Description |
|---------|----------|-------------|
| GET | `/api/v1/admin/dashboard` | Retrieve dashboard analytics |

---

## Health Check

| Method | Endpoint | Description |
|---------|----------|-------------|
| GET | `/health` | Verify server health |

---

# 🔒 Cryptography Stack

| Algorithm | Purpose |
|------------|---------|
| AES-256-CBC | Encrypt Block 1 |
| Triple-DES | Encrypt Block 2 |
| Blowfish | Encrypt Block 3 |
| PBKDF2-SHA512 | Secure key derivation |
| HMAC-SHA256 | Integrity verification |
| LSB Steganography | Hide encryption key inside an image |
| JWT | User authentication |

---

# 👨‍💻 Team Contributions

This project was collaboratively developed by a team of two members.

### Gun Sharma

- Designed the complete user interface and user experience.
- Developed the frontend using HTML, CSS, and JavaScript.
- Integrated frontend components with backend REST APIs.
- Implemented responsive layouts and user dashboards.
- Performed testing, debugging, and deployment on Vercel.

### Akshay Faujdar

- Developed the backend using Node.js and Express.
- Designed the MySQL database.
- Implemented hybrid cryptography modules.
- Built JWT authentication and authorization.
- Developed REST APIs, file management, and steganography logic.

---

# 🚀 Future Enhancements

Planned improvements include:

- AWS S3 integration
- Docker containerization
- Kubernetes deployment
- CI/CD pipeline
- Two-Factor Authentication (2FA)
- Email verification
- File versioning
- Activity logs
- Cloud backup and synchronization
- Mobile responsive improvements
- Real-time notifications

---

# 📜 License

This project was developed for educational and learning purposes. Feel free to fork, explore, and enhance the project while providing appropriate attribution to the contributors.

---

# ⭐ Acknowledgements

We would like to thank our mentors, faculty members, and the open-source community for their valuable resources, documentation, and guidance that contributed to the development of this project.

---

## If you found this project useful, consider giving it a ⭐ on GitHub!
