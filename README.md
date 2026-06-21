<div align="center">

# 🍽️ Recipe Genie

### _Your intelligent cooking companion — from pantry to plate_

[![Live Demo](https://img.shields.io/badge/🌐_Live_Demo-your-vercel-app.vercel.app-10b981?style=for-the-badge)](https://your-vercel-app.vercel.app)
[![GitHub](https://img.shields.io/badge/GitHub-nityaxbatra--RecipeGenie-181717?style=for-the-badge&logo=github)](https://github.com/nityaxbatra/RecipeGenie.git)
[![License: ISC](https://img.shields.io/badge/License-ISC-yellow.svg?style=for-the-badge)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?style=for-the-badge&logo=node.js)](https://nodejs.org)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react)](https://react.dev)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Neon-336791?style=for-the-badge&logo=postgresql)](https://neon.tech)
[![Gemini](https://img.shields.io/badge/Google_Gemini-2.5_Flash-4285F4?style=for-the-badge&logo=google)](https://ai.google.dev)

---

_Recipe Genie is a full-stack recipe application that generates personalized recipes from your pantry ingredients — complete with meal planning, shopping lists, and nutritional insights._

[**View Live →**](https://your-vercel-app.vercel.app) · [**Report Bug**](https://github.com/nityaxbatra/RecipeGenie/issues) · [**Request Feature**](https://github.com/nityaxbatra/RecipeGenie/issues)

</div>

---

## 🌟 Overview

Recipe Genie is a **production-grade, full-stack cooking assistant** that turns pantry ingredients into meal plans. Powered by **Google Gemini 2.5 Flash**, it intelligently generates recipes tailored to available ingredients, dietary restrictions, cuisine preferences, and time constraints.

Built using a **PERN-style stack** with a React + Vite frontend, Express backend, and PostgreSQL database, the app handles everything from authentication to AI-powered meal planning in a clean, responsive interface.

> **Why Recipe Genie?** This app generates _novel, personalized recipes on demand_ and connects them directly to pantry inventory, weekly meal schedules, and grocery lists in one unified workflow.

---

## ✨ Features

### 🔐 Authentication & Profiles

- Secure registration and login with email/password
- Passwords hashed with **bcrypt**
- **JWT tokens** for stateless auth
- Profile management: update name, email, and preferences
- Account deletion with cascading data cleanup

### 🥦 Smart Pantry Management

- Add, edit, and delete pantry items with categories
- Expiry date tracking and alerting
- Quantity management and low-stock visibility
- Sort and filter pantry items by category or expiry
- Pantry stats dashboard showing totals and expiring items

### 🤖 AI Recipe Generation

- Generate recipes from **pantry items** or **manual ingredient input**
- Choose cuisine type and dietary restrictions
- Adjust serving size and cooking time preference
- Each recipe includes:
  - Name, description, cuisine, and difficulty
  - Dietary tags and allergen info
  - Ingredient list with quantities
  - Step-by-step cooking instructions
  - Nutrition facts (calories, protein, carbs, fats, fiber)
  - Smart AI cooking tips

### 📚 Recipe Collection

- Save generated recipes to your personal collection
- Search and filter by cuisine, difficulty, and dietary tags
- Delete saved recipes with confirmation

### 📅 Meal Planner

- Weekly calendar view with meal slots
- Assign saved recipes to breakfast, lunch, and dinner
- Real-time meal updates and visual feedback
- Weekly meal stats and upcoming meal preview

### 🛒 Smart Shopping List

- Auto-generate grocery lists from meal plans
- Merge and sum ingredients from multiple recipes
- Add manual shopping items
- Mark items purchased and sync to pantry
- Clear purchased or all items at once

### ⚙️ User Preferences & Settings

- Default dietary restrictions and cuisine preferences
- Default serving size saved in preferences
- Secure password change flow
- Preferences synced across the app

---

## 🛠 Tech Stack

| Layer           | Technology              | Purpose                       |
| --------------- | ----------------------- | ----------------------------- |
| **Frontend**    | React 19 + Vite         | Fast SPA with HMR             |
| **Styling**     | Tailwind CSS v4         | Utility-first responsive UI   |
| **Routing**     | React Router v6         | Client-side navigation        |
| **HTTP Client** | Axios + Interceptors    | JWT injection, error handling |
| **State**       | React Context API       | Global auth state             |
| **Backend**     | Node.js + Express.js    | REST API server               |
| **Database**    | PostgreSQL (Neon)       | Relational data, serverless   |
| **ORM**         | Sequelize + `pg`        | Safe database access          |
| **Auth**        | JWT + bcrypt.js         | Stateless, secure auth        |
| **AI**          | Google Gemini 2.5 Flash | Recipe generation             |
| **Dev Tools**   | Nodemon, ESLint         | Auto-reload, code quality     |

---

## 🏗 System Architecture

```mermaid
graph TB
    subgraph Client["🖥️ Frontend (React + Vite)"]
        UI[React Pages & Components]
        CTX[AuthContext]
        SVC[API Service Layer<br/>Axios Interceptor]
        UI <--> CTX
        UI <--> SVC
    end

    subgraph Server["⚙️ Backend (Express.js)"]
        MW[Auth Middleware<br/>JWT Verify]
        RT[Route Layer]
        CTRL[Controllers]
        MDL[Models<br/>Parameterized SQL]

        MW --> RT
        RT --> CTRL
        CTRL --> MDL
    end

    subgraph AI["🤖 AI Layer"]
        GEM[Google Gemini 2.5 Flash]
        UTIL[gemini.js Utility<br/>Prompt Engineering]
        UTIL --> GEM
    end

    subgraph DB["🗄️ Database (PostgreSQL on Neon)"]
        USERS[(users)]
        PREFS[(user_preferences)]
        PANTRY[(pantry_items)]
        RECIPES[(recipes)]
        INGR[(recipe_ingredients)]
        NUTR[(recipe_nutrition)]
        MEALS[(meal_plans)]
        SHOP[(shopping_list_items)]
    end

    SVC -- "HTTPS + Bearer Token" --> MW
    CTRL -- "Generate Recipe" --> UTIL
    MDL -- "SQL Queries" --> DB

    style Client fill:#ecfdf5,stroke:#10b981
    style Server fill:#eff6ff,stroke:#3b82f6
    style AI fill:#fef3c7,stroke:#f59e0b
    style DB fill:#f5f3ff,stroke:#8b5cf6
```

---

## 🗂 Project Structure

```
AI-Recipe-Generator-main/
├── backend/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── utils/
│   ├── migrate.js
│   ├── server.js
│   ├── package.json
│   └── .env
└── frontend/
    ├── public/
    ├── src/
    │   ├── components/
    │   ├── context/
    │   ├── pages/
    │   └── services/
    ├── package.json
    ├── package-lock.json
    ├── vite.config.js
    ├── .env.example
    └── README.md
```

---

## 🗄 Database Schema

The schema uses **UUID primary keys**, **JSONB** for instructions, **PostgreSQL arrays** for dietary data, and **indexes** for performance.

```sql
-- Core entities (simplified)

users                    -- id (UUID), email, password_hash, name
user_preferences         -- user_id → cuisines[], dietary_restrictions[]
pantry_items             -- user_id, name, quantity, unit, category, expiry_date
recipes                  -- user_id, name, cuisine, difficulty, instructions (JSONB)
recipe_ingredients       -- recipe_id, name, quantity, unit
recipe_nutrition         -- recipe_id, calories, protein, carbs, fat, fiber
meal_plans               -- user_id, recipe_id, date, meal_type (UNIQUE constraint)
shopping_list_items      -- user_id, name, quantity, category, is_checked
```

**Key design decisions:**

- Recipes use a **normalized structure** for ingredients and nutrition
- `instructions` stored as **JSONB array** for flexible rendering
- `meal_plans` uses **UNIQUE(user_id, date, meal_type)** to prevent duplicates
- **Cascade deletes** keep user data clean on account removal
- **Indexes** on `user_id`, `expiry_date`, and `is_checked`

---

## 📡 API Reference

All protected endpoints require: `Authorization: Bearer <token>`

All responses follow:

```json
{
  "success": true,
  "message": "Human-readable status",
  "data": { ... }
}
```

### Auth — `/api/auth`

| Method | Endpoint          | Auth | Description                  |
| ------ | ----------------- | ---- | ---------------------------- |
| `POST` | `/signup`         | ❌   | Register new user            |
| `POST` | `/login`          | ❌   | Login, receive JWT           |
| `POST` | `/reset-password` | ❌   | Password reset (placeholder) |
| `GET`  | `/me`             | ✅   | Get authenticated user       |

### Users — `/api/users`

| Method   | Endpoint           | Auth | Description               |
| -------- | ------------------ | ---- | ------------------------- |
| `GET`    | `/profile`         | ✅   | Profile + preferences     |
| `PUT`    | `/profile`         | ✅   | Update name/email         |
| `PUT`    | `/preferences`     | ✅   | Update dietary prefs      |
| `PUT`    | `/change-password` | ✅   | Secure password change    |
| `DELETE` | `/account`         | ✅   | Delete account + all data |

### Recipes — `/api/recipes`

| Method   | Endpoint       | Auth | Description               |
| -------- | -------------- | ---- | ------------------------- |
| `POST`   | `/generate`    | ✅   | AI recipe generation      |
| `GET`    | `/suggestions` | ✅   | Pantry-based recipe ideas |
| `GET`    | `/`            | ✅   | List recipes              |
| `GET`    | `/recent`      | ✅   | Recent recipes            |
| `GET`    | `/stats`       | ✅   | Recipe statistics         |
| `GET`    | `/:id`         | ✅   | Full recipe detail        |
| `POST`   | `/`            | ✅   | Save recipe               |
| `PUT`    | `/:id`         | ✅   | Update recipe             |
| `DELETE` | `/:id`         | ✅   | Delete recipe             |

### Pantry — `/api/pantry`

| Method   | Endpoint         | Auth | Description         |
| -------- | ---------------- | ---- | ------------------- |
| `GET`    | `/`              | ✅   | List pantry items   |
| `GET`    | `/stats`         | ✅   | Pantry statistics   |
| `GET`    | `/expiring-soon` | ✅   | Items expiring soon |
| `POST`   | `/`              | ✅   | Add pantry item     |
| `PUT`    | `/:id`           | ✅   | Update pantry item  |
| `DELETE` | `/:id`           | ✅   | Delete pantry item  |

### Meal Plans — `/api/meal-plans`

| Method   | Endpoint    | Auth | Description            |
| -------- | ----------- | ---- | ---------------------- |
| `GET`    | `/weekly`   | ✅   | Weekly meal plan view  |
| `GET`    | `/upcoming` | ✅   | Upcoming meals         |
| `GET`    | `/stats`    | ✅   | Meal plan statistics   |
| `POST`   | `/`         | ✅   | Assign meal slot       |
| `DELETE` | `/:id`      | ✅   | Remove meal assignment |

### Shopping List — `/api/shopping-list`

| Method   | Endpoint         | Auth | Description                       |
| -------- | ---------------- | ---- | --------------------------------- |
| `GET`    | `/`              | ✅   | List shopping items               |
| `POST`   | `/generate`      | ✅   | Auto-generate from meal plan      |
| `POST`   | `/`              | ✅   | Add manual item                   |
| `PUT`    | `/:id`           | ✅   | Update item                       |
| `PUT`    | `/:id/toggle`    | ✅   | Toggle checked status             |
| `DELETE` | `/:id`           | ✅   | Remove item                       |
| `DELETE` | `/clear/checked` | ✅   | Remove checked items              |
| `DELETE` | `/clear/all`     | ✅   | Clear all items                   |
| `POST`   | `/add-to-pantry` | ✅   | Sync checked items back to pantry |

---

## 🚀 Getting Started

### Prerequisites

- Node.js v18 or higher
- npm v9+
- PostgreSQL database
- Google Gemini API key

### 1. Clone

```bash
git clone https://github.com/nityaxbatra/RecipeGenie.git
cd RecipeGenie/AI-Recipe-Generator-main/AI-Recipe-Generator-main
```

### 2. Backend

```bash
cd backend
npm install
```

### 3. Frontend

```bash
cd ../frontend
npm install
```

### 4. Run locally

```bash
cd backend
npm run dev
```

```bash
cd ../frontend
npm run dev
```

Open the Vite URL shown in the terminal.

---

## 🔐 Environment Variables

### backend/.env

```env
PORT=8000
DATABASE_URL=postgres://username:password@localhost:5432/recipe_genie_db
JWT_SECRET=your_jwt_secret
NODE_ENV=development
GEMINI_API_KEY=your_google_gemini_api_key
```

### frontend/.env

```env
VITE_API_URL=http://localhost:8000/api
```

> Do not commit `.env` files.

---

## 📄 License

ISC

---

<div align="center">

**Built with ❤️ by [nityaxbatra](https://github.com/nityaxbatra)**

</div>
