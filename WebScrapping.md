


# 🏆 Hackathon Project: AI Web Scraper & Analyzer

## 📋 Phase 1: Preparation & Architecture

- [ ] **Choose Tech Stack:**
    
    - **Pipeline (Colab):** Python, `requests`, `BeautifulSoup`, `pydantic` (for JSON schema enforcement), LLM SDK (e.g., `openai` or `google-generativeai`).
        
    - **Backend:** FastAPI (Python) - _Fastest for moving Colab code to an API_.
        
    - **Frontend:** Vanilla HTML/CSS/JS or a simple React/Next.js app.
        
    - **Database:** SQLite (built into Python) or a simple `results.json` file to store scraped data for the `/results` endpoint.
        
- [ ] **Get API Keys:** Generate API key for your chosen LLM (OpenAI, Anthropic, or Gemini).
    
- [ ] **Prepare Sample URLs:** Find 5-10 varied B2B company URLs for testing (e.g., local IT agencies, logistics companies).
    

---

## 🧪 Phase 2: Google Colab Pipeline (Subtask 1)

_Goal: Build the extraction logic within the required Colab structure._

### 🟢 Add a New Cell (At the very top)

You **must** add a cell before the template cells to install dependencies.

- [ ] Create **Cell 0**:
    
    Python
    
    ```
    !pip install requests beautifulsoup4 pydantic [your_llm_library]
    ```
    

### 🟡 Modify Cell 1 (The Core Logic)



```
# ================================

# 🏆 Hackathon Template Notebook

# Prospect Research Agent

# ================================

  

# ========= CONFIG =========

# 🔑 Add your API key here

API_KEY = "YOUR_API_KEY"

  
  
  

# ========= REQUIRED FUNCTION =========

def enrich_company(url: str) -> dict:

    """

    Input: Company URL

    Output: Structured company profile (STRICT FORMAT)

    """

  

    # TODO: Implement

    pass
```
Do not change the function signature `def enrich_company(url: str) -> dict:`. Implement your logic inside it.

- [ ] **Import Libraries:** Add `import requests`, `from bs4 import BeautifulSoup`, `import json`, etc., at the top.
    
- [ ] **Step 1: Base Scraping:** Fetch the HTML of the given `url`. Use headers `{"User-Agent": "Mozilla/5.0"}` to avoid basic blocks.
    
- [ ] **Step 2: Smart Link Discovery (Fuzzy Matching):**
    
    - Parse base HTML to find all `<a href="...">` tags.
        
    - Look for keywords in URLs/text like `"about"`, `"contact"`, `"services"`.
        
    - Compile a list of 2-3 highest-priority sub-page URLs.
        
- [ ] **Step 3: Multi-Approach Extraction & Fallback:**
    
    - Try fetching the main page + priority sub-pages.
        
    - _Fallback 1:_ Standard `requests.get`.
        
    - _Fallback 2:_ If blocked (403), try passing different headers or a simple proxy if available.
        
- [ ] **Step 4: Token Optimization (Crucial):**
    
    - Extract text using `soup.get_text(separator=' ', strip=True)`.
        
    - Remove `<script>`, `<style>`, `<nav>`, `<footer>` tags before extracting text.
        
    - Truncate the final text string to fit comfortably within your chosen LLM's context window (e.g., first 15,000 characters).
        
- [ ] **Step 5: LLM Prompting:**
    
    - Pass the cleaned text to the LLM.
        
    - **Prompt Engineering:** Include the exact JSON schema required in your system prompt. Explicitly state: _"If a field is missing, return an empty string "". DO NOT hallucinate data."_
        
    - Force JSON output (e.g., using OpenAI's `response_format={ "type": "json_object" }` or Gemini's `response_mime_type="application/json"`).
        
- [ ] **Step 6: Return Output:** Parse the LLM's JSON response and `return` it as a Python dictionary.
    

### 🔴 Modify Cell 2 (Main Execution & The Golden Rule)

