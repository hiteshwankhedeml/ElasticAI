# Troubleshooting

* Misunderstood Business Jargon:
  * Add instructions
* Incorrect table or column usage:
  * Check table and associated metadata
  * Add SQL examples
  * Remove tables from the agent
* **Filtering Errors:**
  * When Genie doesn't have visibility into the data values, it might set the `WHERE` clause to filter for the wrong value.&#x20;
  * For example, it might try to match the name "California" when the table uses abbreviations like "CA."
  * For situations like this, verify that relevant columns have **Example values** and **Value dictionaries** enabled. If new data has been added to relevant tables, refresh the values.&#x20;
* **Incorrect Joins:**
  * Define foreign key references in your Unity Catalog
  * Define join relationships in your Genie Agent's knowledge store
  * Provide example queries where you join tables together in standard ways.
  * If none of these resolve the problem, pre-join the table into a view and use that as input for the agent instead.
* **Metric Calculation Issue:**
  * Define your metrics as SQL expressions in the knowledge store
  * If your metrics have been pre-computed and are sitting in aggregated tables, explain this in table comments.
  * If the SQL you're trying to generate is very complicated, try creating views that have already aggregated your metrics for your agent.
* **Ignoring Instruction:**
  * Provide example queries that use your tables correctly.
  * Hide irrelevant columns in the Genie Agent
  * Create views from your tables that provide a simpler view of your data.
* **Performance Issues:**
  * Check query history to identify slow-running queries.&#x20;
  * Many performance issues can be resolved by optimizing the generated SQL queries rather than modifying the Genie Agent configuration.
  * Use trusted assets or views to encapsulate complex queries.
  * Reduce the length of your example SQL queries whenever possible
* **Token limit warning:**
  * Remove unnecessary columns
  * Streamline column description ⇒ if a column is named `account_name`, a description like "the name of your account" might be redundant and can be omitted.
  * Edit descriptions and provide synonyms in column metadata.
  * Remove overlapping or redundant examples.
* **Author removed:**
  * To restore the agent, have another user with at least CAN EDIT permission on the Genie Agent reconfigure the agent's SQL warehouse

