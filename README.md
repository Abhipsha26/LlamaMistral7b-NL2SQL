# LlamaMistral7b-NL2SQL
AI chatbot that converts natural language to SQL using Llama Mistral 7B. Connects to a MariaDB database via MCP server with FastAPI-based streaming, session memory, and ngrok tunneling. Built and run on Google Colab.


1. Abstract
This project presents an AI-powered chatbot interface for database interaction using the Mistral 7B Llama model. The system is capable of translating natural language queries into SQL and executing them against a MariaDB database via a locally hosted MCP (MariaDB Chatbot Platform) server. Implemented in a Google Colab environment and connected through ngrok, the system offers contextual memory and streaming outputs via a FastAPI interface. Mistral 7B was chosen over OmniSQL-7B due to its significantly faster inference time on Colab while still maintaining high SQL generation accuracy.


2. Introduction
Translating natural language into SQL (NL2SQL) is an emerging use case in the intersection of natural language processing and structured data management. This project aims to make database interactions intuitive for non-technical users by deploying a large language model that understands user intent and generates SQL queries accordingly. The integration of Mistral 7B, an optimized transformer-based LLM, with an MCP server and a Google Colab frontend provides a real-time, streaming chatbot experience for database querying.


3. System Overview
The system components include:
•	MariaDB Database: Stores structured data in tables like shipment_view.
•	Mistral 7B (Llama): The LLM used for translating user questions into SQL queries.
•	MCP Server: Acts as the intermediary between LLM inference and the database.
•	Ngrok: Used to expose the locally hosted MCP server to the Colab client.
•	Google Colab Notebook: Frontend client with FastAPI server and chat interface.


4. System Architecture
<img width="940" height="1234" alt="image" src="https://github.com/user-attachments/assets/e4d9c78f-7e3e-476c-9145-fe90685ca0b3" />

 
5. Methodology
5.1 Database Schema
The shipment_view table includes:
•	product_id, product_code, product_name, product_type, product_site, year, qtr, month, plan, actual
5.2 Model Integration
Mistral 7B is run using the ctransformers library on Google Colab. Prompts are formatted with schema awareness to guide SQL generation.
5.3 Backend MCP Server
A locally hosted MCP server handles requests to the LLM and forwards valid SQL queries to MariaDB.
5.4 Ngrok Tunneling
Ngrok is used to route requests from Colab to the MCP server hosted on a local machine via public URL.
5.5 Streaming Interface
A FastAPI server on Colab serves streaming responses to the user in real time, with session memory maintained using in-notebook logic.

6. Implementation
•	Language Model: Mistral 7B (Llama variant), integrated via ctransformers
•	SQL Engine: MariaDB
•	API Layer: FastAPI with streaming generator endpoints
•	Frontend: Google Colab notebook
•	Database Connector:
    conn = mysql.connector.connect(
    host="0.tcp.in.ngrok.io",
    port=12615,
    user="root",
    password="password",
    database="office" )
7  Features
•	Natural Language Interface
•	Contextual Memory for multi-turn conversations
•	 Real-Time Streaming Output
•	 Modular Architecture using ngrok, FastAPI, and MCP
•	 Schema-Aware Query Generation using guided prompts


8. Sample Output
 <img width="1011" height="336" alt="image" src="https://github.com/user-attachments/assets/3a145679-686b-41a6-ae2f-4c1cbc752be2" />



9. Challenges Faced
•	OmniSQL 7B took ~2 hours for inference on Colab, making it impractical
•	LLMs required precise prompt engineering to avoid invalid SQL
•	Maintaining memory in FastAPI streaming required custom session logic
•	Ensuring secure access across Colab and MCP without exposing credentials



10. Future Scope
•	Replace Mistral 7B with other good llms like OmniSQL -7b if system is supported by GPU 
•	Add table summarization and natural language explanations of SQL outputs
•	Deploy web-based UI using React 
•	Support JOINs and subqueries in multi-table databases


11. Conclusion
This project delivers a fast, schema-aware AI chatbot capable of translating natural language into SQL and retrieving results in real-time. Mistral 7B offers a practical trade-off between performance and accuracy in the Colab environment. With session memory and streaming capabilities, the project showcases how GenAI can improve data accessibility for non-technical users.


12. References
.	“Mistral 7B LLM,” https://mistral.ai
.	MariaDB Documentation – https://mariadb.com/kb/en/documentation/
.	FastAPI – https://fastapi.tiangolo.com
.	Ngrok Documentation – https://ngrok.com/docs
.	cTransformers GitHub – https://github.com/marella/ctransformers
.	OpenAI GPT Models – https://platform.openai.com/docs


<img width="1292" height="684" alt="Screenshot 2025-07-31 114913" src="https://github.com/user-attachments/assets/23e695c7-763d-47ae-a463-34e5cbd3fc7e" />
<img width="1285" height="423" alt="Screenshot 2025-07-31 114839" src="https://github.com/user-attachments/assets/04b9b1e9-ad72-470e-bd47-40201e2f34d9" />
<img width="1348" height="860" alt="Screenshot 2025-07-31 114806" src="https://github.com/user-attachments/assets/d8ab9dac-f339-4790-8436-2b0d3ef3b85b" />
<img width="1587" height="903" alt="Screenshot 2025-07-31 114743" src="https://github.com/user-attachments/assets/8b999810-e542-4ef4-b838-5c437de919af" />
<img width="1001" height="262" alt="Screenshot 2025-07-31 114749" src="https://github.com/user-attachments/assets/1fcbe9c2-3a4b-4ce6-a359-1c44fdbb0aaf" />
<img width="1790" height="421" alt="Screenshot 2025-07-25 123243" src="https://github.com/user-attachments/assets/8e48de34-8533-44df-beb9-cb6bd38a6edd" />
