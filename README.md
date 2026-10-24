# 🚀 Echelon AI

Echelon AI is a LangGraph-based multi-agent market research and reporting system.

The system is designed to analyze a product or business idea submitted by a user, conduct research, examine trends, perform competitor analysis, evaluate user reviews, generate insights, and deliver the entire process as automated reports.

---

# 🎯 Project Purpose

The purpose of Echelon AI is to:

- Develop ideas coming from the user,
- Collect reliable data from the internet,
- Reduce the risk of hallucination,
- Perform trend analysis,
- Examine competitors,
- Evaluate user reviews,
- Generate insights,
- Produce professional reports at the end of the process,

and to automate all of this with a LangGraph-based multi-agent architecture.

---

# ✨ Key Features

- 🧠 LangGraph-based multi-agent architecture
- 🔍 Tavily-powered research system
- 🛡 Hallucination Guard mechanism
- 📈 Trend analysis
- 🏆 Competitor analysis
- ⭐ User review analysis
- 💡 Insight generation
- 🤖 Prompt enhancement
- 📄 Markdown report generation
- 📑 PDF report generation
- 📂 JSON output support
- 🌐 Streamlit-based user interface

---

# 💼 Use Cases

Echelon AI can be used in the following scenarios:

- Amazon product research
- Evaluating new business ideas
- Competitor analysis
- Trend research
- Market analysis
- Insight generation
- Automated reporting processes
- AI-powered research assistant

---

# ⚙️ Installation

## Cloning the Repository

```bash
git clone <repo_url>

cd Echelon-AI
```

---

## Creating a Virtual Environment

```bash
python -m venv agent_env
```

Activation:

Windows:

```bash
agent_env\Scripts\activate
```

Linux / MacOS:

```bash
source agent_env/bin/activate
```

---

## Installing Dependencies

```bash
pip install -r requirements.txt
```

---

## .env Settings

The project uses environment variables through a `.env` file.

Example:

```env
TAVILY_API_KEY=
GEMINI_API_KEY=
GROQ_API_KEY=
```

Model names are optional. By default, the project uses `llama-3.3-70b-versatile` (Groq) and `gemini-2.5-flash` (Gemini). To use different models, add these to your `.env` file:

```env
GROQ_MODEL=llama-3.3-70b-versatile
GEMINI_MODEL=gemini-2.5-flash
```

## Starting the Application

To run the Streamlit interface:

```bash
streamlit run streamlit_chat.py
```

---

# 📂 Project Structure

```text
Echelon-AI
│
├── agents
│
├── graphs
│
├── states
│
├── utils
│
├── output
│
├── tests
│
├── streamlit_chat.py
│
├── requirements.txt
│
└── README.md
```

---

# 📁 Folder Responsibilities

| Folder | Responsibility |
|---------|--------|
| agents | Contains all specialist agents in the system |
| graphs | Hosts the LangGraph workflow definitions |
| states | Defines the shared state structure |
| utils | Helper services and tools |
| output | Generated output files |
| tests | Test files |
| streamlit_chat.py | User interface |
| requirements.txt | Dependency list |

---

# 🏗 Architecture

The project is built on a LangGraph-based multi-agent architecture.

Each agent focuses on a specific task and shares its results with the other agents through a common state.

This gives the system a structure that is:

- Modular
- Extensible
- Fault tolerant
- Manageable

---

# 🔄 Data Flow

When a user request reaches the system:

1. The prompt is enhanced.
2. Research is performed.
3. The collected data is validated.
4. The hallucination risk is checked.
5. If necessary, an alternative flow is applied.
6. Trend analysis is performed.
7. Competitor analysis is carried out.
8. User reviews are evaluated.
9. Insights are generated.
10. The automation stage runs.
11. The final report is generated.

---

# 🧠 LangGraph Workflow

```text
START
  ↓
prompt
  ↓
research
  ↓
validator
  ↓
(keyword or report)
  ↓
trend
competitor
review
  ↓
insight
  ↓
automation
  ↓
report
  ↓
END
```

The validator node also acts as the Hallucination Guard.

If a risk is detected, the system can use an alternative flow and move directly to the report stage.

---

# 🔗 State Management

