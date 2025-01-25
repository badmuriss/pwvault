# PWVault - Secure Password Manager

PWVault is a password manager designed to provide **maximum security**. It uses **Azure Key Vault** as a database to store passwords, combined with advanced encryption to protect the data.

This project was developed to facilitate password management, ensuring your information is secure against unauthorized access.

---

## **Features**
- Secure password storage using **Azure Key Vault**.
- Cutting-edge encryption to ensure data confidentiality.
- Web interface for password management.

---

## **Technologies Used**
- **Frontend:** Angular
- **Backend:** Spring Boot
- **Storage:** Azure Key Vault
- **Encryption:** AES Algorithm
- **Docker:** For building and deploying the application

---

## **How to Run the Project**

### **Prerequisites**
- **Git** installed
- **Docker** and **Docker Compose** installed
- An Azure account with **Azure Key Vault** and App Registration configured

### **Steps**

1. **Clone the Repository with Submodules**
   To clone the repository and initialize the submodules (frontend and backend):
   ```bash
   git clone --recurse-submodules https://github.com/badmuriss/pwvault.git
   cd pwvault
   ```

   If you already cloned the repository but didn't initialize the submodules, run:
   ```bash
   git submodule init
   git submodule update
   ```

2. **Create the `.env` File**
   In the root directory of the project, create a file named `.env` and add the following environment variables:

   ```env
   # Optional URL for the frontend (e.g., custom domain)
   PWVAULT_FRONT_URI=http://localhost:4200

   # Azure Key Vault URL
   KEYVAULT_URL=<your-keyvault-url>

   # Secret key for encryption
   CRYPTO_SECRET=<your-secret-key>

   # Azure authentication credentials
   TENANT_ID=<your-tenant-id>
   CLIENT_ID=<your-client-id>
   CLIENT_SECRET=<your-client-secret>
   ```

   > **Note:** Replace the values `<...>` with the actual data from your configuration.

3. **Run Docker Compose**
   With Docker configured, run the following command in the root of the project:
   ```bash
   docker-compose up --build
   ```

   This will:
   - Build and run the **frontend** (Angular) at: [http://localhost:4200](http://localhost:4200).
   - Build and run the **backend** (Spring Boot) at: [http://localhost:8080](http://localhost:8080).

---

## **Project Structure**

- **pwvault-front:** Frontend source code (Angular SPA), included as a Git submodule.
- **pwvault-back:** Backend source code (Spring Boot), included as a Git submodule.
- **docker-compose.yml:** Configuration to run the project with Docker.
- **.env:** Configuration file for environment variables.

---

## **Backend Documentation**
The backend API provides documentation with SpringDoc at the endpoint: `/swagger-ui/index.html`:

---

## **License**
This project is licensed under the [MIT](LICENSE) license.