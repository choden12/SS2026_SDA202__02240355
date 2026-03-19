#  DESIGN A URL SHORTENER
## 1. Probelm Analysis
- To converts a Long URL and redirects users to the original URL when the short link is accessed.
### Example
**Long URLs** : https://www.example.com/sangay/profile/details
**short URLs** :https://tinyurl.com/sangay1

### The problem was focuses on both functional and non-functional requirements:
#### Functional Requirments
- Converte a short URL into a long URL
- Must be as short as possible
#### use 
  - numbers (0-0)
  - Lowercase letters (a-z)
  - Uppercase lettters (A-Z)
- Redirect short URL to original URL
- make sure each short URL is unique

#### Non-functional Requirments
- High scalability (100 million URLS per day)
- High availability and reliability
- Fast read performance 
- Good storage for large scale data 

#### Key Challenges Identified
- To handle massive traffic or read heavy sytem
- bring out unique short URLs without collision
- Designing well planned for database and caching systems
- To make up long term storage which was up to 10 years

## 2. Analysis of the solution Given by the Author
- The author suggest a structured system design solution consisting of :
### API Design
**Two REST APIs are suggested:**
- POST/shorten - To create short URL
- GET/shortUrl - To redirect to long URL

### URL redirection strategy 
- Apply hash table or database lookup to map short URL to long URL.
**Uses 301 or 302 HTTP redirects:**
- 301: Cached, reduce server load
- 302: Better for analytics tracking

### Data Storage
**instead of in memory hash tables it uses a relational database.**
- id
- ShortURL
- longURL

### Hashing Techniques
#### Hash + Collision Resolution
- Apply hash functions like MD5 or SHA-1
- Handles collision by modifying the hash 
#### Base 62 Encoding 
- Converts a Unique ID into a short string using 62 characters.

### URL shortening Flow
- It check if URL already exists
**if yes** - Return existing short URL
**if no :**
- Generate unique ID
- Convert to Base62
- store in database

### URL redirection optimization
- Uses cache for faster lookup
**flow**
- Check cache - it will return if found
- Else -  It will fetch from DB

## 3. Review and personal understading
#### From this case i learned that designing a URL stortener is not just about shortening links but about handling:
- High read traffic
- Efficient data storage 
- Fast redirection
#### The most important design decision include : 
- choosing base62 encoding for simplicity
- Applying caching for performance
- Designing scalable APIs and database

### Confusion
#### while i understood the general design there are still areas that i feel confusing:
-  Not really clear on how a distributed unique ID generator works in large systems.
- The concept of database sharding and replication  is still a bit difficult to understand in practical implementation. 
- How cache stability is keep between cache and database.

### Topics for further exploration
- Distributed systems design 
- Cache systems like Redis
- Load limiting for security

## 4. Brief critical analysis summary
- The author offer a well structured and practical system design that weigh of scalability, performance and simplicity.

#### Strengths
- clear breakdown of requirements 
- Realistic assumptions and calculations
- Well organized use of base62 encoding
- Right use of caching for performance

- In conclusion, the design is strong in terms of basic architecture and scalability but it could be improves by including more details on security , system monitoring an dadvance distributed system techniques.
