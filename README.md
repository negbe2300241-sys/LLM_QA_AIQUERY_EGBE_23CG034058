# CSC331 Project 2: AI Query Web Application

## 📋 Project Overview

This project is a full-stack web application that integrates with an external AI API to process user queries. The application features a Flask backend, a responsive frontend, SQLite database for query logging, and deployment on Render.

---

## 🎯 Project Objectives

- Create a web application that queries an external AI service
- Implement a RESTful API backend using Flask
- Store query history in a SQLite database
- Deploy the application to a cloud hosting platform (Render)
- Follow best practices for security and code organization

---

## 📁 Project Structure

```
YOUR-SURNAME_MAT.NO_AI_QUERY_APP/
│
├── app.py                      # Flask backend application
├── requirements.txt            # Python dependencies
├── link_to_my_web_app.txt     # Hosted application URL
├── .env                        # Environment variables (API keys)
├── .gitignore                 # Git ignore rules
├── queries.db                 # SQLite database (auto-generated)
│
├── templates/
│   └── index.html             # Frontend HTML page
│
└── static/                    # Optional static assets
    └── style.css              # CSS styling
```

---

## 🔧 Technical Stack

- **Backend Framework:** Flask (Python)
- **Database:** SQLite3
- **AI API:** Google Gemini AI / Cohere
- **Frontend:** HTML5, CSS3, JavaScript (Vanilla)
- **Deployment:** Render
- **Version Control:** Git/GitHub

---

## 📄 File Descriptions

### 1. **app.py** (Backend)
The main Flask application that:
- Serves the frontend HTML page
- Provides API endpoints for query processing
- Integrates with external AI API (Gemini/Cohere)
- Manages SQLite database operations
- Handles error logging and response formatting

**Key Features:**
- RESTful API endpoint (`/api/query`)
- Database initialization and query storage
- Environment variable management
- CORS handling for API requests

### 2. **templates/index.html** (Frontend)
The user interface featuring:
- Clean, responsive design
- Text input field for user queries
- Submit button with loading states
- Dynamic response display area
- Asynchronous AJAX requests (no page reload)

**User Flow:**
1. User enters a question
2. Clicks submit button
3. Question sent to backend via AJAX
4. AI response displayed without page refresh

### 3. **requirements.txt**
Lists all Python dependencies:
```
Flask==3.0.0
gunicorn==21.2.0
google-generativeai==0.3.0
python-dotenv==1.0.0
requests==2.31.0
```

### 4. **.env**
Stores sensitive configuration:
```
GEMINI_API_KEY=your_actual_api_key_here
```
**⚠️ IMPORTANT:** Never commit this file to GitHub!

### 5. **.gitignore**
Protects sensitive files:
```
.env
__pycache__/
*.pyc
*.pyo
venv/
.DS_Store
```

### 6. **queries.db**
SQLite database (auto-generated) with schema:
```sql
CREATE TABLE queries (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    user_query TEXT NOT NULL,
    ai_response TEXT NOT NULL,
    timestamp DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

### 7. **link_to_my_web_app.txt**
Contains the deployed application URL:
```
https://your-surname-your-matno-ai-app.onrender.com
```

---

## 🚀 Setup Instructions

### Local Development

1. **Clone/Create Project Directory:**
   ```bash
   mkdir YOUR-SURNAME_MAT.NO_AI_QUERY_APP
   cd YOUR-SURNAME_MAT.NO_AI_QUERY_APP
   ```

2. **Create Virtual Environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure Environment Variables:**
   - Create `.env` file
   - Add your API key: `GEMINI_API_KEY=your_key_here`

5. **Run Application:**
   ```bash
   python app.py
   ```
   - Access at: `http://localhost:5000`

---

## 🌐 Deployment on Render

