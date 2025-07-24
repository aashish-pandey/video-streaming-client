# 🎬 JaalChitra Client

JaalChitra is the React frontend for a video-streaming platform. It manages user interface flows for authentication, video playback, profile, group chats, and more. This client is meant to be used with the JaalChitra backend, which handles user data and media delivery.

## 🛠 Tech Stack

- **React.js** (Functional components + hooks)
- **React Router v6**
- **react-cookie** for session management
- **@rehooks/online-status** to track connectivity
- **CSS** for basic styling

## 🚦 Access Control

JaalChitra uses cookie-based checks to manage page-level access:

- `loginStatus`: Guards most protected routes.
- `permissionDenied`: Redirects users with restricted access.

There are two wrapper components:
- `ProtectedRoute`: Redirects to `/landing` if not logged in.
- `PermissionRoute`: Redirects to `/permissionDenied` if access is blocked.

## 📁 Routes Overview

### Public Pages
- `/landing`
- `/login`
- `/setPassword`
- `/forgetPassword`

### Protected Pages
- `/home`
- `/profile`
- `/homefeed`
- `/moviesPage`
- `/trendingPage`
- `/chatPage`
- `/watch/:id`
- `/watchBanner/:id`
- `/accountAccessAvailabilityCheck`
- `/permissionDenied`

> 🔐 Cookies like `uemail`, `loginStatus`, and `permissionDenied` are used to determine access and route logic.

### Upload Page
- `/upload` — currently not protected. You may want to wrap this route as well.

## 🔑 Login Flow

The login system:
- Submits user email/password to the backend via `/login`.
- On successful login:
  - Sets `uemail` and `loginStatus` cookies.
  - Navigates to `/home`.
- On failure:
  - Displays error message returned from backend.

> `.env` must contain `REACT_APP_API_CALL_ADDRESS` for API requests.

## 🚀 Getting Started

```bash
npm install
npm start
```

Ensure that your backend server is running and accessible at the API endpoint configured in `.env`.

## 📂 Folder Notes

- `components/` — shared UI parts (e.g., video player, navigation)
- `pages/` — major app screens
- `App.js` — main router + layout
- `App.css` — global styles

## 💡 Environment Variable Required

Make sure to define the API base URL in your `.env` file:

```env
REACT_APP_API_CALL_ADDRESS=http://localhost:5000
```
