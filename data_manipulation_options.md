# Data Manipulation Requirements

After retrieving book data from either the **static JSON file** or the **Google Books API**, the backend must apply **at least two data manipulation step** before returning results to the frontend.  
Each step should work independently and also function correctly when chained together in sequence.
The goal is to demonstrate understanding of how data is filtered, transformed, and structured within an API layer.

---

## 1. Filtering
Eliminate items that do not meet specified conditions.

### Examples
- **Filter by publication year**  
  Only return books published after 1900:
  ```js
  data = data.filter(book => parseInt(book.year) >= 1900);
  ```
- **Filter by presence of author**  
  Skip entries with missing `author` fields.
- **Filter by search relevance**  
  Match substring in title, case-insensitive:
  ```js
  data = data.filter(book => 
    book.title.toLowerCase().includes(query.toLowerCase())
  );
  ```

---

## 2. Sorting
Arrange results to improve usability.

### Examples
- **Alphabetically by title**
  ```js
  data.sort((a, b) => a.title.localeCompare(b.title));
  ```
- **By publication year (descending)**
  ```js
  data.sort((a, b) => (b.year || 0) - (a.year || 0));
  ```

---

## 3. Normalization
Standardize inconsistent or incomplete fields from the source.

### Examples
- Replace missing author names:
  ```js
  if (!book.author) book.author = "Unknown";
  ```
- Trim whitespace, unify capitalization:
  ```js
  book.title = book.title.trim();
  book.author = book.author.toUpperCase();
  ```
- Handle missing or partial publication dates (e.g., `2024-06` → `2024`).

---

## 4. Aggregation
Compute summary or derived values.

### Examples
- Count number of results per author.
- Group results by decade of publication.
- Return metadata:
  ```json
  {
    "count": 8,
    "results": [ ... ]
  }
  ```

---

## 5. Transformation
Change structure or fields before sending data to the frontend.

### Examples
- **Simplify Google Books API structure**
  ```js
  data = apiData.items.map(item => ({
    id: item.id,
    title: item.volumeInfo.title,
    author: item.volumeInfo.authors?.[0] ?? "Unknown",
    year: item.volumeInfo.publishedDate?.slice(0, 4) ?? "N/A"
  }));
  ```
- **Add computed field**
  ```js
  book.display = `${book.title} (${book.year})`;
  ```

---

## 6. Caching or Sampling (Optional Advanced)
- Return only the first 10 matches (`slice(0, 10)`).
- Cache results for repeated search terms within session memory.

---

## Deliverable Expectation
Your backend should:
1. Retrieve raw data (from JSON or API).  
2. Apply **at least one** filtering, sorting, or transformation step.  
3. Return the cleaned, consistent dataset to the frontend.  
4. Document your manipulation process in your **requirements document** and in code comments.
