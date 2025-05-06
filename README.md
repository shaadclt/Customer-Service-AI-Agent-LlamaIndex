# 🧠 Customer Support Agent using LlamaIndex, Groq, and RAG
This project demonstrates how to build an intelligent customer support agent using LlamaIndex, Groq’s LLaMA 3.3 70B, and HuggingFace Embeddings. The agent can answer questions about orders, return policies, delivery dates, and customer support information by combining function-calling tools and a vector-based RAG (Retrieval-Augmented Generation) setup.

# 🚀 Features
- 📦 Order Queries: Get items and delivery date for any order ID

- 🔁 Return Policies: Determine how many days each item can be returned

- 📄 Document-Based RAG: Query customer service documents using vector search

- 🤖 Function Calling Agent: Uses tool-based reasoning with Groq-hosted LLaMA-3.3-70B

- 📚 Embeddings: Powered by BAAI/bge-small-en-v1.5 from HuggingFace

# 📁 Project Structure
```bash
├── Customer Service.pdf            # Vector database content
├── customer_service_ai_agent.ipynb    # Google Colab notebook with implementation
├── README.md                       # Project documentation
└── LICENSE.txt                    # License File
```

# 🛠️ Installation & Requirements
Install the necessary Python packages:

```bash
pip install llama-index
pip install llama-index-llms-groq
pip install llama-index-embeddings-huggingface
pip install nest_asyncio
```

# 🔑 API Setup
This project uses the Groq API for accessing the LLaMA model.

In Google Colab, store the API key using:

```python
from google.colab import userdata
Settings.llm = Groq(model="llama-3.3-70b-versatile", api_key=userdata.get('GROQ_API_KEY'))
```

# 🧰 Tools Implemented
**1. `get_order_items(order_id)`**
Returns the list of items in a given order.

**2. `get_delivery_date(order_id)`**
Returns the delivery date for a given order.

**3. `get_item_return_days(item)`**
Returns the return period (in days) for a given item.

**4. `support_tool`**
A vector-based query tool built on customer service documentation using `SimpleDirectoryReader` and `VectorStoreIndex`.

# ⚙️ Agent Configuration
- Tools are created using `FunctionTool` and `QueryEngineTool`.

- `FunctionCallingAgentWorker` is used to handle tool calls.

- `AgentRunner` orchestrates queries using tools + LLM-based reasoning.

# ⚙️ Agent Design

![agent_design](https://github.com/user-attachments/assets/5beeff0b-6bd5-4301-beef-8340fe6ca147)


# 💬 Example Queries
✅ Return Policy for Order 1001
```python
agent.query("What is the return policy for order number 1001")
```

✅ Delivery Date, Items, and Support Info
```python
agent.query("When is the delivery date and items shipped for order 1003 and how can I contact customer support?")
```

❌ Invalid Order Query
```python
agent.query("What is the return policy for order number 1004")
```

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE.txt) file for details.


👤 Author
Developed by Mohamed Shaad.
If you found this project helpful, feel free to ⭐ star the repo and share your thoughts!

