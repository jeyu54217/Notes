

Give Direction: Describe the desired style in detail, or reference a relevant persona.

Specify Format: Define what rules to follow, and the required structure of the response.

Provide Examples: Insert a diverse set of test cases where the task was done correctly.

Evaluate Quality: Identify errors and rate responses, testing what drives performance.

Divide Labor: Split tasks into multiple steps, chained together for complex goals.

LLMs work by continuously predicting the next token (~3/4 of a word), starting from what was in your prompt. Each new token is selected based on its probability of appearing next, with an element of randomness (controlled by the temperature parameter), as demonstrated in Figure 1-1.






Generating Lists
Hierarchical List Generation
When To Avoid Using Regular Expressions
Generating JSON
Filtering YAML Payloads
Handling Invalid Payloads in YAML
Diverse Format Generation with ChatGPT
Explain It Like I’m Five
Universal Translation Through LLMs
Ask For Context
Text Style Unbundling
Identifying the Desired Textual Features
Generating New Content with the Extracted Features
Extracting Specific Textual Features with LLMs
Summarization
Summarizing Given Context Window Limitations
Chunking Text
Chunking Strategies
Sentence Detection using SpaCy
Building a simple chunking algorithm in Python
Sliding Window Chunking
Text Chunking Packages
Text Chunking with Tiktoken
Encodings
Estimating Token Usage for Chat API Calls
Sentiment Analysi
Least To Most
Role Prompting
Benefits of Role Prompting
Challenges of Role Prompting
When to use Role Prompting
GPT Best Practices
Classification with LLMs
Building A Classification Model
Majority Vote For Classification
Criteria Evaluation
Meta Prompting



People: fat old man & pretty nice body young lady, 
Activity:  Dating , 
Situation:  man eager to watch the lady, but  the lady jus like the man's money , 
Time: night, 
Location: hotel room
Style: Surrealism & Unique Perspectives & Vintage and Retro,
return picture only, 
return 4 pictures


impressionism





Prompt length is limited so if you can't fit enough context, using LlamaIndex with Pinecone DB can help inject context into each API call. If you want to regularly get consistent results, it might make sense to actually fine-tune the model by training it on lots of examples, which is available at a higher cost.