### Step 1: Obtain AI API Key
1. Visit [Google AI Studio](https://makersuite.google.com/app/apikey)
2. Create a new API key
3. Copy the key for later use

### Step 2: GitHub Repository Setup
1. Create a new GitHub repository
2. Initialize Git in your project folder:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: CSC331 AI Query App"
   git branch -M main
   git remote add origin https://github.com/yourusername/your-repo.git
   git push -u origin main
   ```

### Step 3: Render Deployment
1. **Sign up/Login** to [Render](https://render.com)
2. **Create New Web Service:**
   - Click "New +" → "Web Service"
   - Connect your GitHub repository
   
3. **Configure Service:**
   - **Name:** `your-surname-your-matno-ai-app`
   - **Region:** Choose closest to you
   - **Branch:** `main`
   - **Root Directory:** Leave blank
   - **Runtime:** Python 3
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `gunicorn app:app`
   
4. **Add Environment Variables:**
   - Click "Environment" tab
   - Add variable:
     - **Key:** `GEMINI_API_KEY`
     - **Value:** Your actual API key

5. **Deploy:**
   - Click "Create Web Service"
   - Wait for deployment (5-10 minutes)
   - Copy your live URL

### Step 4: Update link_to_my_web_app.txt
Add your Render URL to the file:
```
https://your-surname-your-matno-ai-app.onrender.com
```

---

## 🔒 Security Best Practices

1. **Never commit `.env` files** to version control
2. **Use environment variables** for sensitive data
3. **Validate user input** before processing
4. **Implement rate limiting** to prevent abuse
5. **Use HTTPS** in production (Render provides this)
6. **Sanitize database inputs** to prevent SQL injection

---

## 🧪 Testing Your Application

### Local Testing
1. Start the Flask app
2. Open browser to `http://localhost:5000`
3. Enter test queries
4. Verify responses are displayed
5. Check `queries.db` for stored records

### Production Testing
1. Visit your Render URL
2. Test various query types
3. Verify response times
4. Check error handling

---

## 📊 Database Schema

**Table: queries**

| Column | Type | Description |
|--------|------|-------------|
| id | INTEGER | Primary key (auto-increment) |
| user_query | TEXT | User's question |
| ai_response | TEXT | AI-generated answer |
| timestamp | DATETIME | Query submission time |

---

## 🎨 Customization Tips

### Unique Variable Names
Use descriptive, project-specific naming:
```python
# Instead of: data, result, response
# Use: gemini_ai_answer, user_submitted_question, database_query_record
```

### Coding Style
- Follow PEP 8 guidelines
- Add comprehensive comments
- Use meaningful function names
- Implement error handling consistently

---

## 📦 Submission Checklist

- [ ] All files present in project folder
- [ ] `.env` excluded from GitHub
- [ ] `queries.db` generated successfully
- [ ] Application deployed on Render
- [ ] `link_to_my_web_app.txt` contains correct URL
- [ ] GitHub repository is public/accessible
- [ ] 2-page report completed
- [ ] Project folder zipped
- [ ] Submitted via specified method

---

## 🐛 Common Issues & Solutions

### Issue 1: API Key Not Working
**Solution:** Verify key is correctly set in Render environment variables

### Issue 2: Database Not Creating
**Solution:** Ensure write permissions in deployment environment

### Issue 3: Render App Sleeping
**Solution:** Free tier apps sleep after inactivity; first request may be slow

### Issue 4: CORS Errors
**Solution:** Add Flask-CORS if making requests from different domains

---

## 📚 Additional Resources

- [Flask Documentation](https://flask.palletsprojects.com/)
- [Google Gemini API Docs](https://ai.google.dev/docs)
- [Render Deployment Guide](https://render.com/docs)
- [SQLite Tutorial](https://www.sqlitetutorial.net/)

---

## 👨‍💻 Development Notes

### Future Enhancements
- Add user authentication
- Implement query history viewer
- Add export functionality for queries
- Create admin dashboard
- Implement caching for common queries

### Performance Optimization
- Use connection pooling for database
- Implement request caching
- Optimize API call frequency
- Add loading indicators

---

## 📝 Report Guidelines

Your 2-page report should cover:

1. **Introduction**
   - Project purpose and objectives
   - Technologies used

2. **Implementation Details**
   - Backend architecture
   - Frontend design decisions
   - Database structure
   - API integration approach

3. **Challenges & Solutions**
   - Problems encountered
   - How you resolved them

4. **Deployment Process**
   - Steps taken
   - Configuration details

5. **Testing & Results**
   - Test cases
   - Application performance

6. **Conclusion**
   - Learning outcomes
   - Future improvements

---

## 📧 Contact & Support

For questions or issues:
- Check project documentation
- Review error logs in Render dashboard
- Consult course materials
- Reach out to Mr. Dami or course instructor

---

## ✅ Final Notes

- **Unique Code:** Use distinctive variable names and coding patterns
- **Documentation:** Comment your code thoroughly
- **Testing:** Test locally before deploying
- **Backup:** Keep local copies of your work
- **Deadline:** Submit on time via specified method

**Good luck with your project! 🚀**

---
