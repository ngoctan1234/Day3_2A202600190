# Individual Report: Lab 3 - Chatbot vs ReAct Agent

- **Student Name**: Nguyen Ngoc Tan
- **Student ID**: 2A202600190
- **Date**: 2026-04-06

---

## I. Technical Contribution (15 Points)

_Describe your specific contribution to the codebase._

- **Contribution**: I have contributed to  the group's code. My work focused on creating the ReACt agent for the team.
- **Modules Implemented**: React agnt
- **Code Highlights**: Full code
- **Documentation**: Provided the structure and formatting for the group report.

---

## II. Debugging Case Study (10 Points)

_Analyze a specific failure event you encountered during the lab using the logging system._

- **Problem Description**: While testing the ReAct Agent to find offline Python courses in Cầu Giấy, Hà Nội, the system crashed during Step 4/5 with an error: `Invalid operation: The response.text quick accessor requires the response to contain a valid Part, but none were returned`. The agent initially successfully fetched search results, but the LLM eventually returned an empty response.
- **Log Source**:

```text
⚠️ [CẢNH BÁO LLM]: Model trả về rỗng (finish_reason=1)
❌ Đã xảy ra lỗi hệ thống: Invalid operation: The `response.text` quick accessor requires the response to contain a valid `Part`, but none were returned.
```

- **Diagnosis**: The LLM returned an empty response (`finish_reason=1`), likely due to exceeding context limits or an internal model interruption. The agent's code did not handle the case where `response.text` could be empty, leading to an unhandled exception.
- **Solution**: Added a **check for empty responses** before accessing `response.text`. Implemented a retry mechanism for the LLM call, and ensured fallback to previous observations when the current response is invalid. This prevented the agent from crashing and allowed it to continue reasoning or terminate gracefully.

---

## III. Personal Insights: Chatbot vs ReAct (10 Points)

_Reflect on the reasoning capability difference._

1. **Reasoning**: The `Thought` block allowed the agent to **plan multiple steps**, choose the most relevant tool, and justify its next action. This made it more structured than a direct Chatbot answer.
2. **Reliability**: In cases where the environment provided incomplete information (like missing location or budget), the ReAct Agent sometimes performed worse than a simple Chatbot because it could get stuck in repetitive tool calls.
3. **Observation**: Feedback from the environment (Observations) was crucial for updating the agent’s next steps. For example, when a search returned no results, the agent adapted by choosing a different query or tool rather than giving a random answer.

---

## IV. Future Improvements (5 Points)

_How would you scale this for a production-level AI agent system?_

- **Scalability**: Implement an **asynchronous queue** for tool calls to handle multiple requests concurrently and prevent crashes due to blocked or long-running tasks.
- **Safety / Reliability**: Add **empty response checks**, **retry mechanisms**, and **fallbacks to previous observations** to ensure the agent handles LLM or tool failures gracefully.
- **Performance**: Cache frequent tool call results and maintain **observation history** to reduce redundant searches and prevent API overload, improving efficiency and reducing the chance of errors.