You **must** change the hardcoded `urls` array to an input prompt so judges can paste their own array.

- [ ] Modify the `urls` assignment to accept user input:
    
    Python
    
    ```
    import ast
    
    if __name__ == "__main__":
        # 👉 THE GOLDEN RULE: Ask for input
        user_input = input("Paste the array of URLs here: ")
        try:
            # Convert string representation of list to actual Python list
            urls = ast.literal_eval(user_input) 
        except:
            print("Invalid format. Using fallbacks.")
            urls = ["https://example1.com", "https://example2.com"]
    
        results = []
        # ... (keep the existing for loop) ...
    ```
    
- [ ] **Save to JSON:** Implement the TODO to save results:
    
    Python
    
    ```
        # Save results to JSON file
        with open("results.json", "w") as f:
            json.dump(results, f, indent=4)
    ```
    

---

## 🌐 Phase 3: Web App Backend (Subtask 2)

_Goal: Turn your Colab script into an API._

- [ ] **Setup Project:** Create a new folder, set up a virtual environment, `pip install fastapi uvicorn requests beautifulsoup4 ...`
    
- [ ] **Port Code:** Copy your `enrich_company` function from Colab into a `scraper.py` file.
    
- [ ] **Create `main.py` (FastAPI):**
    
    - [ ] Initialize FastAPI app.
        
    - [ ] Set up a database mechanism (a simple SQLite DB using `sqlite3` or an in-memory Python list combined with a `data.json` file for persistence).
        
- [ ] **Build `POST /enrich` API:**
    
    - Accepts JSON: `{"website_name": "...", "url": "..."}`.
        
    - Calls `enrich_company(url)`.
        
    - Saves the resulting dictionary to your database.
        
    - Returns the exact dictionary.
        
- [ ] **Build `GET /results` API:**
    
    - Queries your database.
        
    - Returns a list of all previously enriched company dictionaries.
        

---

## 🖥️ Phase 4: Web App Frontend (Subtask 2)

_Goal: Build the UI to consume your APIs._

- [ ] **Layout:** Create a clean, single-page UI (HTML/CSS or React).
    
- [ ] **Form Section (Enrich):**
    
    - [ ] Input: Website Name (for record-keeping).
        
    - [ ] Input: Website URL.
        
    - [ ] Button: "Enrich" (Submit).
        
    - [ ] **Bonus:** Add a loading spinner/text ("Scraping and analyzing AI insights...") while the API call is in progress.
        
- [ ] **Results Display Section:**
    
    - [ ] Area to render the single output of the "Enrich" call. Design a nice card showing the business insights, and specifically format the `mail` array nicely (e.g., as tags/pills).
        
- [ ] **Database Section (Show All):**
    
    - [ ] Button: "Show All Results".
        
    - [ ] Fetches `/results`.
        
    - [ ] Renders a data table or a CSS grid of cards for all historical data. Ensure missing data (e.g., "") renders cleanly as "N/A" on the UI.
        

---

## 🚀 Phase 5: Deployment & Final Testing

- [ ] **Deploy Backend:** Push code to GitHub. Connect to **Render** (Web Service) or **Railway**. (Ensure you add your `API_KEY` to the environment variables on the hosting platform).
    
- [ ] **Deploy Frontend:** If separate, deploy to **Vercel** or **Netlify**. If served by FastAPI, it will deploy with the backend.
    
- [ ] **Test the Flow:**
    
    - [ ] Open Live App -> Click "Show All Results" (should be empty or show pre-processed test data).
        
    - [ ] Enter a completely new URL (e.g., a local plumber or software agency) -> Click "Enrich".
        
    - [ ] Verify the backend doesn't crash, the UI shows a loading state, and the final JSON displays correctly.
        
- [ ] **Colab Final Check:** Clear all outputs in Colab. Run all cells. Paste a test array into the input box. Ensure `results.json` is generated flawlessly.
    
- [ ] **Submit:** Zip your code, copy your live URL, and ensure Colab sharing is set to "Anyone with the link can view".