The system uses a Shared State approach.

Each agent:

- Receives its input data from the state.
- Writes its processing results into the state.
- Subsequent agents work using these results.

This structure creates a loosely coupled architecture between the agents.

# 🤖 Agents

Echelon AI has a LangGraph-based multi-agent architecture.

Each agent focuses on a specific area of expertise and shares data with the other agents through the common state.

---

# 🧩 Prompt Enhancer Agent

## File

```text
agents/prompt_enhancer.py
```

## Responsibility

To improve the request coming from the user and make it better suited to the research stage.

## Input

- User prompt

## Output

- Refined / improved prompt

## Relationship with Other Agents

```text
User
    ↓
Prompt Enhancer
    ↓
Research Agent
```

---

# 🔍 Research Agent

## File

```text
agents/research_agent.py
```

## Responsibility

To collect data from the internet and prepare research results.

The Tavily service is used during the research process.

## Input

- Improved user prompt

## Output

- Research data
- Sources
- Initial research results

## Relationship with Other Agents

```text
Prompt Enhancer
      ↓
Research Agent
      ↓
Validator Agent
```

---

# 🛡 Validator Agent

## File

```text
agents/validator_agent.py
```

## Responsibility

To validate the collected data and check the hallucination risk.

It acts as the Hallucination Guard within the system.

## Input

- Research Agent outputs

## Output

- Validated research results
- Risk assessment

## Relationship with Other Agents

```text
Research Agent
      ↓
Validator Agent
      ↓
Keyword Agent or Report Agent
```

---

# 🔑 Keyword Agent

## File

```text
agents/keyword_agent.py
```

## Responsibility

To generate keywords from the research results and prepare the structure to be used in later stages.

## Input

- Validated research results

## Output

- Keywords

## Relationship with Other Agents

```text
Validator
    ↓
Keyword Agent
    ↓
Trend Agent
```

---

# 📈 Market Trend Agent

## File

```text
agents/market_trend_agent.py
```

## Responsibility

To perform trend analysis.

## Input

- Keywords
- Research results

## Output

- Trend data
- Market trends

## Relationship with Other Agents

```text
Keyword Agent
      ↓
Market Trend Agent
      ↓
Insight Agent
```

---

# 🏆 Competitor Agent

## File

```text
agents/competitor_agent.py
```

## Responsibility

To perform competitor analysis.

## Input

- Research data

## Output

- Competitor information
- Competitor assessments

## Relationship with Other Agents

```text
Keyword Agent
      ↓
Competitor Agent
      ↓
Insight Agent
```

---

# ⭐ Review Agent

## File

```text
agents/review_agent.py
```

## Responsibility

To perform review and feedback analysis.

## Input

- Research results

## Output

- User review analyses

## Relationship with Other Agents

```text
Keyword Agent
      ↓
Review Agent
      ↓
Insight Agent
```

---

# 💡 Insight Agent

## File

```text
agents/insight_agent.py
```

## Responsibility

To generate insights by combining the results obtained from the trend, competitor, and review analyses.

## Input

- Trend results
- Competitor analyses
- Review analyses

## Output

- Insight data

## Relationship with Other Agents

```text
Trend Agent
Competitor Agent
Review Agent
        ↓
   Insight Agent
        ↓
Automation Agent
```

---

# ⚙ Automation Agent

## File

```text
agents/automation_agent.py
```

## Responsibility

To prepare the results coming from the insight stage for subsequent processing.

## Input

- Insight results

## Output

- Processed results

## Relationship with Other Agents

```text
Insight Agent
      ↓
Automation Agent
      ↓
Report Agent
```

---

# 📄 Report Agent

## File

```text
agents/report_agent.py
```

## Responsibility

To produce the system's final reports.

## Input

- Results from all agents

## Output

- Markdown reports
- PDF reports
- JSON outputs

## Relationship with Other Agents

```text
Automation Agent
      ↓
Report Agent
      ↓
END
```

---

# 🔄 Overall Relationship Between Agents

```text
User
 ↓
Prompt Enhancer
 ↓
Research
 ↓
Validator
 ↓
Keyword
 ↓
 ├── Market Trend
 ├── Competitor
 └── Review
         ↓
      Insight
         ↓
     Automation
         ↓
       Report
         ↓
        END
```

