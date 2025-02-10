# FAQ Chatbot with OpenAI and FastApi
This project implements an FAQ chatbot that leverages OpenAI's GPT-3.5 API to provide conversational answers to both frequently asked questions (FAQs) and general user queries. The chatbot also stores conversation history in an SQLite database to improve contextual responses.

## Features:
FAQ-based responses: Answer questions from a predefined set of FAQs.
General conversation: Handles general conversational inputs like greetings and introductions.
Database support: Stores conversation history in an SQLite database.
OpenAI integration: Uses OpenAI GPT-3.5 for fallback responses with conversation context.
Dockerized application: The project is dockerized for easy deployment.

## Tech Stack:
 - Backend: FastAPI, OpenAI API
 - Database: SQLite (SQLAlchemy ORM)
 - Containerization: Docker
 - Frontend: (Can be added, e.g., Streamlit, if you want to provide a UI for users)

## Requirements:
- Python 3.7+
- Docker
- Docker Compose (if needed)

## Setup Instructions:
1. Clone the repository:
git clone https://github.com/your-username/faq-chatbot.git

2. Install dependencies:

 - Option 1: Using Docker (Recommended)
 
   - This project is dockerized for easy deployment.
   
   - Build the Docker container:
   docker-compose build
   
   - Start the application:
   docker-compose up
 
 - Option 2: Local Development (Without Docker)
 
   - Create a virtual environment:
   python3 -m venv venv
   
   - Activate the virtual environment:
   
    - On Windows: venv\Scripts\activate
    - On macOS/Linux: source venv/bin/activate
   
   - Install dependencies:
   pip install -r requirements.txt
   
   - Set up your .env file (create one in the root directory):
   OPENAI_API_KEY=your-openai-api-key
   
   - Start the application:
   uvicorn main:app --reload

## 3. Application URL:
Once the server is up, the API will be running at http://127.0.0.1:8000

You can interact with the API by sending POST requests to the /ask endpoint with a query as the payload.

Example request:

json
{
  "query": "What is your name?"
}
Response:
{
  "answer": "I am an FAQ chatbot here to assist you with common questions."
}

## Database:
The project uses SQLite to store conversation history. The table conversation_history contains the following columns:

 - id: Auto-incrementing primary key.
 - query: The user's input.
 - response: The chatbot's response.
 - role: The role of the speaker (either "user" or "assistant").

To initialize the database, the project automatically creates the necessary tables upon startup. You can inspect the database using SQLite tools or SQLite browser.

## FAQ:
Q1: How do I interact with the chatbot?

You can send POST requests to the /ask endpoint of the API. The request body should contain a query key with the user's question or statement.

Q2: Does the chatbot remember previous conversations?

Yes, the chatbot saves the conversation history in an SQLite database. This history is used to provide better context in the chatbot’s responses.

Q3: Can I add more FAQs?

Yes! You can easily add more FAQ data by editing the faqs.json file in the root directory. The chatbot will automatically load this data at startup.

Q4: How can I deploy this chatbot to production?

Since the application is dockerized, you can deploy it on any platform that supports Docker. You can use platforms like Heroku, AWS, or DigitalOcean to host the container.

Q5: How does the chatbot handle general conversation?

The chatbot is designed to understand and respond to general statements like greetings or personal introductions. These responses are defined in the general_responses dictionary in the backend.
