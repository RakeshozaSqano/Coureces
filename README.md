# # 📘 Course API Service

The Course API Service automatically creates:

- ✅ **Courses** (with modules and lessons)
- ❓ **Quizzes** (multiple-choice questions)
- 💻 **Coding Questions** (for technical subjects)

This service uses **FastAPI**, **MongoDB**, and **OpenAI** to generate learning content automatically.

---

## 🔧 Tech Stack

| Component     | Technology             |
|---------------|-------------------------|
| Backend       | FastAPI (Python)        |
| Database      | MongoDB                 |
| AI Generation | OpenAI (GPT-3.5 / GPT-4)|
| Orchestration | LangChain               |

---

## 🚀 Getting Started

1. **Clone the project**  
```bash
git clone https://github.com/your-org/course-api.git
cd course-api
```

2. **Set up environment variables**  
```bash
cp .env.example .env
# Edit the file and set OPENAI_API_KEY, MONGODB_URI, etc.
```

3. **Create and activate virtual environment**
```bash
python -m venv .venv
source .venv/bin/activate
```

4. **Install dependencies**
```bash
pip install -r requirements.txt
```

5. **Run the app**
```bash
uvicorn app.main:app --reload
# Visit: http://localhost:8000/docs
```

---

## 📚 Features Overview

### ✅ Course Generation
- Generates full course structure: course → modules → lessons
- Uses OpenAI to create educational content
- Saved into MongoDB

### ❓ Quiz Generation
- Creates MCQs for modules or entire courses
- Each question includes options, answers, and explanations

### 💻 Coding Questions
- For technical courses only
- Supports Python, JS, Java, SQL, C++, etc.
- Includes problem, starter code, solution, test cases

---

## 🗃️ Database Collections

| Collection | Description                        |
|------------|------------------------------------|
| courses    | Course metadata                    |
| modules    | Modules linked to courses          |
| lessons    | Lessons linked to modules          |
| quizzes    | Quiz questions + coding exercises  |

---

## 🌐 API Endpoints (Examples)

### Courses
```http
POST /courses/generate
GET /courses
GET /courses/{course_id}
```

### Quizzes
```http
POST /quizzes/generate
POST /quizzes/generate-all/{course_id}
POST /quizzes/auto-generate
GET /quizzes/by-course/{course_id}
```

### Coding Questions
```http
POST /quizzes/courses/{course_id}/quizzes/{quiz_id}/coding-questions
POST /quizzes/courses/{course_id}/coding-questions
```

---

## 🔄 Auto-Generate Quizzes & Coding Questions

```http
POST /quizzes/auto-generate
```

This will:
- Find new courses without quizzes
- Generate quizzes and coding questions (if technical)
- Return a summary like:

```json
{
  "courses_analyzed": 10,
  "quizzes_generated": 8,
  "courses_skipped": 2,
  "coding_questions_added": 4
}
```

---

## 📌 Best Practices

- Generate quizzes after course content is ready
- Mark technical courses for coding question generation
- Use `/auto-generate` endpoint regularly
- Review AI content before publishing

---

## 📞 Support

If you need help or want to contribute, feel free to open an issue or contact the dev team.
