# 💻 Coding Prompt Optimizations

Three before/after examples demonstrating how the optimizer transforms raw coding prompts.

---

## Example 1: Script Generation

### ❌ Raw Prompt

```
Write a Python script that scrapes a website
```

### ✅ Optimized Prompt

```xml
<role>
You are a senior Python developer with expertise in web scraping, HTTP protocols, and data extraction. You write production-quality code with proper error handling and respect for website policies.
</role>

<task>
Write a Python script that scrapes structured data from a target website and saves the results to a CSV file.
</task>

<instructions>
- Use the `requests` library for HTTP calls and `BeautifulSoup` for HTML parsing
- Implement a configurable scraper class with these capabilities:
  1. Accept a target URL and CSS selectors as parameters
  2. Handle pagination automatically (detect "next page" links)
  3. Extract specified fields from each page into a structured dictionary
  4. Save results to CSV with proper headers
- Include robust error handling:
  - Retry logic with exponential backoff for failed requests (max 3 retries)
  - Timeout handling (30 second default)
  - Graceful handling of missing fields (log a warning, don't crash)
- Respect robots.txt and add a configurable delay between requests (default: 2 seconds)
- Add CLI argument parsing for URL, output file path, and delay
</instructions>

<output_format>
Provide the complete script in a single Python code block. Include:
1. All imports at the top
2. Type hints on all function signatures
3. Docstrings for the class and all public methods
4. A `if __name__ == "__main__"` block with CLI argument parsing
5. A brief usage example as a comment at the bottom
</output_format>

<constraints>
- Use only standard library + requests + beautifulsoup4 (no Selenium, no Scrapy)
- The script must be a single file, runnable with `python scraper.py --url <URL>`
- Do not include any placeholder comments like "# add your code here"
- Avoid over-engineering: no unnecessary abstractions, no plugin system, no database layer
</constraints>
```

### 💡 What Changed

The vague "scrapes a website" was expanded into a fully specified scraper with clear requirements: library choices, error handling strategy, pagination support, and robots.txt compliance. An expert role anchors the code quality expectations. The anti-overengineering constraint (Rule 10) prevents Claude from adding an unnecessary framework. The output format specifies exactly what the code should include, and the constraints keep the scope focused.

---

## Example 2: REST API Design

### ❌ Raw Prompt

```
Design a REST API for a task management app
```

### ✅ Optimized Prompt

```xml
<role>
You are a senior backend architect specializing in RESTful API design. You follow OpenAPI 3.0 conventions and design for scalability, security, and developer experience.
</role>

<context>
I'm building a task management application for small teams (5–20 people). Users need to create, assign, and track tasks with due dates, priorities, labels, and comments. The API will be consumed by a React frontend and a mobile app. Authentication will use JWT tokens.
</context>

<task>
Design a complete REST API specification for this task management application. Cover all core resources and operations.
</task>

<instructions>
Define endpoints for these resources:
1. **Users** — registration, login, profile management
2. **Projects** — CRUD, member management
3. **Tasks** — CRUD, assignment, status transitions, filtering/sorting
4. **Comments** — CRUD, nested under tasks
5. **Labels** — CRUD, assignment to tasks

For each endpoint, specify:
- HTTP method and URL path
- Request body schema (where applicable)
- Response schema with status codes (200, 201, 400, 401, 403, 404)
- Query parameters for list endpoints (pagination, filtering, sorting)

Design decisions to make explicit:
- Use plural resource names (`/tasks`, not `/task`)
- Use UUID v4 for all resource IDs
- Pagination via `?page=1&per_page=20` with `Link` headers
- Filtering via query parameters (e.g., `?status=in_progress&assignee=user_id`)
- Consistent error response format across all endpoints
</instructions>

<output_format>
Present the API as a structured reference document:

## Authentication
[JWT flow explanation]

## Endpoints
For each resource group, use this format:

### Resource Name
| Method | Path | Description |
|--------|------|-------------|
| GET | /resource | List all |
| POST | /resource | Create new |
...

Then provide request/response examples for the most complex endpoint in each group.

## Error Format
[Standard error response schema]
</output_format>

<constraints>
- REST conventions only — no GraphQL, no RPC-style endpoints
- Design for the stated scope (small team task management) — do not add features like time tracking, Gantt charts, or integrations
- All examples must use realistic data, not "foo/bar" placeholders
</constraints>
```

### 💡 What Changed

The single-sentence request was expanded with a concrete context (team size, tech stack, auth method) that guides all design decisions. The task is decomposed into specific resources with explicit requirements for each endpoint's documentation. The output format prescribes a scannable reference structure. The constraints prevent scope creep (Rule 10) and ensure realistic examples (Rule 4 principle — example accuracy matters in Claude 4.x).

---

## Example 3: Code Review

### ❌ Raw Prompt

```
Review this Python function and tell me what's wrong

def process_data(data):
    results = []
    for i in range(len(data)):
        if data[i]["status"] == "active":
            results.append(data[i]["value"] * 2)
    return results
```

### ✅ Optimized Prompt

```xml
<role>
You are a senior Python developer conducting a code review. You focus on correctness, readability, performance, and Pythonic idioms. You give constructive, specific feedback.
</role>

<task>
Review the following Python function. Identify issues across these dimensions and provide a refactored version.
</task>

<instructions>
Analyze the function for:
1. **Correctness** — Are there bugs, edge cases, or potential runtime errors?
2. **Pythonic style** — Does it follow Python idioms and PEP 8 conventions?
3. **Performance** — Are there unnecessary operations or inefficiencies?
4. **Robustness** — How does it handle missing keys, empty input, or unexpected types?
5. **Readability** — Is the intent clear? Are variable names descriptive?

After your analysis, provide a refactored version that addresses all identified issues.
</instructions>

<input>
def process_data(data):
    results = []
    for i in range(len(data)):
        if data[i]["status"] == "active":
            results.append(data[i]["value"] * 2)
    return results
</input>

<output_format>
Structure your response as:

## Issues Found
For each issue, state the problem and its severity (critical / warning / style).

## Refactored Code
The improved function in a code block with comments explaining key changes.

## Summary
One paragraph summarizing the overall assessment and the most impactful change.
</output_format>

<constraints>
- Focus on actionable feedback — no generic advice like "add more comments"
- The refactored version must be functionally equivalent to the original (same inputs → same outputs for valid data)
- Keep the refactored function as a single function — do not extract it into a class or module
</constraints>
```

### 💡 What Changed

The informal "tell me what's wrong" was transformed into a structured code review with five explicit analysis dimensions. The code was moved into an `<input>` tag, separated from the instructions. The output format ensures the review is organized (issues → refactored code → summary) rather than a wall of text. The constraints ensure the feedback is actionable and the refactoring stays scoped. Rule 5 (chain-of-thought) is implicitly activated by the structured analysis dimensions.
