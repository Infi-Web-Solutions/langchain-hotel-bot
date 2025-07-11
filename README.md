# 🏨 LangChain Hotel Inventory Chatbot

**Revolutionize hotel renovations and inventory management with AI-powered conversations.**  
This project brings together the power of LangChain, OpenAI, and Django to create a smart, interactive assistant for hotel operations—making complex data accessible to everyone, instantly.

---

## 🚀 Why You'll Love This Project

- **Ask Anything, Get Instant Answers:**  
  No more digging through spreadsheets or dashboards. Just ask questions like “Show me all rooms on floor 2” or “How many of item P123 are in the hotel warehouse?” and get real, actionable answers.

- **AI That Understands Your Data:**  
  The bot writes and executes safe, context-aware SQL queries using your actual hotel database schema. It’s like having a data analyst on call 24/7.

- **See the Bot Think:**  
  Watch the reasoning process unfold in real time, with step-by-step streaming of the bot’s thoughts and final answers.

- **Voice-Enabled:**  
  Speak your queries and hear the answers—perfect for busy hotel staff on the move.

- **Modern, Beautiful UI:**  
  Enjoy a sleek chat interface with markdown, tables, and real-time updates.

---

## 🏗️ Project Structure

```
chatbot/
  ├── chatbot_core.py           # Main agent logic, streaming, session handling
  ├── custom_prompt_template.py # LLM prompt with schema and instructions
  ├── database_executor.py      # Safe SQL execution and formatting
  ├── sql_query_generator.py    # Extracts SQL and explanations from LLM output
  ├── utils.py                  # Session, memory, and chat DB helpers
frontend/
  └── chatbot.html              # Modern chat UI (voice, streaming, markdown)
requirements.txt                # All dependencies (Python, Django, LangChain, etc.)
```

---

## ⚡ Quick Demo

> **“Show me all rooms on floor 2.”**  
> **“How many of item P123 are in the hotel warehouse?”**  
> **“What’s in container Container_1?”**  
> **“List all pending installations for floor 5.”**

The bot instantly generates the right SQL, queries your database, and presents the answer in a friendly, readable format.

---

## 🛠️ Installation & Setup

### 1. **Clone the Repository**

```bash
git clone https://github.com/yourusername/langchain-hotel-bot.git
cd langchain-hotel-bot
```

### 2. **Set Up Python Environment**

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. **Install Dependencies**

```bash
pip install -r requirements.txt
```

### 4. **Configure Environment Variables**

- Set your OpenAI API key:
  ```bash
  export OPENAI_API_KEY=your-openai-key
  ```
- Configure your Django/PostgreSQL database in your Django `settings.py` (see below).

### 5. **Django Setup**

- Make sure you have a Django project and an app (e.g., `hotel_bot_app`) with the required models (`InvitedUser`, `ChatSession`, `ChatMessage`, `ChatEvaluation`).
- Run migrations:
  ```bash
  python manage.py makemigrations
  python manage.py migrate
  ```

### 6. **Run the Server**

```bash
python manage.py runserver
```

### 7. **Access the Chatbot**

Open your browser to:  
`http://localhost:8000/frontend/chatbot.html`

---

## 🧠 How It Works

1. **User asks a question** (text or voice) in the chat UI.
2. **Session is created** and tracked for context.
3. **LangChain agent** receives the question, plus chat history, and uses a custom prompt with your hotel’s database schema.
4. **LLM generates SQL** and a human-readable explanation.
5. **SQL is safely executed** against your PostgreSQL database (read-only, no dangerous queries).
6. **Results are streamed back** to the frontend, showing the bot’s reasoning and the final answer.
7. **Voice output** reads the answer aloud if the user used voice input.

---

## 🏢 Database Schema

The bot is aware of your hotel’s schema, including tables like:

- `room_data` (room details)
- `install` (installation progress)
- `inventory` (warehouse tracking)
- `shipping`, `inventory_received`, `hotel_warehouse`, etc.

**See `chatbot/custom_prompt_template.py` for the full schema and field descriptions.**

---

## 🖥️ Frontend

- **Modern chat UI** with real-time streaming, markdown, tables, and voice.
- **Session management** and error handling.
- **API endpoints expected:**  
  - `POST /api/session/create/` — creates a new chat session  
  - `POST /api/chat/stream/` — streams the bot’s response

---

## 🔒 Security

- **SQL Safety:**  
  The bot blocks any destructive SQL (no `DELETE`, `DROP`, `INSERT`, etc.).
- **User Authentication:**  
  Integrate with Django’s user system for access control if needed.

---

## 🧩 Extending & Customizing

- **Add new tables/fields:**  
  Update the schema in `chatbot/custom_prompt_template.py` and your database/models.
- **Change the LLM model:**  
  Edit the `build_llm` function in `chatbot_core.py`.
- **Customize the UI:**  
  Edit `frontend/chatbot.html` for branding, layout, or new features.

---

## 🧪 Testing

- **Unit tests:**  
  Add tests for your Django models, views, and utility functions.
- **Manual testing:**  
  Try a variety of queries in the chat UI and verify results.

---

## 🤝 Contributing

Pull requests and issues are welcome!  
- Fork the repo, create a feature branch, and submit a PR.
- For major changes, open an issue first to discuss your ideas.

---

## 💡 Inspiration

This project was built to solve real-world pain points in hotel renovation and inventory management—making data accessible, actionable, and easy for everyone on the team.

---

## 📞 Support

For questions, feature requests, or help, open an issue or contact the maintainer.

---

**Transform your hotel operations—one conversation at a time!**
