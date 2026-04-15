You are a **senior AI engineer + full-stack architect** tasked with building a **production-ready hackathon project** called:

# 🏆 AI Web Scraper & Business Analyzer

Your goal is to generate **complete, runnable code** with **clean structure**, **modular design**, and **clear documentation**.

---

# ⚠️ CORE REQUIREMENTS (STRICT)

### 1. Architecture

Build a system with 3 parts:

### 🧪 A. Google Colab Pipeline

- Python-based scraping + AI enrichment
    
- Must follow **given function signature EXACTLY**:
    

```python
def enrich_company(url: str) -> dict:
```

- Must include:
    
    - requests + BeautifulSoup scraping
        
    - smart internal link discovery (about/contact/services)
        
    - fallback scraping strategy
        
    - text cleaning + token optimization
        
    - LLM-based structured extraction
        
    - strict JSON schema enforcement using `pydantic`
        

---

### 🌐 B. Backend (FastAPI)

- REST API with:
    
    - `POST /enrich`
        
    - `GET /results`
        
- Must reuse the same `enrich_company` logic
    
- Must store results in:
    
    - SQLite OR JSON file
        

---

### 🖥️ C. Frontend

- Simple UI (HTML/CSS/JS or React)
    
- Features:
    
    - Input form (name + URL)
        
    - Enrich button
        
    - Loading state
        
    - Results card UI
        
    - "Show All Results" section
        

---

# ⚠️ CRITICAL RULES (DO NOT BREAK)

### ❗ RULE 1: NO HALLUCINATION

If data is missing:

```json
"field": ""
```

---

### ❗ RULE 2: STRICT JSON OUTPUT

Return ONLY valid JSON from LLM

---

### ❗ RULE 3: GOOGLE COLAB FILE HANDLING (VERY IMPORTANT)

Since Google Colab does not persist files reliably:

👉 You MUST:

- Create **local file equivalents** for ALL Colab outputs
    
- Include them in project structure
    
- Mention exact file paths in README
    

Example:

- `colab/results.json` → also saved as `backend/data/results.json`
    

---

### ❗ RULE 4: CLEAN PROJECT STRUCTURE

Generate full folder structure like:

```
project-root/
│
├── colab/
│   ├── scraper_colab.ipynb
│   ├── results.json
│
├── backend/
│   ├── main.py
│   ├── scraper.py
│   ├── database.py
│   ├── models.py
│   ├── data/
│   │   └── results.json
│
├── frontend/
│   ├── index.html
│   ├── style.css
│   ├── script.js
│
├── requirements.txt
├── README.md
```

---

# 🧠 SCRAPING LOGIC REQUIREMENTS

### Step 1: Fetch HTML

- Use headers:
    

```python
{"User-Agent": "Mozilla/5.0"}
```

---

### Step 2: Smart Link Discovery

Extract `<a>` tags and prioritize:

- about
    
- contact
    
- services
    

---

### Step 3: Multi-page scraping

Scrape:

- main page
    
- 2–3 priority pages
    

---

### Step 4: Cleaning

- Remove:
    
    - script
        
    - style
        
    - nav
        
    - footer
        
- Use:
    

```python
soup.get_text(separator=" ", strip=True)
```

- Limit text (~15k chars)
    

---

### Step 5: LLM Prompt

Use this structure:

- Extract:
    
    - company_name
        
    - services
        
    - industry
        
    - emails
        
    - phone
        
    - summary
        
    - location
        
- Add instruction:
    

```
If missing → return ""
DO NOT hallucinate
```

---

### Step 6: Schema Validation

Use `pydantic` model like:

```python
class CompanyProfile(BaseModel):
    company_name: str
    services: list[str]
    industry: str
    emails: list[str]
    phone: str
    summary: str
    location: str
```

---

# 🔌 API REQUIREMENTS

### POST /enrich

Input:

```json
{
  "website_name": "ABC",
  "url": "https://example.com"
}
```

Output:

- enriched JSON
    
- store in DB/file
    

---

### GET /results

- Return all stored data
    

---

# 🎨 FRONTEND REQUIREMENTS

- Clean UI
    
- Show:
    
    - company name
        
    - summary
        
    - emails (as tags)
        
- Handle empty values → show "N/A"
    
- Show loading state
    

---

# 📄 README REQUIREMENTS (IMPORTANT)

README must include:

### 1. Setup Instructions

- Backend
    
- Frontend
    
- Colab
    

---

### 2. File Mapping (VERY IMPORTANT)

Explicitly explain:

|Colab File|Local Equivalent|
|---|---|
|colab/results.json|backend/data/results.json|

---

### 3. API Usage

---

### 4. Deployment Steps

Mention:

- Render
    
- Railway
    
- Vercel
    
- Netlify
    

---

# 🧾 OUTPUT FORMAT (VERY IMPORTANT)

You must generate:

### 1. Folder Structure

### 2. All Code Files (FULL CODE)

- No partial snippets
    
- No "..." placeholders
    

### 3. README.md

---

# ⚡ QUALITY EXPECTATIONS

- Clean, readable code
    
- Proper comments
    
- Modular design
    
- Error handling included
    
- Beginner-friendly but production-ready
    

---

# 🚀 FINAL INSTRUCTION

Generate the **ENTIRE PROJECT** step-by-step with:

1. Folder structure
    
2. Colab code
    
3. Backend code
    
4. Frontend code
    
5. README
    

DO NOT skip anything.
