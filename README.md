# 🎧 Spotify Account Cloner (Backend)

Developed end-to-end by **Sultan Rasul**, this backend powers the **Spotify Account Cloner**, a project that allows users to securely authenticate with their Spotify account and transfer playlists, liked songs, and other personal data between profiles.  

It handles **Spotify OAuth 2.0 authorisation**, **token exchange**, and **refresh logic**—enabling the frontend to clone user data seamlessly.

🔗 **Frontend Repository:** [Spotify Account Cloner (Frontend)](https://github.com/sultanrasul/Spotify-Account-Cloner-Frontend)

---

## 🧠 Overview

This backend is responsible for:

- Managing Spotify’s **OAuth 2.0 authorisation flow**  
- Exchanging authorisation codes for **access and refresh tokens**  
- Refreshing expired tokens for ongoing Spotify API use  
- Providing secure endpoints used by the frontend to complete login and cloning operations  
- Running locally or on a hosted domain to support web-based authentication

The **frontend**, built with modern JavaScript and the Spotify Web API, depends on this backend to obtain valid authentication tokens before cloning user data.

---

## 🔐 Authentication Flow

1. User initiates login via the frontend.  
2. Backend redirects them to Spotify’s authorisation page (`/backend/login1` or `/backend/login2`).  
3. After the user grants access, Spotify redirects back with an authorisation code.  
4. Backend exchanges the code for an **access token** and **refresh token** at `/backend/callback`.  
5. Frontend then uses the token to interact with Spotify APIs for playlist and library operations.  

Two login routes are provided:
- **/backend/login1** → read-only access (fetch user data)  
- **/backend/login2** → write access (clone or modify playlists, liked songs, etc.)

---

## ⚙️ Setup Instructions

```bash
# 1. Clone the repository
git clone https://github.com/sultanrasul/Spotify-Account-Cloner-Backend.git
cd Spotify-Account-Cloner-Backend

# 2. Install dependencies
npm install

# 3. Create a .env file
# (never commit this file)
CLIENT_ID=your_spotify_client_id
CLIENT_SECRET=your_spotify_client_secret

# 4. Run the backend
node app.js
```
The backend runs on:
📡 http://localhost:8888

---
## 🌐 Key Endpoints

| Endpoint | Description |
|-----------|--------------|
| `GET /backend/login1` | Redirects to Spotify for read-only authorisation |
| `GET /backend/login2` | Redirects to Spotify for playlist modification authorisation |
| `GET /backend/callback` | Handles Spotify redirect and exchanges authorisation code for access/refresh tokens |
| `GET /backend/refresh_token` | Refreshes expired access tokens |

---

## 🧰 Tech Stack

| Category | Technology |
|-----------|-------------|
| Backend | Node.js, Express |
| Authentication | Spotify OAuth 2.0 |
| Environment Management | dotenv |
| Networking | CORS, HTTP Requests (via `request`) |
| Cookie Handling | cookie-parser |
| Deployment | Nginx, Cloud or Local Server (port 8888) |

---

## 🧩 Frontend Integration

This backend is designed to work directly with the Spotify Account Cloner Frontend, which handles the user interface, cloning logic, and playlist creation.
The frontend relies entirely on this backend for token exchange and authentication.
Ensure that both services are running and that the frontend’s redirect URL matches the backend’s configured url value.
