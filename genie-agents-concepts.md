# Genie Agents concepts

* Genie selects relevant names and descriptions from annotated tables and columns to convert natural language questions to an equivalent SQL query.&#x20;
* It responds with the generated query and results table, if possible.&#x20;
* If Genie can't generate an answer, it can ask follow-up questions to clarify before providing a response.
* Genie Agents use a [compound AI system](https://www.databricks.com/glossary/compound-ai-systems) to interpret business questions and generate answers.&#x20;
* Instead of using a single large language model, compound AI systems process tasks in AI applications by combining multiple interacting components
* A Genie Agent is based on data registered to Unity Catalog



**Improve Response:**

1. Reviews the initially generated SQL query.
2. Authors smaller SQL statements to verify specific aspects of the query, such as:
   * Confirming the correct filter values are included.
   * Validating date range logic, such as trailing 7-day windows.
   * Checking join conditions and aggregations.
3. Identifies gaps or potential issues in the original query.
4. If issues are identified, generates an improved SQL query that resolves them.
5. Performs a final comparison between the original and improved queries.
6. Returns the query that most accurately answers your question.



**Agent Mode:**

* Agent mode creates and refines a research plan, runs multiple SQL queries, learns from each result, and iterates until it has enough evidence to deliver a comprehensive report with citations, visualizations, and supporting tables.



**How data access works:**

* Each user's own Unity Catalog data permissions are applied to the query results.&#x20;
* Users only see data they are authorized to access.&#x20;
* Any question about data they cannot access returns an empty response.
