🚀 Agentic AI Lab – LangChain & CrewAI

End-to-end implementation of AI Agents and Multi-Agent Systems using LangChain and CrewAI, built in Google Colab with real-world tools, web search, memory, and task orchestration.
This repository demonstrates how to design, build, debug, and deploy agentic AI systems capable of:
Autonomous reasoning
Tool usage (search, files, APIs)
Multi-agent collaboration
Task decomposition and execution

🧠 What This Project Demonstrates

✅ Single AI Agents using LangChain
✅ Multi-Agent Collaboration using CrewAI
✅ Real-time Web Search (DuckDuckGo)
✅ Agent Roles: Researcher, Analyst, Writer
✅ Tool Calling, Memory, and Chains
✅ Error handling & debugging in Colab
✅ Production-ready project structure

🏗️ Architecture Overview
User Query
   ↓
Task Decomposition
   ↓
LangChain Agent / CrewAI Agents
   ↓
Tool Invocation (Search, Files)
   ↓
Agent Reasoning & Memory
   ↓
Final Structured Output

🧩 Tech Stack
Category	Tools
LLM Orchestration	LangChain
Multi-Agent Framework	CrewAI
Search Tool	DuckDuckGo
LLM Provider	OpenAI
Environment	Google Colab
Programming	Python
Agent Design	ReAct / Tool-Calling
Version Control	Git & GitHub

📁 Project Structure
agentic-ai-lab-langchain-crewai/
│
├── notebooks/
│   ├── 01_langchain_single_agent.ipynb
│   ├── 02_tools_and_memory.ipynb
│   ├── 03_crewai_multi_agent.ipynb
│
├── agents/
│   ├── researcher.py
│   ├── analyst.py
│   ├── writer.py
│
├── tools/
│   ├── search_tool.py
│   ├── file_reader.py
│
├── utils/
│   ├── llm_config.py
│   ├── helpers.py
│
├── requirements.txt
├── .env.example
└── README.md

⚙️ Setup Instructions (Google Colab)
1️⃣ Install Dependencies
!pip install -U langchain langchain-openai crewai duckduckgo-search python-dotenv

2️⃣ Set Environment Variables
import os
os.environ["OPENAI_API_KEY"] = "your_api_key_here"

3️⃣ Verify Installation
from langchain_openai import ChatOpenAI
llm = ChatOpenAI(model="gpt-4o-mini")
llm.invoke("Hello Agentic AI")

🤖 LangChain: Single AI Agent Example
from langchain.agents import initialize_agent, AgentType
from langchain.tools import Tool
from langchain_openai import ChatOpenAI
from duckduckgo_search import DDGS

def search_tool(query):
    with DDGS() as ddgs:
        return list(ddgs.text(query, max_results=3))

tools = [
    Tool(
        name="Web Search",
        func=search_tool,
        description="Search the web for information"
    )
]

llm = ChatOpenAI(model="gpt-4o-mini")

agent = initialize_agent(
    tools=tools,
    llm=llm,
    agent=AgentType.ZERO_SHOT_REACT_DESCRIPTION,
    verbose=True
)

agent.run("Latest trends in Agentic AI")

👥 CrewAI: Multi-Agent System Example
Agent Roles
Agent	Responsibility
Researcher	Gathers accurate information
Analyst	Synthesizes & reasons
Writer	Produces structured output
CrewAI Code
from crewai import Agent, Task, Crew

researcher = Agent(
    role="AI Researcher",
    goal="Find accurate and recent information",
    backstory="Expert in AI research",
    verbose=True
)

analyst = Agent(
    role="AI Analyst",
    goal="Analyze and summarize findings",
    backstory="Expert in reasoning and synthesis",
    verbose=True
)

writer = Agent(
    role="AI Writer",
    goal="Create a clean final report",
    backstory="Expert technical writer",
    verbose=True
)

task = Task(
    description="Research and summarize Agentic AI use cases",
    expected_output="Structured report with examples",
    agent=researcher
)

crew = Crew(
    agents=[researcher, analyst, writer],
    tasks=[task],
    verbose=True
)

result = crew.kickoff()
print(result)


📊 Output Example
Title: Agentic AI Use Cases

1. Autonomous Research Assistants
2. Multi-Agent Business Analysis
3. AI-Driven Market Intelligence
4. Automated Content Pipelines

🧪 Debugging & Error Handling

✔ Version mismatches resolved
✔ Tool import errors handled
✔ LangChain deprecation fixes
✔ CrewAI agent wiring validated
✔ Colab-safe dependency installs

🎯 Skills Demonstrated
Agentic AI Design Patterns
Multi-Agent Orchestration
LangChain Tool & Chain Building
CrewAI Task Coordination
Prompt Engineering
LLM Debugging
Real-World AI System Design
Production-grade Code Structuring

📌 Use Cases
Autonomous Research Agents
AI Business Analysts
Knowledge Discovery Systems
AI-powered Assistants
Enterprise Decision Support

🛣️ Future Enhancements
Vector DB Memory (FAISS / Chroma)
Streaming Agent Responses
Async Multi-Crew Execution
API Deployment (FastAPI)
UI Integration (Streamlit)

👨‍💻 Author
Venkatasurya Abburi
AI / ML Engineer | Agentic AI Enthusiast
🔗 GitHub: Add your profile link
🔗 LinkedIn: Add your profile link

⭐ If You Found This Useful

Give this repo a ⭐ and feel free to fork or contribute!
