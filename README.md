# PWVault - Secure Password Manager

PWVault is a secure password manager that leverages **Azure Key Vault** for cloud-based password storage, combined with client-side AES encryption to ensure maximum data protection. The application features a modern Angular frontend with Azure MSAL authentication and a robust Spring Boot backend.

---

## **Features**
- 🔐 Secure password storage using **Azure Key Vault**
- 🛡️ Client-side AES encryption for additional security
- 🌐 Modern web interface built with Angular 19
- 🔑 Azure MSAL authentication integration
- 📱 Responsive design with Bootstrap 5
- 🐳 Docker containerization for easy deployment
- 📚 Complete API documentation with Swagger

---

## **Technologies Used**
- **Frontend:** Angular 19.1, Bootstrap 5, Azure MSAL, TypeScript
- **Backend:** Spring Boot 3.4.1, Java 17, MapStruct, Lombok
- **Storage:** Azure Key Vault
- **Encryption:** AES-256 encryption
- **Authentication:** Azure Active Directory with JWT tokens
- **Containerization:** Docker & Docker Compose
- **Documentation:** SpringDoc OpenAPI (Swagger)

---

## **Quick Start (Docker)**

### **Prerequisites**
- Docker and Docker Compose installed
- Azure account with Key Vault and App Registration configured

### **Steps**

1. **Clone the Repository**
   ```bash
   git clone https://github.com/badmuriss/pwvault.git
   cd pwvault
   ```

2. **Create Environment File**
   Create a `.env` file in the root directory:
   ```env
   PWVAULT_FRONT_URI=http://localhost:4200
   KEYVAULT_URL=https://your-keyvault.vault.azure.net/
   CRYPTO_SECRET=your-32-character-encryption-key
   TENANT_ID=your-azure-tenant-id
   CLIENT_ID=your-azure-client-id
   CLIENT_SECRET=your-azure-client-secret
   ```

3. **Run the Application**
   ```bash
   docker-compose up --build
   ```

   Access the application:
   - **Frontend:** [http://localhost:4200](http://localhost:4200)
   - **Backend API:** [http://localhost:8080](http://localhost:8080)
   - **API Documentation:** [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)

---

## **Development Setup**

### **Backend (Spring Boot)**
```bash
cd pwvault-back
./mvnw clean compile     # Build
./mvnw spring-boot:run   # Run (port 8080)
./mvnw test             # Run tests
```

### **Frontend (Angular)**
```bash
cd pwvault-front
npm install             # Install dependencies
npm start              # Start dev server (port 4200)
npm test               # Run tests
npm run build          # Build for production
```

---

## **Project Structure**

```
pwvault/
├── pwvault-back/              # Spring Boot backend
│   ├── src/main/java/com/outis/pwvault/
│   │   ├── PwvaultApplication.java     # Application entry point
│   │   ├── client/                     # Azure Key Vault client
│   │   ├── config/                     # Security & CORS configuration
│   │   ├── controller/                 # REST controllers
│   │   ├── dto/                        # Data Transfer Objects
│   │   ├── service/                    # Business logic
│   │   └── util/                       # Crypto & utility classes
│   └── src/test/                       # Unit tests
├── pwvault-front/             # Angular frontend
│   ├── src/app/
│   │   ├── components/                 # Angular components
│   │   ├── services/                   # HTTP & auth services
│   │   ├── guards/                     # Route guards
│   │   └── dto/                        # TypeScript interfaces
│   └── src/environments/               # Environment configuration
├── docker-compose.yml         # Multi-container setup
├── CLAUDE.md                  # Development guidelines
└── README.md                  # This file
```

---

## **Architecture**

### **Security Architecture**
1. **Authentication:** Azure MSAL handles user authentication with Azure AD
2. **Authorization:** JWT tokens validated on each API request
3. **Encryption:** Secrets encrypted client-side with AES-256 before storage
4. **Storage:** Encrypted secrets stored in Azure Key Vault
5. **Transport:** HTTPS/TLS for all communications

### **Backend Components**
- **SecretService:** Core business logic for secret management
- **AzureClient:** Azure Key Vault integration
- **CryptoUtil:** AES encryption/decryption utilities
- **SecurityConfig:** JWT token validation and CORS setup

### **Frontend Components**
- **AuthService:** Azure MSAL authentication handling
- **SecretService:** API communication for secret operations
- **Components:** Modular UI components for different views

---

## **API Documentation**

The backend provides comprehensive API documentation via Swagger UI:
- **Local:** [http://localhost:8080/swagger-ui/index.html](http://localhost:8080/swagger-ui/index.html)
- **Endpoints:** CRUD operations for secrets, user management, folder organization

---

## **Testing**

### **Backend Tests**
- **Framework:** JUnit 5 with Spring Boot Test
- **Coverage:** Unit tests for services and controllers
- **Run:** `./mvnw test`

### **Frontend Tests**
- **Framework:** Jasmine & Karma
- **Coverage:** Component and service testing
- **Run:** `npm test`

---

## **Environment Variables**

| Variable | Description | Example |
|----------|-------------|---------|
| `PWVAULT_FRONT_URI` | Frontend URL for CORS | `http://localhost:4200` |
| `KEYVAULT_URL` | Azure Key Vault endpoint | `https://vault.vault.azure.net/` |
| `CRYPTO_SECRET` | AES encryption key (32 chars) | `your-secret-encryption-key-here` |
| `TENANT_ID` | Azure AD tenant ID | `12345678-1234-1234-1234-123456789012` |
| `CLIENT_ID` | Azure app registration client ID | `87654321-4321-4321-4321-210987654321` |
| `CLIENT_SECRET` | Azure app registration secret | `your-client-secret` |

---

## **License**
This project is licensed under the [MIT License](LICENSE).