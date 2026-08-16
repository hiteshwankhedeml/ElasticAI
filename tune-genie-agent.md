# Tune Genie Agent

* Add SQL examples and instructions
* Example SQL queries help Genie generate the correct SQL to answer common user questions
* For questions that cannot be answered with a static or parameterized SQL query, you can register a custom function to Unity Catalog.
* Example queries show Genie how to use the available data to answer questions.&#x20;
* Enter a sample question into the text field, and then enter a SQL query that answers that question.
* Write the sample question the way a user would naturally ask it.&#x20;
* When Genie receives a matching question, it can use the example query directly to provide an answer.&#x20;
* When Genie gets a similar question, it uses clues from the example query to learn and structure the SQL provided in the response.
*   You can provide Genie additional context to explain when an example query is particularly relevant.

    <figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

**To add parameter to a query:**

* Place your cursor where you want to insert the parameter.
* Click Add paramter
* &#x20;You can also add a parameter by typing a colon followed by a parameter name (`:parameter_name`) directly in the editor



**Knowledge Store:**

* **Agent-level metadata customization**: Agent-specific descriptions for tables, columns, and business terms and synonyms.
* **Agent-level data customization**: Simplified, focused datasets without changing the underlying Unity Catalog tables.
* **Prompt matching**: Examples that help Genie match values that are most relevant to the user's question and correct spelling issues in user prompts. This includes [format assistance](https://learn.microsoft.com/en-us/azure/databricks/genie-agents/tune-quality#manage-format-assistance) and [entity matching](https://learn.microsoft.com/en-us/azure/databricks/genie-agents/tune-quality#configure-entity-matching).
* **Join relationships**: Defined table relationships for accurate `JOIN` statements.
* **SQL expressions**: Structured definitions of measures, filters, and dimensions that capture business logic.
