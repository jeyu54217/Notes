- [你用过的爬虫框架或者模块有哪些？优缺点？](#你用过的爬虫框架或者模块有哪些优缺点)
- [Which database is used to store data after crawling, and why?](#which-database-is-used-to-store-data-after-crawling-and-why)
- [Is it better to use multi-processing or multi-threading for writing spiders?](#is-it-better-to-use-multi-processing-or-multi-threading-for-writing-spiders)
- [What are the most commonly used web page parsers?](#what-are-the-most-commonly-used-web-page-parsers)
- [For web pages that require login, how to handle simultaneous IP, cookie, session limitations?](#for-web-pages-that-require-login-how-to-handle-simultaneous-ip-cookie-session-limitations)
- [How to solve CAPTCHA?](#how-to-solve-captcha)
- [What are the most used databases, and what is your understanding of them?](#what-are-the-most-used-databases-and-what-is-your-understanding-of-them)
- [What web scraping middlewares have you written?](#what-web-scraping-middlewares-have-you-written)
- [How to crack "Geetest" sliding CAPTCHAs?](#how-to-crack-geetest-sliding-captchas)
- [How often to crawl, and how is the crawled data stored?](#how-often-to-crawl-and-how-is-the-crawled-data-stored)
- [How to handle dynamic loading with high immediacy requirements?](#how-to-handle-dynamic-loading-with-high-immediacy-requirements)
- [What are the advantages and disadvantages of HTTPS?](#what-are-the-advantages-and-disadvantages-of-https)
- [How does HTTPS ensure secure data transmission?](#how-does-https-ensure-secure-data-transmission)
- [What are TTL, MSL, and RTT?](#what-are-ttl-msl-and-rtt)
- [What do you know about Selenium and PhantomJS?](#what-do-you-know-about-selenium-and-phantomjs)
- [How do you usually use proxies?](#how-do-you-usually-use-proxies)
- [How do you store data in databases (Redis, MySQL, etc.)?](#how-do-you-store-data-in-databases-redis-mysql-etc)
- [How do you monitor the status of crawlers?](#how-do-you-monitor-the-status-of-crawlers)
- [Describe the mechanism of the Scrapy framework?](#describe-the-mechanism-of-the-scrapy-framework)
- [What is your understanding of Scrapy?](#what-is-your-understanding-of-scrapy)
- [How do you make a POST request with the Scrapy framework?](#how-do-you-make-a-post-request-with-the-scrapy-framework)
- [How to monitor the status of a crawler?](#how-to-monitor-the-status-of-a-crawler)
- [How to determine if a website has been updated?](#how-to-determine-if-a-website-has-been-updated)
- [How to bypass anti-leeching mechanisms for images and videos?](#how-to-bypass-anti-leeching-mechanisms-for-images-and-videos)
- [What is the typical volume of data you scrape, and how frequently do you scrape?](#what-is-the-typical-volume-of-data-you-scrape-and-how-frequently-do-you-scrape)
- [What database do you use to store the scraped data? How do you handle deployment?](#what-database-do-you-use-to-store-the-scraped-data-how-do-you-handle-deployment)
- [Incremental Crawling](#incremental-crawling)
- [How do you deduplicate data in scraping, specifically in scrapy?](#how-do-you-deduplicate-data-in-scraping-specifically-in-scrapy)
- [Pros and Cons of Scrapy?](#pros-and-cons-of-scrapy)
- [How to set crawl depth in Scrapy?](#how-to-set-crawl-depth-in-scrapy)
- [Differences between scrapy and scrapy-redis? Why choose Redis?](#differences-between-scrapy-and-scrapy-redis-why-choose-redis)
- [What problem does distributed crawling solve?](#what-problem-does-distributed-crawling-solve)
- [What distributed crawling solutions are you aware of?](#what-distributed-crawling-solutions-are-you-aware-of)
- [Have you worked with scrapy-redis or other distributed crawling frameworks?](#have-you-worked-with-scrapy-redis-or-other-distributed-crawling-frameworks)


## 你用过的爬虫框架或者模块有哪些？优缺点？
1. Scrapy
   - Advantages:
   Highly efficient and powerful for scraping and crawling websites.
   Built-in support for extracting data (using XPath or CSS selectors) and handling requests asynchronously.
   Extensible with middlewares and pipelines for processing data.
   Built-in support for generating feed exports in various formats (JSON, CSV, XML) and handling duplicate requests.
   - Disadvantages:
   Steep learning curve for beginners.
   Overkill for simple scraping tasks.
2. BeautifulSoup
    - Advantages:
    Easy to use for beginners, especially for simple scraping tasks.
    Flexible in parsing different types of markup (HTML, XML) and navigating the parse tree.
    Works well with Python's built-in requests module for fetching web content.
    - Disadvantages:
    Slower compared to Scrapy for large-scale scraping operations.
    Lacks built-in features for managing requests asynchronously or handling JavaScript-rendered content.
3. Selenium
    - Advantages:
    Can interact with webpages dynamically (clicking, scrolling, filling out forms) which is crucial for JavaScript-heavy websites.
    Mimics a real user's interaction with a browser, allowing access to content loaded dynamically.
    - Disadvantages:
    Slower compared to other scraping tools because it controls a web browser to simulate user actions.
    Requires more resources (CPU, memory) and can be more complex to set up for web scraping purposes.
4. Requests-HTML
    - Advantages:
    Combines the simplicity of Requests for HTTP requests with the ability to parse and interact with HTML.
    Can handle JavaScript by using Pyppeteer (a Python version of Puppeteer) in the background.
    Good for scraping tasks that require JavaScript rendering without the overhead of Selenium.
    - Disadvantages:
    Less efficient than Scrapy for complex and large-scale web scraping projects.
    Pyppeteer integration can be less stable and require additional setup compared to native Selenium use.
5. Lxml
    - Advantages:
    Very fast and efficient for parsing large XML/HTML files.
    Provides both XPath and CSS selectors for data extraction.
    - Disadvantages:
    The API can be less intuitive than BeautifulSoup for newcomers.
    Requires additional effort to manage web requests and data storage compared to Scrapy or BeautifulSoup.


Python自带：urllib,urllib2

第三方：requests

框架： Scrapy

urllib 和urllib2模块都做与请求URL相关的操作，但他们提供不同的功能。

urllib2: urllib2.urlopen可以接受一个Request对象或者url,(在接受Request对象时，并以此可以来设置一个URL的headers),urllib.urlopen只接收一个url。

urllib 有urlencode,urllib2没有，因此总是urllib, urllib2常会一起使用的原因

scrapy是封装起来的框架，他包含了下载器，解析器，日志及异常处理，基于多线程，twisted的方式处理，对于固定单个网站的爬取开发，有优势，但是对于多网站爬取100个网站，并发及分布式处理不够灵活，不便调整与扩展

requests是一个HTTP库，它只是用来请求，它是一个强大的库，下载，解析全部自己处理，灵活性高

Scrapy优点：异步，xpath，强大的统计和log系统，支持不同url。shell方便独立调试。写middleware方便过滤。通过管道存入数据库

## Which database is used to store data after crawling, and why?
The choice of database for storing crawled data depends on the nature of the data and the application's requirements. SQL databases like MySQL or PostgreSQL are often used for structured data that fits well into tables with fixed schemas. NoSQL databases like MongoDB, Elasticsearch, or Cassandra are preferred for semi-structured or unstructured data, offering flexibility in data storage and scaling. The choice is driven by factors such as data model, scalability, performance, and the specific features needed by the application.

## Is it better to use multi-processing or multi-threading for writing spiders?
The choice between multi-processing and multi-threading depends on the I/O bound or CPU bound nature of the web scraping tasks. Multi-threading is generally preferred for I/O bound tasks (such as waiting for network responses) because threads are lighter on resources and can efficiently handle waiting times. Multi-processing is suited for CPU bound tasks when parallel execution of tasks that require significant computational resources is needed. Python’s GIL (Global Interpreter Lock) often makes multi-processing a better choice for CPU-bound tasks to bypass the GIL limitation.

164. What are common anti-scraping techniques and countermeasures?
Common anti-scraping techniques include:

CAPTCHAs: To distinguish between human and automated access.
Rate limiting: Restricting the number of requests from a single IP address.
IP blocking: Banning IPs that exhibit bot-like behavior.
User-Agent checking: Blocking requests with suspicious or bot-like user agents.
Countermeasures include using CAPTCHA solving services, implementing rotating proxies and user agents, using headless browsers, and respecting robots.txt rules to mimic human-like access.
## What are the most commonly used web page parsers?
The most commonly used web page parsers include BeautifulSoup and lxml in Python. BeautifulSoup is user-friendly and works well with broken HTML, making it a popular choice for beginners and tasks requiring robust parsing. lxml is faster and can provide better performance for large-scale scraping tasks but requires well-formed HTML/XML.

## For web pages that require login, how to handle simultaneous IP, cookie, session limitations?
Handling IP, cookie, and session limitations requires a strategy to mimic legitimate user behavior as closely as possible. This can include:

Using proxy servers to rotate IP addresses.
Managing sessions and cookies carefully to maintain a logged-in state across requests.
Employing rate limiting and random delays between requests to mimic human behavior.
Using OAuth or similar authentication mechanisms if supported by the target website.
## How to solve CAPTCHA?
Solving CAPTCHAs can involve manual solutions, CAPTCHA solving services, or machine learning models trained to recognize and solve CAPTCHA patterns. It's important to note that bypassing CAPTCHAs aggressively can be unethical and against the terms of service of many websites.

## What are the most used databases, and what is your understanding of them?
The most used databases can be categorized into SQL and NoSQL types. SQL databases (e.g., MySQL, PostgreSQL) are relational, offering ACID compliance and structured query language for data manipulation. They excel in transactions and complex queries. NoSQL databases (e.g., MongoDB, Redis, Cassandra) offer flexibility in data models (document, key-value, wide-column, graph) and scale horizontally, making them suitable for large datasets and unstructured data.

## What web scraping middlewares have you written?
Writing web scraping middlewares often involves creating components that process requests and responses, handle session management, retry mechanisms, proxy rotation, user-agent rotation, and error handling. Specific middleware depends on the scraping framework used, such as Scrapy in Python, where custom middleware can be developed for processing requests and responses according to the scraping needs.

## How to crack "Geetest" sliding CAPTCHAs?
Cracking "Geetest" sliding CAPTCHAs involves simulating the slider movement in a way that mimics human interaction. This can be achieved using browser automation tools like Selenium, combined with image processing to determine the correct position for the slider. Advanced techniques may involve analyzing JavaScript or employing machine learning models to predict the movement pattern. Note that attempting to crack CAPTCHAs may violate terms of service.

## How often to crawl, and how is the crawled data stored?
The frequency of crawling depends on the requirements of the project and the nature of the data. It can range from real-time or near-real-time for dynamic content to daily, weekly, or monthly for static content. The crawled data is stored in databases or data storage systems chosen based on the data structure and query requirements, as discussed in question 161.




## How to handle dynamic loading with high immediacy requirements?
Dynamic content loading can be challenging when there's a high requirement for immediacy. Strategies to handle this include using AJAX (Asynchronous JavaScript and XML) calls to load data as needed without refreshing the page, employing WebSocket for real-time data communication between the client and server, and implementing server-sent events (SSE) for unidirectional communication from the server to the client. Optimizing backend response times and considering edge caching or CDN (Content Delivery Network) services can also improve performance.

## What are the advantages and disadvantages of HTTPS?
Advantages:

Security: HTTPS encrypts the data exchanged, enhancing security against eavesdropping and man-in-the-middle attacks.
Data Integrity: It ensures that the data transferred between the client and server is not altered or corrupted.
Authentication: Provides a way to ensure that the website the user is communicating with is the intended one.
Disadvantages:

Performance: Encryption and decryption require additional processing power, potentially slowing down the server response time.
Cost: Obtaining and managing SSL/TLS certificates (though many are now available for free) can incur costs.
Complexity: Setting up and maintaining HTTPS, including certificate management, can be more complex than HTTP.
## How does HTTPS ensure secure data transmission?
HTTPS ensures secure data transmission by using SSL/TLS protocols. These protocols establish an encrypted link between the client and the server. The process involves a handshake phase where the client and server agree on the encryption algorithms to use and exchange keys for creating a secure connection. Data transmitted over this connection is encrypted, protecting it from eavesdroppers and ensuring that any intercepted data is unreadable.

## What are TTL, MSL, and RTT?
TTL (Time To Live): A mechanism that limits the lifespan or the number of hops that data packets can take through the network before they are discarded.
MSL (Maximum Segment Lifetime): The time a TCP segment can exist in the network before being discarded. This is used to ensure that old duplicate segments are removed from the network.
RTT (Round Trip Time): The time it takes for a signal to be sent plus the time it takes for an acknowledgment of that signal to be received. This is a key factor in determining the efficiency of a network connection.
## What do you know about Selenium and PhantomJS?
Selenium: A powerful tool for automating web browsers. It allows for testing web applications by simulating user interactions with browsers. Selenium supports multiple programming languages and browsers.

PhantomJS (deprecated): A headless browser used for automating web page interaction. PhantomJS can be used for page automation, network monitoring, and testing, but it's important to note that development for PhantomJS has been suspended in favor of headless Chrome and Firefox.

## How do you usually use proxies?
Proxies can be used for various purposes, including improving security and privacy, accessing geo-restricted content, and managing web scraping activities to avoid IP bans. The implementation depends on the context:

Web Browsing: Configuring the browser settings to route traffic through a proxy server.
Web Scraping: Using libraries or tools that support proxy settings (e.g., setting up proxies in Scrapy or Selenium scripts).
Network Configuration: Setting up proxy settings at the network level to route all outgoing web traffic through a proxy server.
## How do you store data in databases (Redis, MySQL, etc.)?
Data storage in databases involves several steps:

Schema Design: Designing the database schema that defines the structure of the data (for relational databases like MySQL) or deciding on the data model (for NoSQL databases like Redis).
Connection: Establishing a connection to the database using a suitable driver or library in your application.
CRUD Operations: Performing Create, Read, Update, and Delete (CRUD) operations using SQL queries for relational databases or appropriate commands for NoSQL databases.
Optimization: Implementing indexes, caching strategies, and optimizing queries for performance.
## How do you monitor the status of crawlers?
Monitoring the status of crawlers can be achieved through logging, dashboards, and alerting systems:

Logging: Implementing detailed logging within the crawler to track its progress and errors.
Dashboards: Using monitoring tools or custom dashboards that display real-time metrics about the crawler's activity and health.
Alerting: Setting up alerting mechanisms to notify developers or administrators about critical issues or status changes.
## Describe the mechanism of the Scrapy framework?
Scrapy operates on an event-driven, non-blocking (asynchronous) framework designed for web scraping. It follows a few basic steps:

Spiders: You define spiders, which are classes in Scrapy that detail how to follow links and extract data from pages.
Engine: The Scrapy engine manages the data flow between all components of the system and triggers events.
Scheduler: The scheduler receives requests from the engine and enqueues them for processing.
Downloader: Fetches web pages and feeds them back to the engine, which sends them to the spiders for processing.
Item Pipeline: After spiders extract data, the item pipeline processes and stores it.
## What is your understanding of Scrapy?
Scrapy is an open-source and collaborative framework for extracting the data you need from websites in a fast, simple, yet extensible way. It allows for crafting spider programs to define how a website (or a group of websites) will be scraped, including how to perform the crawl (i.e., follow links) and how to extract structured data from their pages (i.e., scraping items). Scrapy is built with Python and provides a built-in mechanism for data extraction (using selectors), item pipelines, middlewares, and extensions for a wide range of web scraping tasks.


## How do you make a POST request with the Scrapy framework?
To make a POST request in Scrapy, you use the FormRequest class, which is designed for sending form data. Here’s a basic example:

from scrapy import FormRequest
```python
class MySpider(scrapy.Spider):
    name = 'example_spider'
    start_urls = ['http://example.com/login']

    def parse(self, response):
        return FormRequest.from_response(
            response,
            formdata={'username': 'john', 'password': 'secret'},
            callback=self.after_login
        )

    def after_login(self, response):
        # continue scraping with authenticated session...

#  This example shows how to send a POST request using credentials to login to a site. FormRequest.from_response automatically fills in the form with the specified formdata.
```
## How to monitor the status of a crawler?
Monitoring a crawler's status can be achieved through logging, metrics, and alert systems. Tools like Prometheus for metrics collection and Grafana for visualization can be used. Additionally, scrapy, a popular Python web scraping framework, provides built-in support for logging and stats collection, which can be extended with custom monitoring solutions.

## How to determine if a website has been updated?
To detect updates on a website, you can use techniques such as ETag headers, Last-Modified headers, or by computing and comparing checksums (hashes) of web pages content over time. Monitoring RSS feeds or using website-specific APIs (if available) can also be efficient methods.

## How to bypass anti-leeching mechanisms for images and videos?
Bypassing anti-leeching mechanisms can involve techniques such as simulating browser requests by setting appropriate headers (e.g., User-Agent, Referer), using proxies to rotate IP addresses, or applying more advanced methods like rendering pages with headless browsers to execute JavaScript. Note, bypassing such mechanisms may violate the terms of service of the website.

## What is the typical volume of data you scrape, and how frequently do you scrape?
The volume and frequency of scraping depend on the project requirements. It could range from a few megabytes to terabytes of data, and scraping could be done from multiple times a day to monthly. The key is to respect the website's terms of service and avoid causing undue load on their servers.

## What database do you use to store the scraped data? How do you handle deployment?
Common databases for storing scraped data include relational databases (e.g., MySQL, PostgreSQL) and NoSQL databases (e.g., MongoDB, Elasticsearch). Deployment can be managed using containerization tools like Docker and orchestration tools like Kubernetes, or through cloud services. The choice depends on the scale, accessibility, and complexity of the project.

## Incremental Crawling
Incremental crawling involves only scraping new or updated content since the last crawl, rather than re-scraping all content. This can be managed by tracking changes in web pages through timestamps, ETags, or content hashes.

## How do you deduplicate data in scraping, specifically in scrapy?
Scrapy uses a deduplication middleware that relies on fingerprints (hashes) of the requests to filter out duplicates. This ensures that the same URL is not crawled more than once within the same crawling session.

## Pros and Cons of Scrapy?
Pros include Scrapy being fast, extendable, and with a wide range of built-in middlewares and extensions for tasks like user-agent spoofing, proxy rotation, and data extraction. Cons might include a steeper learning curve for beginners, being less suited for JavaScript-heavy sites (though it can be integrated with Splash for JS rendering), and scalability issues that can be addressed with Scrapy-Redis for distributed crawling.

## How to set crawl depth in Scrapy?
In Scrapy, crawl depth can be controlled by setting the DEPTH_LIMIT setting in your project's settings.py file. This limits how deep the crawler will go into a site based on the link depth from the start url.

## Differences between scrapy and scrapy-redis? Why choose Redis?
Scrapy-Redis is an extension of Scrapy that adds support for distributed crawling, allowing multiple instances of Scrapy to share URLs to be crawled via Redis. Redis is chosen for its performance, scalability, and ease of use for managing a distributed queue of URLs to crawl.

## What problem does distributed crawling solve?
Distributed crawling addresses scalability and efficiency issues. It allows for parallel processing of crawling tasks across multiple machines, reducing the time required to crawl large or complex websites and mitigating the risk of IP bans through IP rotation.

What is distributed storage?
Distributed storage involves spreading data across multiple physical servers, typically to improve redundancy, fault tolerance, and access speed. It allows for data to be stored, accessed, and managed efficiently across a network of computers.

## What distributed crawling solutions are you aware of?
Beyond scrapy-redis, other distributed crawling solutions include Apache Nutch, a highly scalable web crawler; Frontera, which can manage crawl frontiers for very large crawls; and custom solutions that might use message brokers like Kafka and databases like Cassandra for URL distribution and storage.

## Have you worked with scrapy-redis or other distributed crawling frameworks?
This question invites personal or hypothetical insights into experiences with scrapy-redis and other distributed crawling frameworks. Scrapy-Redis is popular for its ease of integration with Scrapy and Redis, but there are many architectures and frameworks available for building distributed crawlers, depending on the project's requirements.