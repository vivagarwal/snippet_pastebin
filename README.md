# 📝 **Pastebin Project** (Spring Boot Backend + React Frontend)

This project is a simple **Pastebin-like application** that allows users to create snippets with optional expiration dates and access limits. It is designed with a **Spring Boot backend** and a **React frontend (Vite + Tailwind CSS)**. The backend manages snippet creation and retrieval, while the frontend provides an intuitive UI for interacting with the backend.

## 🔗 **Live Demo**
- [Frontend Live Demo](https://pastebin-frontend-inky.vercel.app)

---

## 📂 **Project Structure**
- **Backend Repo:** [Pastebin Backend](https://github.com/vivagarwal/pastebin_backend)
- **Frontend Repo:** [Pastebin Frontend](https://github.com/vivagarwal/image_processing_frontend)

---

## 🔧 **Backend Setup**

### Environment Variables
To run the backend, set up the following environment variables in a `.env` file or using Railway's environment settings:

```
MONGODB_URL=<Your MongoDB Atlas URL>
FRONTEND_URL=<Frontend URL>
Example:
```
FRONTEND_URLL=http://localhost:5173
```
```

### Core Backend Functionalities
- **Create Snippet:** POST request to `/api/snippets/create` with content, optional expiration date, and access limit.
- **View Snippet:** GET request to `/api/snippets/view/{uniqueLink}` to retrieve and display snippet content.

### Data Handling in Backend:
- **UUID Generation:** Unique links for snippets are generated using UUID.
- **Expiration & Access Limits:** Snippets with expired dates or exceeding access limits are deleted automatically.

---

## 🔧 **Frontend Setup**

### Environment Variables
To run the frontend, add the following in the `.env` file:
```
VITE_BASE_URL=<Backend Base URL>
```
Example:
```
VITE_BASE_URL=http://localhost:8080
```

### UI Features
- Form for creating snippets (content, expiration date, and access limit).
- Generates a unique link to view the snippet.
- Automatically copies the link after snippet creation.

---

## 🛠️ **How to Run Locally**

### Backend
1. Clone the backend repo:
   ```bash
   git clone https://github.com/vivagarwal/pastebin_backend.git
   cd pastebin_backend
   ```
2. Add the `.env` file with the required environment variables.
3. Run the application:
   ```bash
   ./mvnw spring-boot:run
   ```
   The backend will start at `http://localhost:8080`.

### Frontend
1. Clone the frontend repo:
   ```bash
   git clone https://github.com/vivagarwal/image_processing_frontend.git
   cd image_processing_frontend
   ```
2. Add the `.env.local` file:
   ```plaintext
   VITE_BASE_URL=http://localhost:8080
   ```
3. Install dependencies and start the server:
   ```bash
   npm install
   npm run dev
   ```
   The frontend will run at `http://localhost:5173`.

---

## 🚀 **API Endpoints**

### 1. **Create Snippet**
- **Endpoint:** `POST /api/snippets/create`
- **Request Body:**
  ```json
  {
    "content": "System.out.println('Hello World!');",
    "expirationTime": "2025-12-31T23:59:59",
    "accessLimit": 10
  }
  ```
- **Response:**
  ```json
  {
    "id": "679dda0eb8048a5f73afca21",
    "content": "System.out.println('Hello World!');",
    "createdAt": "2025-02-01T13:53:42.612851",
    "expirationTime": "2025-12-31T23:59:59",
    "accessLimit": 10,
    "currentViews": 0,
    "uniqueLink": "23a17a6e-9f27-43cb-8e32-8a90affea950"
  }
  ```

### 2. **View Snippet**
- **Endpoint:** `GET /api/snippets/view/{uniqueLink}`
- **Response:**
  ```json
  {
    "content": "System.out.println('Hello World!');"
  }
  ```


## 📦 **Deployment Details**

### Backend Deployment (Railway)
1. **Build & Start Commands:**
   ```
   ./mvnw clean package -DskipTests
   java -jar target/*.jar
   ```

2. Ensure the correct **MONGODB_URL** and **FRONTEND_URL** are set in the environment settings.

### Frontend Deployment (Vercel)
- Deploy the React frontend using Vercel with the correct **VITE_BASE_URL** in `.env.local`.

---

## 🔑 **Security Considerations**
- CORS is enabled on the backend using Spring's configuration to allow requests from the frontend.
- Ensure sensitive data (e.g., MongoDB credentials) is properly secured.

---

## 🤝 **Contributing**
Contributions are welcome! Please fork the repository and submit a pull request.

---

## 📜 **License**
This project is licensed under the MIT License.

---

Let me know if this format works or if you’d like any adjustments!