# 🏗 Graph Structure

Echelon AI uses a LangGraph-based workflow architecture.

Graph definition:

```text
graphs/market_graph.py
```

This file defines the nodes, edge connections, and execution order within the system.

---

# 🔗 Node Structure

The nodes in the system:

| Node | Responsibility |
|--------|--------|
| prompt | Improve the user request |
| research | Conduct research |
| validator | Validate the data |
| keyword | Generate keywords |
| trend | Perform trend analysis |
| competitor | Perform competitor analysis |
| review | Analyze user reviews |
| insight | Generate insights |
| automation | Process the results |
| report | Produce the final report |

---

# 🔄 Workflow

The LangGraph flow works as follows:

```text
START
  ↓
prompt
  ↓
research
  ↓
validator
  ↓
keyword
  ↓
 ├──── trend
 ├──── competitor
 └──── review
          ↓
       insight
          ↓
      automation
          ↓
        report
          ↓
         END
```

---

# 🌐 Data Flow

The system operates in the following order:

## 1. Prompt Stage

The user's request is received.

↓

It is improved by the Prompt Enhancer Agent.

↓

It is passed on to the research stage.

---

## 2. Research Stage

The Research Agent:

- Conducts internet research,
- Collects data,
- Saves the results into the state.

↓

It is passed on to the Validator Agent.

---

## 3. Validation Stage

The Validator Agent:

- Reviews the data,
- Assesses the hallucination risk,
- Validates the results.

↓

It passes the results to the Keyword Agent.

---

## 4. Keyword Generation

The Keyword Agent:

Extracts meaningful keywords from the research results.

↓

These keywords are used by three different specialist agents.

---

## 5. Parallel Analysis Stage

### Trend Analysis

Market Trend Agent:

- Examines trends
- Evaluates market tendencies

---

### Competitor Analysis

Competitor Agent:

- Examines competitors
- Evaluates competitors' strengths and weaknesses

---

### Review Analysis

Review Agent:

- Examines user reviews
- Evaluates feedback

---

These three agents work independently.

↓

The results are combined in the Insight Agent.

---

## 6. Insight Generation

The Insight Agent:

Brings together

- The trend results,
- The competitor analyses,
- The review analyses

to produce overall insights.

↓

It is passed on to the Automation Agent.

---

## 7. Automation Layer

The Automation Agent:

Processes the insight results.

↓

Sends them to the Report Agent.

---

## 8. Reporting Layer

The Report Agent:

Using all the results within the system, produces:

- Markdown report
- PDF report
- JSON outputs

---

# 🧠 State Structure

State definition:

```text
states/market_state.py
```

This file defines the common data structure used within LangGraph.

---

# Shared State Approach

The system uses a central Shared State structure.

Each agent:

1. Retrieves the data it needs from the state.
2. Performs its own processing.
3. Saves its results back into the state.
4. Subsequent agents use this data.

This way, state-based data sharing is used between agents instead of direct dependencies.

---

# 🔄 Data Sharing Between Agents

```text
Prompt
 ↓
Research
 ↓
Validator
 ↓
Keyword
 ↓
 ├── Trend
 ├── Competitor
 └── Review
         ↓
      Insight
         ↓
    Automation
         ↓
       Report
```

The data produced at each stage is kept in the state.

---

# 🎯 Advantages of the Shared State Approach

This architecture provides advantages such as:

- Modularity
- Flexibility
- Scalability
- Low coupling
- Easy maintenance
- Ease of adding new agents

---

# 🛡 Hallucination Guard

The Validator Agent also serves as a Hallucination Guard.

The goals are to:

- Detect unreliable data,
- Filter risky results,
- Reduce the generation of false information,
- Improve report quality.

This layer is integrated into the workflow to increase the reliability of the system.

---

# 📌 General Architecture

```text
                     Shared State

                           ▲
                           │

Prompt Agent ──────────────┤
Research Agent ────────────┤
Validator Agent ───────────┤
Keyword Agent ─────────────┤
Trend Agent ───────────────┤
Competitor Agent ──────────┤
Review Agent ──────────────┤
Insight Agent ─────────────┤
Automation Agent ──────────┤
Report Agent ──────────────┘
```

