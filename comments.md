Few-shot prompt with examples
This prompt included several example question-to-SQL pairs before the actual user question.

Result: The model generated more accurate SQL, especially for:
    Joins between clients, orders, and invoices
    Aggregation queries (e.g., total billed per client)

The SQL structure became more consistent with the examples.

However:

If examples were too different from the actual question, the model sometimes copied patterns incorrectly.

Long or overly complex examples reduced clarity.

Hallucinations:
    if temperature is betwen 0 and 1 answers are consistent.
    If temperature is above 1.2 it gives slightly different results: some times it returns explanations along with the SQL. Response time also is increased.
    If temperature is above 1.5 Hallucinations begin: it returns explanations, mixes SQL and text.
    As temperature approaches two 2 hallucinations are exacerbated

What Worked Best:
    The most reliable results came from the few-shot structured prompt because it:
    Provided clear examples of correct SQL patterns
    Used consistent join logic
    Included explicit instructions to output only SQL
    The structured sections also helped the model interpret the schema and the task more clearly.