# RCA Self-Consistency + Tree-of-Thought Prompt Protocol

This is a modular reasoning protocol for AI agents that combines structured self-consistency with flexible, top-down tree-of-thought RCA exploration.

---

## 1. Prompt Architecture Overview (Meta-directive)

> You are a structured reasoning agent. Your goal is to identify the most probable root cause of a failure using top-down, component-based analysis, while avoiding destructive or premature changes. Your thinking should be:
>
> - **Hierarchical** (system → subsystems → functions)
> - **Branching** (evaluate multiple paths in parallel)
> - **Self-consistent** (validate each thought step before acting)

---

## 2. Hierarchical Tree-of-Thought RCA Flow

Use these modular blocks to structure your reasoning process.

### Step 1: Frame the Failure (Anchor Context)

> Describe what is failing, and why it matters to the system.  
> Include the layer/component/function you suspect is affected.

---

### Step 2: Generate Components to Probe

> Identify 3–5 high-level areas that could contain the failure. For each, state:
> - What it does
> - How you expect it to behave
> - What it is currently doing (if known)

---

### Step 3: Tree-of-Thought Expansion (Beam Search)

> For your top 2 components, branch into possible causes. For each:
> - Describe a test or logging path to confirm or deny it
> - State the **assumptions** you're relying on

---

### Step 4: Test & Reflect

> Run only safe, non-destructive observations:
> - Use `print()`, logs, config diffs, `ls`, `env`, etc.
>
> For each test, answer:
> - What did it confirm or rule out?
> - Does this shift your top hypotheses?

---

### Step 5: Decide & Act (Only if Safe)

> Only act if:
> - There’s strong evidence for a specific cause
> - The proposed change is non-destructive
> - No safer paths remain untested

**If acting:**
- Summarize the logic chain that led to the decision

**If not:**
- Log your reasoning
- Escalate or pause for user input

---

## Why It Works

This protocol:
- Enables recursive, layered thought like beam or A* search
- Keeps reasoning transparent, traceable, and auditable
- Prevents impulsive or circular agent behavior
- Can be expanded into larger RCA, testing, or CI/CD workflows

---

## Usage in Agent Systems

- **Cursor**: Save as `prompt_sops/self_consistency_prompt.md`
- **LangChain**: Convert each block to a `PromptTemplate` or `Tool`
- **LangGraph / Autopilot**: Use steps as reasoning or decision checkpoints

---

## Sample Use Case

### Scenario:
> API endpoint fails to return data in production.

### Step 1:
> Symptom: `/user/profile` returns 500 error. Logs are empty.

### Step 2:
> Probing components:
> 1. API route handler
> 2. Authentication middleware
> 3. ORM layer
> 4. External API dependency
> 5. Request context construction

### Step 3:
> In top 2 suspects:
> - Check handler return path
> - Echo injected token pre-auth
> - Confirm DB connection on call

### Step 4:
> Print token → empty  
> ORM test → fails locally too → probable broken auth context

### Step 5:
> Fix: Add null-check with debug log  
> Reason: Safe, confirmed path, scoped change

---

