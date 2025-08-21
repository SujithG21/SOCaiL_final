Project Overview

SOCaiL is a full‑stack platform designed for social‑media creators. It combines an Express/MongoDB backend, a React/Tailwind frontend, and Python utilities to deliver tools for authentication, habit tracking, trend compilation, content generation, and AI‑assisted chat.

What the App Can Do
* User Authentication – Register and log in with hashed passwords; successful login issues a JWT token used to access protected routes  
* Progress Tracking – Records daily posting streaks in MongoDB and exposes CRUD endpoints for retrieving or updating a user’s current and highest streaks 
* AI Chatbot – Stores chat history and refines model output with Google’s Gemini API before returning it to the user 
* Content Writer – Generates scripts and hashtags via a separate Flask service that wraps Gemini; users can refine results with additional prompts  
* Trend Compiler – Aggregates Twitter, Instagram, and TikTok trends from local JSON files and offers incremental or full lists in the UI 
* Chat Interface – A React component retrieves prior conversations and posts new questions using the stored JWT token 

How It Works
1. Routing & State Management – React Router and a custom PrivateRoute guard control access to dashboard features after token verification 
2. Backend Services – Express middleware enforces JWT authentication; Mongoose schemas (User, Chat, ProgressTracker) persist data in MongoDB  
3. External APIs
    * The chatbot sends queries to an NGROK‑exposed model, then refines replies through Gemini before saving them 
    * The Flask microservice calls Gemini directly to produce content and hashtags 
4. Trend Data Acquisition – Python scrapers fetch Instagram and Twitter trends and store them as CSV/JSON for the React compiler to consume  
Factors Involved
* Security & Auth: JWT tokens, bcrypt hashing, and Express middleware safeguard user routes 
* Data Layer: MongoDB via Mongoose manages users, chat logs, and posting streaks 
* Cross‑Service Communication: REST calls between React, Express, NGROK endpoints, and the Flask Gemini wrapper coordinate data flow  
* External Dependencies: Google Generative AI (Gemini), axios/fetch for HTTP, React hooks, and Tailwind for UI styling.





# React + Vite

This template provides a minimal setup to get React working in Vite with HMR and some ESLint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh
