## Feature
```
SELECT * WHERE {  # this query is executed routinely  <-- Line 1
    GRAPH ?g { ?s ?p ?o . }  # inline comments do not trigger an LLM call
} LIMIT 10
# This full-line comment would trigger and LLM call if it was on Line 1.
```

## Feature

Write a comment line on Line 1 to send the entire text area contents to the first available LLM.

### How it works
- The LLM will interpret the *entire* text area contents as a prompt and try to generate the best matching SPARQL query.
- Other comments do not trigger and LLM call but are included in the LLM prompt if Line 1 is also commented out.
- A single natural-language comment on Line 1 is sufficient to execute the request; other lines are optional.
- After the LLM returns its response, it will be executed automatically against the quadstore.
- If this fails or there are no LLMs available at the moment, an error message will appear on the `Response` tab.
- The original request and the process of LLM interaction will be documented right in the text area as new comments.
