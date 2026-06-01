
---

# FAQ Chatbot using n8n + Groq LLM

This is a simple FAQ chatbot that uses [n8n](https://n8n.io/) for automation and a Groq-hosted LLM to respond to user questions. The chatbot interface is built with HTML and interacts with a webhook flow deployed via n8n.

##  Features

* Clean, modern chatbot interface
* User input sent to an n8n webhook
* n8n workflow forwards the question to a language model (via Groq)
* Scrapes and refers to a specific FAQ page for answers
* Provides concise, bot-style responses
* Hosted completely via n8n and static frontend

## 📂 Project Structure

```
📁 project-root
├── index.html          # Frontend chatbot UI
├── README.md           # This file
└── n8n-workflow.json   # Exported workflow from n8n
```

## 🧠 How It Works

1. **Frontend (HTML page)**
   A user types a question and clicks "Ask". The question is sent to a webhook hosted on n8n.

2. **n8n Workflow**
   The workflow consists of the following nodes:

   * **Webhook Node**: Accepts incoming POST requests with user questions.
   * **Set Node**: Extracts the question from the body and assigns it.
   * **LLM Chain Node**: Forms the prompt using the question and sends it to the Groq LLM.
   * **Groq Chat Model**: Calls a Groq-hosted language model.
   * **Respond to Webhook Node**: Returns the LLM's response to the frontend.

3. **Web Scraping via Prompting**
   The prompt instructs the model to refer to a specific FAQ page and answer only if the information is available on that page.

## 🖼️ Screenshot

> ![image](https://github.com/user-attachments/assets/42439c87-e1bc-468f-8d23-22c81b0e3791)


##  Setup Instructions

### 1. Clone the Repo

```bash
git clone https://github.com/your-username/faq-chatbot.git
cd faq-chatbot
```

### 2. Deploy the HTML

You can open the `index.html` file directly or host it using GitHub Pages, Netlify, or any static host.

### 3. Setup the n8n Workflow

* Import the `n8n-workflow.json` file into your n8n instance.
* Make sure the webhook URL in `index.html` matches your n8n public webhook URL.
* Add your Groq API credentials in n8n.
* Activate the workflow.

## 🧪 Example Questions

* "What are the office hours?"
* "How can I register for the next semester?"
* "Where can I find the contact information?"

## ✅ To Do / Improvements

* Add fallback if LLM doesn’t know the answer
* Add chat history / memory
* Deploy frontend with a backend server for security
* Handle multiple languages

## 📄 License

This project is licensed under the MIT License.

---

