## Setting Up
- [Python](https://github.com/jeyu54217/Notes/blob/main/Python/Setting_Up.md#venv-built-in-in-python-3)
- [Django](https://github.com/jeyu54217/Notes/blob/main/Django/Setting_Up.md#install)
- [DB](https://github.com/jeyu54217/Notes/blob/main/DB/Setting_Up.md)
- [Git](https://github.com/jeyu54217/Notes/blob/main/git.md)
  
## VScode
- Make Contents
  ```
  > Markdown All in One Create Table of Contents
  ```
## genAI Prompts
- Make ChatGPT Prompt
  ```
  Adjust these sentences to be more precise, short, and easily interpretable by ChatGPT " "  
  ```
  
### English
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
    C= "nikonz5"
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
  only respond to the list.
  ```
- Hidden Gem
  ```
  AREA=[  ]
  MONTH=[   ]
  List 20 best Hidden Gems to travel to during [MONTH] in [AREA] above with brief reasons,
  only respond to the list.
  ```
- Days Estimation
  ```
  PLACE=[  ]  
  Days to visit [PLACE] above,
  only response in the number of days
  ```
  
- Travel Schedule
  ```
  DAYS=[   ]
  PLACE=[   ]  
  Plan a [DAYS] days trip for [PLACE] above.
  first-time visitors,
  only response in code of MD table.

  ex.
  |Timing | Day 1 | Day 2 | Day3 |
  |-----|----------|-------------|
  | Morning   | 1.Place A 2.Place B | 1.Place A 2.Place B  | 1.Place A 2.Place B 3.Place C |
  | Afternoon  | 1.Place A 2.Place B | 1.Place A 2.Place B  | 1.Place A 2.Place B 3.Place C |
  | Night | 1.Place A 2.Place B | 1.Place A 2.Place B  | 1.Place A 2.Place B 3.Place C |
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