All agents communicate through the common state structure.

# 🛠 Utils

The utils folder contains the helper services and shared components used within the system.

```text
utils
│
├── llm.py
├── scraper.py
└── tavily_client.py
```

---

# 🧠 llm.py

## Responsibility

Manages the LLM (Large Language Model) layer.

This layer allows the language model connections used by the agents to be managed centrally.

## Where It Is Used

- Agents
- LangGraph workflow

## Structure It Provides

- Model access
- Shared LLM configuration
- Centralized model management

---

# 🌐 scraper.py

## Responsibility

Contains helper scraping operations used in data collection processes.

## Where It Is Used

- Research processes

## Structure It Provides

- Data fetching operations
- Helper web data collection functions

---

# 🔎 tavily_client.py

## Responsibility

Manages the Tavily API connection.

## Where It Is Used

- Research Agent

## Structure It Provides

- Internet research
- Source collection
- Retrieval of search results

---

# 🖥 Streamlit Interface

Interface file:

```text
streamlit_chat.py
```

This file provides the interaction between the user and the system.

---

# User Flow

```text
User
     ↓
Prompt Input
     ↓
LangGraph Workflow
     ↓
Agents
     ↓
Report Generation
     ↓
Displaying Results
```

---

# Interface Components

The Streamlit interface manages components such as:

- User input area
- Result display area
- Agent outputs
- Report results

---

# Result Screens

The results generated by the system can be viewed through the interface.

Generated outputs:

- Markdown reports
- PDF reports
- JSON files

---

# 📂 Output

The output folder contains the outputs generated by the system.

This folder holds:

## 📄 Markdown Reports

Reports generated by the AI are stored here.

---

## 📑 PDF Outputs

PDF versions of the reports are stored here.

---

## 🗂 JSON Outputs

JSON records of the results coming from the agents are kept here.

---

# 🧪 Tests

Test folder:

```text
tests
│
├── market_graph_test.py
└── test_gemini.py
```

---

# market_graph_test.py

## Module Under Test

LangGraph workflow structure

## Purpose

To verify that the graph structure works as expected.

---

# test_gemini.py

## Module Under Test

Gemini integration

## Purpose

To test the model connection and response generation.

---

# 💻 Technologies Used

## Core Technologies

- Python
- Streamlit
- LangGraph
- Gemini
- Groq
- Tavily

---

# Libraries Used

The project's dependencies are managed through the `requirements.txt` file.

Main technologies used:

| Technology | Purpose |
|------------|-----|
| Python | Core programming language |
| Streamlit | Interface |
| LangGraph | Workflow management |
| LangChain | Agent infrastructure |
| Gemini | LLM support |
| Groq | Alternative LLM support |
| Tavily | Internet research |
| dotenv | Environment variables |
| JSON | Data storage |
| Markdown | Reporting |
| PDF | Final output generation |

---

# 🔮 Future Development

The code structure has a modular architecture suited to improvements such as:

- Adding new agents,
- Extending the workflow,
- Increasing LLM options,
- Improving the reporting system,
- Enhancing research processes.

Note:

The Gemini and Groq clients are kept in the system for future support.

---

# 🤝 Contributing

Contributions are welcome.

To contribute:

1. Fork the repository.
2. Create a new branch.

```bash
git checkout -b feature/new-feature
```

3. Commit your changes.

```bash
git commit -m "Added new feature"
```

4. Push the branch.

```bash
git push origin feature/new-feature
```

5. Create a Pull Request.

---

# 📜 License

This project is being developed as open source.

License information should be specified within the repository.

---

# 🎯 Conclusion

Echelon AI is a modular AI system that, thanks to its LangGraph-based multi-agent architecture, brings research, validation, trend analysis, competitor analysis, review evaluation, insight generation, and reporting processes together under a single workflow.

Thanks to the Shared State structure, data is shared between agents; reliability is increased through the Hallucination Guard mechanism; and results are delivered to the user in Markdown, PDF, and JSON formats.

This structure is designed to be extensible, maintainable, and suitable for adding new agents.
