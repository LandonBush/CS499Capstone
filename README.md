## Landon Bush's Capstone Portfolio

### Artifact Explanation and Self-Assessment

The artifact I've chosen for my three narratives is a lightweight, self-hostable social network that I created a while ago that allows custom user-defined CSS styling on posts. Since it's a broad enough project to add a wide variety of features to, I thought it would be a good opportunity to showcase my abilities in multiple areas. During my time in SNHU's Computer Science course, I feel that I've matured a lot as a software developer. The most important thing that I've learned is the difference between code that "works" and code that's Good. It can be easy for inexperienced developers to stumble around until they've got the functionality that they were trying to create, and then avoid commenting, organizing, or optimizing it. This is a trap that I often fell into before. The narratives below summarize my experience fixing up an old codebase that I created in the past, and trying to make it into something that I can be proud of now with my improved experience and abilities.

### Code Review

My code review video [can be found here](https://youtu.be/YCCN7cI8OXQ).

### Narrative 1: Software Engineering

To display my software engineering ability, I've refactored all of the code to make it more clean and well-commented. I've also added unit testing and fixed up various bugs. After refactoring, the code is significantly more readable and easier to make additions to. Readable and organized code is important because even as the person who wrote the code, it's easy to forget how it works later if it's too complex, and organized structure prevents the codebase from getting more confusing and entangled as new features are added.

One challenge that I faced making these changes was figuring out how to unit test something that uses a database. Since you can't clear the entire database every time you run the unit tests, you have to use a "mock database" for testing purposes. I found a library called mongo-unit that allowed me to mock a mongodb database for my unit tests.

Overall this has been an enjoyable undertaking to see the difference in the quality of code that I'm able to write now, compared to when I initially created this artifact.

### Narrative 2: Algorithms and Data Structures

For this section, I chose to add post tagging and a search feature, as well as a basic login feature so that users can have a persistent CSS stylesheet rather than defining it for each individual post.

I found that adding post tagging and search was the easiest of the enhancements that I made. MongoDB has good support for document search built in, so there weren't really any challenges in adding that particular feature.

Adding the login system was a challenge, because there are a lot of little things to pay attention to when dealing with security. It's particularly important to hash passwords rather than storing them in plaintext, make sure the login system is well-tested to avoid bugs, and make sure that users can't access resources that they're not supposed to be authorized to access. I'm glad that I've added unit tests to the project (in Narrative 1), because the unit tests for the login system revealed a few bugs that would have, for example, made it possible to log in to an account that doesn't exist.

### Narrative 3: Databases

Regarding databases, I switched the database used from SQL to MongoDB. I found the switch to be a little bit complex, because the library I used to interface with MongoDB (Mongoose) required stricter setup than the raw SQL calls that I was previously using. However, that strictness comes with the reward of making it easier to catch typos and bugs that would otherwise only come up as runtime errors.

One optimization I made was to change the way that post fetching works, so the server only sends the most recent 20 posts to users (unless otherwise specified). Previously, as I mentioned in my code review, the server was sending the entire database of posts, which could be a massive performance issue if enough posts accrued over time.
