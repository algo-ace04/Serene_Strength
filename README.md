# 🌿 Serene Strength — README

**Serene Strength** is a **full-stack personal wellness platform** that helps users build sustainable health habits through **goal tracking**, **AI-assisted recommendations**, and a **beautiful, interactive dashboard**.


---

## 🧠 Vision
Make healthy habits **simple, measurable, and delightful** — combining **lightweight UX**, **robust data tracking**, and an **AI assistant** that understands each user’s preferences and progress.

---

## 🗂️ Table of Contents
1. [Project Overview](#project-overview)  
2. [Features](#features)  
3. [Tech Stack & Tools](#tech-stack--tools)  
4. [Architecture & Data Model](#architecture--data-model)  
5. [API Reference](#api-reference)  
6. [Frontend Structure](#frontend-structure)  
7. [Getting Started (Local Setup)](#getting-started-local-setup)  
8. [Environment Variables](#environment-variables)  
9. [Deployment Guide](#deployment-guide)  
10. [Security & Best Practices](#security--best-practices)  
11. [Testing & Debugging](#testing--debugging)  
12. [Future Roadmap](#future-roadmap)  
13. [Contributors & Contact](#contributors--contact)  
14. [License](#license)

---

## 🧩 Project Overview
**Serene Strength** empowers users to manage and track their **daily, weekly, and long-term wellness goals** across three main areas:

### 🥗 Nutrition
- Water tracker (with visual progress bar)  
- Macronutrient targets (carbs, proteins, fats, fibers)  
- Meal diary (editable meal entries with checkboxes)  
- Persistent data storage in MongoDB  

### 💪 Training
- Workout minutes tracker with ± time increments  
- Multi-level routines (beginner / intermediate / advanced)  
- Per-routine timers with frontend UI controls  
- Add/remove routines dynamically from daily tasks  

### 🧘 Mindfulness
- Yoga & meditation minutes tracking  
- Genre categorization (strengthening, relaxation, focus, mindfulness)  
- Editable and multi-select routines  

Additional highlights:
- **AI chatbot (Gemini API)** for dynamic goal suggestions and motivation  
- **Weekly goal manager** with custom and preset options  
- **Activity heatmap calendar** for visual performance tracking  
- **Favourites system** for quick access to workouts, foods, and poses  
- **Animated motivational header** and **responsive dashboard**

---

## ✨ Features

### 🔐 Authentication & User Management
- Secure **register/login** using **bcrypt** password hashing  
- **JWT-based authentication** — backend issues token, stored in `localStorage`  
- Editable **profile page** with avatar and personal details  

### 📅 Daily Goals & Tracking
- **Water tracking**, **meal diary**, and **macronutrient logging**  
- Real-time progress animation and DB synchronization  

### 💪 Workout & Routines
- Add/subtract workout minutes  
- Multi-select routines across difficulty levels  
- Per-routine timers and “add to favourites” functionality  

### 🧘 Yoga & Meditation
- Minute targets with reset controls  
- Guided/focused genre-based categories  

### 🎯 Weekly Goals
- Editable user goals with preset dropdowns  
- Custom goal creation and progress tracking  
- Motivational messages  

### 📆 Activity Calendar & Heatmap
- Interactive 30-day heatmap (color intensity = minutes or score)  
- Clickable dates for tooltip insights  
- Data fetched from `activity` map (date → minutes)  

### 💖 Favourites
- Manage favourite workouts, meals, and yoga poses  
- Add favourites to dashboard; stored persistently in DB  

### 🤖 AI Assistant (Gemini API)
- Floating AI chat icon expands into a panel  
- User messages are proxied to **Gemini API** via `/api/ai/ask`  
- Assistant returns actionable suggestions like:  
  - “Reduce unnecessary lines in this section”  
  - “Try adding a stretch goal for better engagement”  
  - “Here’s a sample diet for your target calories”
- Confirms before saving goals to user dashboard  

### 🎨 UI & UX
- **Collapsible sidebar** (compact icons expand for labels)  
- **Animated motivational header** with SVG background  
- **Responsive layout** for desktop & mobile  
- **Toasts** for confirmations, warnings, and destructive actions  

---

## 🧰 Tech Stack & Tools

### 🖥️ Frontend
- **HTML5**, **CSS3** , **Tailwind CSS** (modern, responsive, animated)  
- **Vanilla JavaScript (ES6)**  
- `live-server` *(optional for local hosting)*  

### ⚙️ Backend
- **Node.js (v18+)**  
- **Express.js** for API routing  
- `node-fetch` / `undici` — for Gemini API requests  
- `jsonwebtoken` — for JWT handling  
- `bcryptjs` — for password hashing  
- `cors` — for cross-origin resource sharing  

### 🧾 Database
- **MongoDB Atlas (cloud)**  
- **Mongoose ODM** for schema-based data modeling  

### 🧑‍💻 Development & Deployment
- `nodemon` — for local development  
- **GitHub** — for version control  
- **Render / Railway / Heroku** — for backend deployment  
- **Netlify / Vercel / GitHub Pages** — for frontend hosting  

### 🧪 Tools
- **Postman** — for API testing  
- **Chrome DevTools** — for debugging  
- **Git / GitHub** — for collaboration and versioning  

---

## 🧱 Architecture & Data Model

### High-Level Architecture
- **Frontend (Static)** — served via static hosting or local server  
- **Backend (Express)** — handles authentication, routes, AI proxy, and CRUD  
- **MongoDB Atlas** — stores persistent user and activity data  

### Example: `User` Model (Mongoose)
```js
{
_id: ObjectId,
username: String,
email: String,
password: String, // hashed
avatarUrl: String,
goals: [Object],
activities: [Object],
favourites: [Object],
createdAt: Date,
updatedAt: Date
}

