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
- Travel Days Estimation
  ```
  L=[   ]  
  Suggest a visit duration in days for "L" for traveling, increase the duration number by 1, and only show me the number.
  ```
- Travel Planning
  ```
  D=[   ]
  L=[   ]  
  Plan a [D] day trip for [L] for traveling.
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
  explain [   ] in detail using md including Table of contents
  ex.
  - [Document and Element Manipulation](#document-and-element-manipulation)
    - [**DOM (Document Object Model) API**](#dom-document-object-model-api)
    - [**CSSOM (CSS Object Model)**: Manipulate CSS stylesheets and rules programmatically.](#cssom-css-object-model-manipulate-css-stylesheets-and-rules-programmatically)
  - [Network Requests and Communication](#network-requests-and-communication)
    - [**Fetch API**](#fetch-api)
    - [**XMLHttpRequest**](#xmlhttprequest)
    - [**WebSockets**](#websockets)
    - [**Server-Sent Events (SSE)**](#server-sent-events-sse)
  
  # Document and Element Manipulation
  ## **DOM (Document Object Model) API**
  - Manipulate HTML and CSS, dynamically changing content, structure, and style.
  - Structure
    - **Nodes**
    - **Tree Structure**
  - Manipulating
    - **CRUD HTML elements**
    - **Change CSS styles**
    - **React to user interactions**
      - clicks, keyboard presses, mouse movements, etc.
    
  ## **CSSOM (CSS Object Model)**: Manipulate CSS stylesheets and rules programmatically.
  
  # Network Requests and Communication
  ## **Fetch API** 
  - Perform network requests to retrieve or send data over the network asynchronously.
  ## **XMLHttpRequest**
  - An older way of performing network requests; largely superseded by the Fetch API.
  ## **WebSockets**
  - Facilitate real-time, bidirectional communication between web clients and servers.
  ## **Server-Sent Events (SSE)**
  - Allow servers to push updates to clients over HTTP or HTTPS.

  ```
- Comparison X, Y
  ```
  X,Y=[ , ]
  1. Create a Markdown table(in code) comparing 'X' and 'Y'. For each category, provide a clear and "detailed" comparison.
  2. List the advantages and disadvantages of 'X' and 'Y'. For each item, provide a concise but comprehensive list of pros and cons.
  ```
