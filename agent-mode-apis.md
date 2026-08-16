# Agent Mode APIs

* Lets you run Agent mode programmatically
* You send a natural-language question to a Genie Agent.&#x20;
* It creates and refines a research plan, runs SQL queries, iterates based on each result, and returns a report with citations and supporting tables.&#x20;
* Results stream to your client as Server-Sent Events
* We can use databricks openai in python for this

**Send First Prompt:**

```
curl -N --no-buffer \
  -X POST "https://${DATABRICKS_HOST}/api/2.0/genie/agents/${AGENT_ID}/responses" \
  -H "Authorization: Bearer ${DATABRICKS_TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
    "input": [
      {
        "type": "message",
        "role": "user",
        "content": [{"type": "input_text", "text": "What were our top 10 customers by revenue last quarter?"}]
      }
    ]
  }'
```

