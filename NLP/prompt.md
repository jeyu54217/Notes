## genAI Prompts

### Software Dev
  ```
  FEATTURE=[ ],
  FUNCTIONS=[ ],
  TOOL=[ ],

  Professional expert senior advice,
  How to make [FEATTURE] including [FUNCTIONS] above using [TOOL]?

  ```
### Language
  - Writing
    ```
    Rephrase these sentences to emulate casual British English " "  
    ```
  - Speaking
    ```
    Let's chat. Correct my English to sound casually British.
    ```
### Article
  - Article Summarize
    ```
    Provide a summary and a detailed list of all the  points of each topic in the following article [ ]
    ```
    ```
    Provide a detailed list of all the points of each topic in the following article [ ]
    ```
  - News Summarize (Recommend)
    ```
    Make Date and Title as the Title, Provide a summary and a detailed list of all the facts and perspectives presented in the following article [ ] 
    ```
    - Most news is more narrative than logically coherent, so give up manual summarization after reading and use AI summarization before doing QA.
      
  - Asking Questions
    ```
    Create a list of questions related to the article's content that will help the reader gain a better understanding. Then, provide answers to each of these questions.
    ```
### Outline Chapters in a Book
  ```
  "Create a table that outlines <Chapter 2> . The table should include: 1) a sequential list of all key concepts presented in the chapter, 2) a detailed summary of the facts discussed, and 3) a clear presentation of the various points of view expressed. Each item in the table should be indexed for easy reference."
  ```
### Instagram Post
    ```
    L= " "
    C= " "
    1. Create 3 distinct introductions, each containing a minimum of 50 words, suitable for a social media post. These introductions should highlight the attached images."
    2. Each introduction should be written from the perspective of a visitor. Adopt a humorous and contemporary tone, emulating the style of a young, popular British writer."
    3. Ensure that the descriptions in each introduction indicate that the location depicted in the images is "L"
    4. Incorporate relevant hashtags at the end of each English introduction. These should include the country, city, specific location, and the term 'nikonz5,' all in lowercase and prefixed with a hashtag (#)."
    5. Provide a Chinese translation for each of the introductions immediately following the English version."
    6. Below each English introduction, include a version formatted in Markdown code."
    ```
### Travel
- Destination
  ```
  AREA=[  ]
  MONTH=[   ]
  List 20 best Destination to travel to during [MONTH] in [AREA] above with brief reasons,
  add link (google map search) to each name,
  only respond to list.

  ex.
  1.[Place Name](https://www.google.com/maps/search/Place+Name): brief Intro...
  ```
- Hidden Gem
  ```
  AREA=[  ]
  MONTH=[   ]
  List 20 best Hidden Gems to travel to during [MONTH] in [AREA] above with brief reasons,
  add link (google map search) to each name,
  only respond to list.

  ex.
  1.[Place Name](https://www.google.com/maps/search/Place+Name): brief Intro...
  ```
- Days Estimation
  ```
  PLACE=[  ]  
  Days to visit [PLACE] above,
  only response in the number of days

  ex.
  3 days
  ```
  
- Travel Schedule
  ```
  DAYS=[   ]
  PLACE=[   ]  
  Plan a [DAYS] days trip for [PLACE] above,
  add link (google map search) to each name,
  only response in code of MD table.

  ex.
  |Timing | Day 1 | Day 2 | Day3 |
  |-----|----------|-------------|
  | Morning   | 1.[Place Name](https://www.google.com/maps/search/Place+Name) 2.[Place Name](https://www.google.com/maps/search/Place+Name)| 1.Place A 2.Place B  | 1.Place A 2.[Place Name](https://www.google.com/maps/search/Place+Name) 3.[Place Name](https://www.google.com/maps/search/Place+Name) |
  | Afternoon  | 1.[Place Name](https://www.google.com/maps/search/Place+Name) 2.[Place Name](https://www.google.com/maps/search/Place+Name) | 1.[Place Name](https://www.google.com/maps/search/Place+Name) 2.[Place Name](https://www.google.com/maps/search/Place+Name)  | 1.[Place Name](https://www.google.com/maps/search/Place+Name)  |
  | Night | 1.[Place Name](https://www.google.com/maps/search/Place+Name) | 1.[Place Name](https://www.google.com/maps/search/Place+Name) 2.[Place Name](https://www.google.com/maps/search/Place+Name)  | 1.[Place Name](https://www.google.com/maps/search/Place+Name) |

  also, return how it would render as a table,
  also, return csv file,
  ```
- Public Transportation
  ```
  PLACE=[  ]  
  Public transportation for [PLACE] above,
  List by points.
  ```
- History
  ```
  PLACE=[  ]  
  Modern History for [PLACE] above,
  List by points.
  ```

- Perceptions Info
  ```
  L=[   ],
  List common views (advantages and disadvantages) of [L] from both [visitors] and [locals].
  Each one should have at least 5 points.
  ```
  
### Learning
- Explain
  ```
  explain [   ] in detail
  only responds in md code
  
  ex.
  # Title A
  ## Subtitle A
  - content A
    - content a
    - content b
  - content B
  ```
- Comparison Table
  ```
  LIST = [ ]
  Comparing concepts in "LIST" above in detail.
  only response in code of MD table.
  also, return how it would render as a table
  
  ```
- Similar Tools List
  ```
  TARGET=[   ]
  List similar commonly used Tools/Concepts in the industry with a brief intro for [TARGET]
  only responds in md code
  ```
- Use Cases List
  ```
  LIST = [ ]
  List use cases for concepts in "LIST" above in detail as much as possible
  only responds in md code

  ex.
  # Concept A
  ## Use Cases
    1. Case 1
    2. Case 2
  # Concept B
  ```
- Pros and Cons List
  ```
  LIST = [ ]
  List Pros and Cons for each concepts in "LIST" above in detail
  only responds in md code
  
  ex.
  # Concept A
  ## Pros
    1. Pros 1
    2. Pros 2
  ## Cons

  ```





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
