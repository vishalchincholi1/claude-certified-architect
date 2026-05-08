# Claude Certified Architect - Study Repository

A comprehensive repository of production-grade Claude applications and implementations aligned with the **Claude Certified Architect – Foundations** exam domains.

## 📚 Exam Domains Overview

This repository is organized around the five core domains tested in the Claude Certified Architect exam:

### Domain 1: Agentic Architecture & Orchestration (~25%)
Design and implement agentic systems using Claude's Agent SDK. Covers:
- Agentic loops
- Multi-agent orchestration
- Hooks and workflows
- Session management
- Task decomposition patterns
- Production-grade AI applications

**Code Examples:**
- [`agent.py`](agent.py) - Complete agentic loop implementation with tool orchestration

### Domain 2: Tool Design & MCP Integration (~20%)
Design effective tools and integrate with Model Context Protocol (MCP) servers. Covers:
- Tool description best practices
- Structured error responses
- Tool distribution patterns
- MCP configuration
- Claude's built-in tools

**Code Examples:**
- [`agent.py`](agent.py) - Tool schema design and execution patterns
- Error handling categories (transient, permission, validation, internal)

### Domain 3: Claude Code Configuration & Workflows (~20%)
Configure Claude Code for development workflows. Covers:
- CLAUDE.md hierarchy
- Custom commands and skills
- Plan mode and iterative refinement
- CI/CD integration
- Batch processing

**Code Examples:**
- API validation patterns in [`api_check.py`](api_check.py)

### Domain 4: Prompt Engineering & Structured Output (~20%)
Master prompt engineering techniques for production systems. Covers:
- Explicit criteria
- Few-shot prompting
- Tool_use for structured output
- JSON schema design
- Validation-retry loops
- Multi-pass review strategies

### Domain 5: Context Management & Reliability (~15%)
Manage context effectively in production systems. Covers:
- Progressive summarization risks
- Context positioning
- Escalation patterns
- Error propagation
- Context degradation
- Human review and information provenance

---

## 📁 Repository Structure

```
claude-certified-architect/
├── README.md                           # This file
├── agent.py                            # Domain 1 & 2: Agentic loop + tool orchestration
├── api_check.py                        # Domain 3 & 5: Configuration & environment validation
├── scenario-1-customer-support.md      # Scenario 1: Customer Support Agent (Domains 1, 2, 5)
├── domain-1/                           # Agentic Architecture examples
│   └── [future additions]
├── domain-2/                           # Tool Design & MCP examples
│   └── [future additions]
├── domain-3/                           # Claude Code Configuration examples
│   └── [future additions]
├── domain-4/                           # Prompt Engineering examples
│   └── [future additions]
└── domain-5/                           # Context Management examples
    └── [future additions]
```

## 🎯 Exam Scenarios

### Scenario 1: Customer Support Resolution Agent
**Primary Domains:** Agentic Architecture & Orchestration, Tool Design & MCP Integration, Context Management & Reliability

A complete customer support agent handling returns, billing disputes, and account issues with 80%+ first-contact resolution.

**Key Features:**
- Agentic loop with tool orchestration
- Structured error handling and escalation
- Context management patterns
- Anti-pattern avoidance strategies

**Documentation:** [`scenario-1-customer-support.md`](scenario-1-customer-support.md)

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Anthropic API key

### Installation

```bash
# Clone the repository
git clone https://github.com/vishalchincholi1/claude-certified-architect
cd claude-certified-architect

# Install dependencies
pip install anthropic
```

### Set Your API Key

**Windows PowerShell:**
```powershell
setx ANTHROPIC_API_KEY "your_key_here"
# Restart PowerShell after running setx

# Verify
$env:ANTHROPIC_API_KEY
```

**macOS/Linux:**
```bash
export ANTHROPIC_API_KEY="your_key_here"
```

### Run Examples

**Agentic Loop Example:**
```bash
python agent.py
```

**API Validation:**
```bash
python api_check.py
```

---

## 💡 Key Concepts Covered

### Agentic Loop Pattern
The agent continuously loops until completion:
1. Call Claude API with user message + available tools
2. Check `stop_reason`:
   - `"end_turn"` → return final answer
   - `"tool_use"` → execute tools, append results, continue
3. Structured error handling for resilience

### Tool Design Best Practices
- Clear, actionable descriptions
- Well-defined JSON schemas
- Structured error categories
- Graceful failure handling

### Error Categories
- **Transient** — Infrastructure hiccup; retryable
- **Permission** — Access denied; escalate
- **Validation** — Bad params; self-correct
- **Internal** — Unexpected; surface to coordinator

---

## 📖 Code Examples

### Basic Agent Loop
```python
import anthropic

client = anthropic.Anthropic()

def run_agent(user_message: str) -> str:
    messages = [{"role": "user", "content": user_message}]
    
    while True:
        response = client.messages.create(
            model="claude-haiku-4-5",
            max_tokens=4096,
            tools=tools,
            messages=messages
        )
        
        if response.stop_reason == "end_turn":
            return response.content[0].text
        
        if response.stop_reason == "tool_use":
            messages.append({"role": "assistant", "content": response.content})
            # Execute tools and append results...
```

### Tool Definition
```python
tools = [
    {
        "name": "lookup_order",
        "description": "Look up an order by ID",
        "input_schema": {
            "type": "object",
            "properties": {
                "order_id": {"type": "string", "description": "Order ID"}
            },
            "required": ["order_id"]
        }
    }
]
```

---

## 🎯 Exam Preparation

Use this repository to:
- Study production patterns for each domain
- Practice implementing agentic systems
- Understand tool design best practices
- Explore context management strategies
- Build confidence before the exam

---

## 📌 Contributing

Add domain-specific implementations:
1. Create a folder for the domain (e.g., `domain-1/`)
2. Add well-documented code examples
3. Update this README with new examples
4. Commit and push to GitHub

---

## 🏆 Why Get Claude Certified?

✅ Validate expertise in building production-grade Claude applications  
✅ Stand out to employers seeking Claude Certified Architects  
✅ Demonstrate mastery of agentic architecture, tool design, and prompt engineering  
✅ Join the first wave of Anthropic-certified AI professionals  
✅ Credential recognized across the Claude partner ecosystem  
✅ **Free to attempt** — no cost barrier to proving your skills  

---

## 📚 References

- [Anthropic Claude Documentation](https://docs.anthropic.com)
- [Claude API Reference](https://docs.anthropic.com/en/api)
- [Agent SDK Documentation](https://docs.anthropic.com/en/docs/agents)

---

## 📄 License

This repository is for educational purposes. See LICENSE for details.

---

**Last Updated:** May 8, 2026  
**Prepared for:** Claude Certified Architect – Foundations Exam
