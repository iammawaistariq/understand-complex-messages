# 🚀 FlowixPro: The AI Project Clarity Engine

**Turn messy client messages into professional, structured project plans in seconds.**

FlowixPro is an AI-powered tool designed for freelancers and agencies who are tired of "scope creep" and vague client requirements. Whether it's a chaotic WhatsApp message, a rambling email, or a half-baked Upwork post, FlowixPro decodes the chaos and gives you instant clarity.

---

## ✨ Key Features
- **🎯 Multi-Mode Analysis**: Choose exactly what you want to extract:
  - **Summary**: Executive-level project goals.
  - **Scope**: Clear "In-Scope" vs. "Out-of-Scope" boundaries.
  - **Risks**: Ruthless audit of technical and financial red flags.
  - **Gaps**: Identification of missing info needed for quotes.
  - **Questions**: Strategic questions to send back to the client.
- **🧠 Multi-Step AI Pipeline**: Uses a chain of "AI Experts" (Architect, Auditor, and PM) for superior accuracy.
- **🛡️ Risk Mitigation**: Doesn't just find risks—it suggests professional mitigation strategies.
- **⚡ FastAPI Service**: Simple `/analyze` endpoint for product integration.


---

## 🏗️ System Architecture
FlowixPro runs as a **FastAPI** service and uses a 3-phase LangChain prompt flow:

```mermaid
graph TD
    A[Client Message] --> B[FastAPI: POST /analyze]
    B --> C[Phase 1: Architect (text)]
    C --> D[Phase 2: Auditor (text)]
    D --> E[Phase 3: Strategist (JSON)]
    E --> F[Validated JSON Output (Pydantic)]

    style B fill:#f9f9f9,stroke:#333,stroke-width:2px
    style C fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    style D fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    style E fill:#e1f5fe,stroke:#01579b,stroke-width:2px
    style F fill:#f1f8e9,stroke:#33691e,stroke-width:2px
```

---

## 🛠️ Technology Stack
- **LLM**: OpenAI `gpt-4o-mini` (default) or Groq-hosted Llama models
- **Orchestration**: LangChain (`ChatOpenAI` + `ChatPromptTemplate`)
- **API**: FastAPI + Uvicorn
- **Data Validation**: Pydantic V2
- **Environment**: Python 3.9+

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/your-username/FlowixPro.git
cd FlowixPro
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Setup Environment Variables
Create a `.env` file in the root directory:
```env
OPENAI_API_KEY=your_api_key_here
# optional (only if using Groq)
GROQ_API_KEY=your_groq_key_here

# defaults shown in Swagger
FLOWIX_PROVIDER=openai
FLOWIX_MODEL=gpt-4o-mini
FLOWIX_TEMPERATURE=0.1
```

### 4. Run the application
```bash
uvicorn main:app --reload
```

### 5. Use the API

- Health: `GET /health`
- Defaults: `GET /defaults`
- Analyze: `POST /analyze`

Example request:

```json
{
  "message": "Need an ecommerce site in 2 weeks with $200 budget"
}
```

---

