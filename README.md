# Book Search Application – Assignment

## Overview
You will design a **Book Search web application** that connects a simple frontend to a backend service.  
The starter materials include a **wireframe** and **sample JSON data**.  
Your goal is to complete the system design, write a **requirements document**, and build a minimal working prototype.

---

## Application Flow
1. **Frontend**
   - Based on the provided wireframe.
   - Includes:
     - A search bar for book titles.
     - A results list with clickable book entries.
     - A details section displaying selected book info.

2. **Backend**
   - Implements two REST endpoints:
     - `GET /api/books?title=term` — searches books.
     - `GET /api/books/:id` — retrieves details for one book.
   - Begins with a **static JSON file** for testing.
   - Later connects to the **Google Books API**:
     ```
     https://www.googleapis.com/books/v1/volumes?q=<term>
     ```
   - Must include **one data manipulation step** (e.g., filter, sort, format, or simplify results).

3. **Data Flow**
   - User enters a title → frontend sends GET request → backend retrieves and reformats data → response displayed on page.

---

## Your Task
- Write a **short requirements document (1–2 pages)** describing:
  1. The system’s purpose and scope.
  2. Functional and nonfunctional requirements.
  3. Data sources and how they are used.
  4. Example input/output for each endpoint.
  5. How the wireframe and data flow diagram support your design.
- Then, implement a working version that matches your document.

---

## Deliverables
- `requirements.pdf` — clear, complete, and aligned with diagrams.  
- `server.js` — Express backend with endpoints and transformation.  
- `index.html` — minimal frontend matching the wireframe.  
- `README.md` — this file.

---

## Submission
Push all files to your GitHub Classroom repository before the deadline.  
Be prepared to discuss how your written requirements informed your implementation.
