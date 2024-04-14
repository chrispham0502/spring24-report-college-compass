# Spring 2024 Final Design Reports - College Compass

## Table of content

1. [Project Description](#1-project-description)

2. [User Interface Specification](#2-user-interface-specification)

3. [Test Plan and Results](#3-test-plan-and-results)

4. [User Manual](#4-user-manual)

5. [Spring Final PPT Presentation Slide](#5-spring-final-ppt-presentation-slide)

6. [Final Expo Poster](#6-final-expo-poster)

7. [Assessments](#7-assessments)

8. [Summary of Hours and Justification](#8-summary-of-hours-and-justification)

9. [Summary of Expenses](#9-summary-of-expenses)

10. [Appendix](#10-appendix)

## 1. Project Description

Project **College Compass**: The University of Cincinnati is a diverse academic community with a wide range of programs, resources and opportunities. However, navigating this vast ecosystem can be overwhelming. This project is an AI-powered web app that aims to guide college students to success through personalized suggestion of UC resources, advice, and knowledge bits.

Team member:
- Bao Huynh (huynhlbg@mail.uc.edu)
- Triet Pham (phamt7@mail.uc.edu)
- Advisor: Dr. Jillian Aurisano

## 2. User Interface Specification
The web app has only one page, which consists of the following components:
- Side bar:
  - New Chat button: allow the user to start a new conversation
  - Personal Information form: allow the user to provide basic information to give the chatbox more context and generate more personalized responses
- Main content:
  - Chat History: Scrollable conversation history of the bot and the user. Each chat message includes:
    - Logo: Bot logo or User logo to indicate the owner of the message
    - Message Text: The text content of the message
  - Question Input: a text input field for user to type their question in. After user have entered the question, displays an indicatior for loading response.

User Interface Screenshot:
![](/images/UI.png)

## 3. Test Plan and Results

### 3.1. Web Scraping

[GPT Crawler library](https://www.builder.io/blog/custom-gpt#get-started-with-gpt-crawler) by Builder IO was used as a base to develop our Web Crawler.

Test Plan:
- Ensure that the web scraper accurately extracts data from target websites
- Verify that the scraper handles missing data, empty pages and 404 not found pages.

Results:
The Web Crawler was used to scrape the following websites:

- [CEAS college website](https://ceas.uc.edu): The scraping took 1 hour to recursively scrape 1000 pages from the website, and the result can be accessed through this [link](https://github.com/bhuynhdev/college-compass-code/blob/main/backend/output-ceas.json).

- [Lindner College of Business website](https://business.uc.edu/): The scraping took 45 minutes to recursively scrape 730 pages from the website, and the result can be accessed through this [link](https://github.com/bhuynhdev/college-compass-code/blob/main/backend/output-business.json).

The data are clean and can be used for database injection.

### 3.2. Database and Data Injection/Retrieval

We used a vector database to store our web data. Each document's data is segmented into smaller chunks and turned into an embedded vector. When retrieving data, the input is also embedded and a cosine similarity search will performed, returning k most relevant documents.

Test plan:
- Verify that the segmentation is good and the the text input is correctly converted into numerical vectors using embedding
- Confirm that the database stores vectors accurately
- Test with a variety of query vectors and assess whether the most relevant documents are returned based on cosine similarity scores

Results:
Our database development was successful. Vectorization process accurately converts text chunk into appropriate numerical vectors. Data tests confirmed accurate retrieval of relevant documents.

### 3.3. Website Interface

Test plan:
- Verify all components function as intended
- Verify the communication with the the backend server

Results:
The components works correctly. The users are able to make conversations, input information and get responses with relevant documents.

## 4. User Manual

### Start a new chat
By default, the website will always open with a new chat, but if you wish to clear the chat after a long conversation, do the following steps:
- Locate the New Chat button at the top left corner of the page
- Press the New Chat button

### Using the query functionality

To use the query functionality provided by College Compass to ask questions about the University:
- First head to the "Ask a question" box in your home page
- Add your questions in the Question box, and hit Submit
- Wait for College Compass's response

After that, you can continue asking follow up questions. College Compass will keep the context of the conversation, allowing for cohesive and personalized conversation

### Customizing your profile

In the sidebar, there is a Your Inforamtion form. If you wish to provide your personal information for more context:
- Change your information including name, academic year, major, interests.
- Click Save

If you wish to change the information you entered:
- Click Edit
- Change your information including name, academic year, major, interests.
- Click Save

### FAQ

1. Do you collect my persional data?
- No, we do not store your personal data in anyway. The data is only there in your chat session.

2. What information does the application collect?
- We only collect basic information about your college journey such as your major and year of study to provide personalized and appropriate answers. Conversation history are cleared between each session and are not kept persistently.

3. How do I know if the information is correct?
- The information provided might not be 100% correct. We try our best to provide you with the most relevant data and the sources for the data so you can do fact check yourself. If the bot does not find enough resources for your question, it will reponse "I do not know" instead of giving you a made up answer.

## 5. Spring Final PPT Presentation Slide

Link to [Powerpoint Presentation Slide](https://docs.google.com/presentation/d/1wC7XzozPRLzkHhBp5ehkf5SDKDkhDG7mPbO7xQDfIFk/edit#slide=id.g2ba0dbe58a4_3_428).

## 6. Final Expo Poster

Link to [Final Expo Poster](https://docs.google.com/presentation/d/1Sn7Oh8uM0Z34iwutH4Zvw9pdMpENWJd8dvcrtuLWjTs/edit?usp=sharing).

## 7. Assessments

### 7.1. Initial Self-Assessments

#### Bao Huynh

My collective experiences from college course plays a pivotal role in shaping the development of this
project. The knowledge I have learned from the CS-4033 - AI Principles and Applications course equips
me with a deep understanding of AI principles. I am also taking the Intelligent System class this semester,
which I hope to will further my understanding of Large Language Model behavior and thus I will be able
to tune the GPT API to my needs and wants and debug and fix potential limitations. I am also taking User
Interface class this semester, which will hone my skills in empathizing with user needs and pain points,
allowing me to create an intuitive and user-friendly design. Furthermore, my CS-5165 - Cloud Computing
class has provided me with insights into selecting the most efficient and cost-effective cloud services for
the project, ensuring its scalability and sustainability. Additionally, the project management knowledge
from my EECE-3093 - Software Engineering class will help the team manage the project effectively using
industry-proven practices and principles such as Agile and Test-driven development to not only meet all 
deadlines but also create a resilient code base that satisfy user needs.

My cooperative work experiences, especially in the field of web development, is also extremely helpful
for the project. As a Full-sack Web Developer intern at EyeQ Tech, I was able to hone my web
development skills, specifically in working with backend systems and RESTful API design using JavaScript.
The work also provided me insights into Developer Operations work and how to deploy my web
applications onto cloud services and maintain uptime. Then, at my Software Engineer Coop role at
Siemens Digital Industry Software, I continued to sharpen my web development skills, through learning
how to use the Chrome Developer Tools to debug logical errors and performance issues. The experience
at Siemens also strengthened my communication and teamwork skills, which will help me tremendously
as I work and communicate with my teammate and falculty advisor. These experiences have allowed me
to gain practical insights into industry-standard practices and will definitely contribute greatly to the
project’s development.

I am deeply motivated and excited to participate in Project College Compass because I am passionate
about supporting student education, and I love the opportunity make a huge positive impact in the lives
of college student. I am also have long been interested in the development and evolution of Artificial
Intelligence, and the advent of the powerful GPT Large Language Model has finally gives us capabilities
the opportunity to develop a platform that can truly assists students in achieving their academic and
career goals in a personalized manner. This project also serves a test for my skills as a web developer,
and also an opportunity for me to try out new technologies in a web development space. My preliminary
approach involves meticulous planning, collaborative brainstorming, and agile development
methodologies. O intend to prioritize user feedback throughout the project’s lifecycle, ensuring that our
solution is constantly refined to meet user needs effectively. Our expected results and accomplishments
include delivering a fully functional and user-tested AI-powered web application that will also be able to
converted into a mobile app through PWA technologies. Success metrics will be based on high
satisfaction score in the initial beta testing surveys.

I will assess my contributions to the project through several key indicators. Firstly, it will be through user
feedback; user satisfaction will play a crucial role in gauging the success of the interface design and
overall user experience, and will be an indicator if I have done a good job in gathering user requirements.
The timely completion of project milestones and objectives within the specified timeline will also serve
as a measure of my progress. Moreover, I will utilize project management tools to track and document
my work, ensuring that tasks are completed to the best of our abilities. Regular team meetings will
facilitate discussions on project status and allow us to align my efforts with the project’s goals and also
serve as a regular checkpoint to know if I am on the right track and diagnose any problems I have.
Ultimately, I will consider my contributions successful when our team have delivered a functional, user-
centric, and impactful College Compass web application that fulfills its mission of assisting college
students on their path to success.

#### Triet Pham

From my college curriculum, I have gained relevant knowledge that would help me in this project. From 
Data Structures (CS-2028C), I have acquired a strong foundation of structures like lists, arrays, trees, 
graphs. Combined with the deep understanding of algorithm design, analysis, and optimization gained 
from Design and Analysis of Algorithms (CS-4071), I will be able to create efficient systems for storing 
user profiles, recommendations, and other relevant data. Data Design and Development (CS-4092) also 
provided me with the necessary knowledge to create a robust and efficient database system for storing 
user data and content. Finally, I learnt useful concepts such as design patterns and principles from 
Software Engineering (EECE-3093C), which will help me build appropriate systems based on the needs 
and specifications of the project. All in all, the classes that I took provide me with a solid foundation in 
key areas that are essential for the development of my web application. 

Besides school, my co-op experience has also equipped me with valuable knowledge as well. During my 
time as a Full-stack Software Engineer Co-op at Fox Sports, I had been exposed to API and web 
development using .Net, Blazor Framework and C#. Although the technologies I used were different from 
what I intend to use for this project, the process is similar and it would help me familiarize with the new 
languages better. My API development skill was enhanced and I have also gained more experience in 
JavaScript, HTML and CSS when I worked as a Full-stack engineer, at Farental Inc, on a management web 
application project. These skills are relevant to the scope of my project and would lay a solid foundation 
for me to work upon. Lastly, as a Software Developer Intern at FPT Software, I picked up technical 
documentation and effective communication, which would be important in communicating with my 
teammate and documenting our progress as well as code base.

This project is exciting to me for several reasons. First of all, it is relevant to today’s world, as it 
incorporates new technology. This project also serves as a tool to better the college students community, 
which aligns with my value as a Global Engineer, that is to use my skill to make positive impacts on the 
world. Not only does this project have the potential to contribute to students’ well-being and future 
success by well-being and future success, it will also allow me to expand my skillset and gain more 
experience in web development, AI integration, data analysis, user experience design. Not only does this 
project have the potential to contribute to students’ well-being and future success by helping them 
overcome academic, personal, and professional challenges, it will also allow me to expand my skillset 
and gain more experience in web development, AI integration, data analysis, user experience design. 
More specifically, I wish to gain more exposure to TypeScript, Rust and other database systems. Lastly, 
completing such a project will help me become more equipped to be a desirable engineer and land a 
good job after graduation.

In the beginning phase, I plan to research to gather relevant information and context to know how and 
where to start this project. My team’s initial intentions are to use ChatGPT dev kit to power the 
Application, and some programming languages we have in mind are JavaScript, TypeScript, Python, Rust, 
HTML and CSS. We would feed UC data to the model so it knows more relevant information for UC 
students. In my mind, a success in this semester would be a functional website with a proper interface 
that could generate personalized and helpful responses when prompted. With my experience, I would 
work on the front-end and the generative components of the system. To know whether I have done a 
good job, I plan to properly document my progress and seek continuous feedback to make adjustments 
and reflect on. Furthermore, setting timelines and milestones is also a way for more to keep track of 
where I am and how far I am to my goals.

### 7.2. Final Self-Assessments

#### Bao Huynh

In this project, my individual contribution primarily focused on designing and implementing the web scraping system and database infrastructure, leveraging the skills identified in my initial assessment from last Fall, particularly in programming, data management, and problem-solving. To begin, I developed a efficient and scalable Python-based web scraper using the GPT Crawler library by Builder IO. This was designed to extract structured data from University of Cincinnati websites efficiently. Furthermore, I undertook the responsibility of designing and setting up a vector database using PostgreSQL to store the scraped data systematically. This included meticulous schema design to accommodate the unique attributes of UC-related data, implementing data normalization techniques to reduce redundancy and ensure data integrity, and establishing optimized operations for seamless data injection and retrieval. The database architecture was crafted with a focus on performance, anticipating large volumes of data and enabling efficient querying for rapid data access.

During the development of the web scraper for this project, I encountered several challenges that required innovative solutions to ensure data quality and effective querying capabilities. One of the prominent challenges was navigating through error pages, such as 404 errors or empty websites, which could disrupt the scraping process and potentially lead to incomplete or bad data. To address this, I implemented a filtering system within the scraper logic to detect and handle such error pages gracefully. This involved setting up error handling mechanisms to retry requests intelligently or skip problematic pages while logging any encountered issues for further analysis and improvement. Another key challenge was optimizing the quality of extracted data for efficient querying. To enhance query quality and optimize database performance, I implemented a content segmentation strategy within the scraper. This involved segmenting each website's content into smaller, manageable chunks. By breaking down the data into more structured segments, I was able to improve the granularity of data retrieval, facilitating more targeted and effective querying capabilities within the database.

#### Triet Pham

My primary responsibilities centered around prompt engineering and front-end development. As the project's prompt engineer, I played a pivotal role in designing the requirements for the prompts used to feed into GPT API. This was the chance for me to apply what I learnt last semester in Requirement Engineering. This ensured the bot understood its role as an assistant and only answer relevant questions. Configuring the requirements also helpes us design the output for the users, such as providing website links in the answer, so the user can verify the information on their own, or restricting the bot's answer so that it does not give biased answers or hallucinate and provide incorrect information. Additionally, I took charge of building the front-end interface, translating our design concepts into a visually appealing and user-friendly application. Building the front-end honed my skills in front-end development, specifically proficiency in web technologies such as HTML, CSS, and JavaScript, along with frameworks like React.js. 

A challnege I faced was to improve the reliability and coherence of the bot's answers. I attmpted to give the bots specific keywords defining its role and refined prompt structures to guide it towards consistent and relevant responses. In most cases, the answer will be good, yet occasional unpredictability persisted, leading to random or unexpected outputs from the bot. This variability underscored the complex nature of AI language models and the importance of continuous refinement in prompt design to achieve more consistent results. Moving forward, I am better equipped to leverage these insights to optimize AI-driven applications and enhance the reliability and coherence of AI-generated outputs.

## 8. Summary of Hours and Justification

### Bao Huynh

The estimates of our work hours put into the project are as follows:

- Fall 2023 - Total: 55 hours
  - Researching and selecting appropriate tools and libraries for web scraping (10 hours)
  - Designing and planning the web scraping system (10 hours)
  - Implementing the initial version of the scraping scripts (15 hours)
  - Fine-tuning the web scraping system (5 hours)
  - Test and improve performance for the web scarping system (5 hours)
  - Team meetings and other activities (10 hours)


- Spring 2024 - Total: 50 hours
  - Setting up the database schema and infrastructure (10 hours)
  - Building data injection mechanisms (10 hours)
  - Building data retrieval system (10 hours)
  - Opimizing web scraping system for better data retrieval (10 hours)
  - Team meetings and other activities (10 hours)


### Triet Pham

- Fall 2023 - Total: 50 hours
  - Researching user requirements (10 hours)
  - Designing user interface wireframes and mockups (10 hours)
  - Integrating basic interactive elements and UI components (15 hours)
  - System testing, user feedback and revisions of the website (5 hours)
  - Team meetings and other activities (10 hours)

- Spring 2024 - 45 hours
  - Design prompts for model (10 hours)
  - Testing prompts and improve reponses results (10 hours)
  - Integrating data into the UI (10 hours)
  - Testing and debugging front-end components (5 hours)
  - Team meetings and other activities (10 hours)

## 9. Summary of Expenses

To date, expeneses only include $5 OpenAI GPT3.5 API cost

## 10. Appendix

### Google Form Survey form

To help understand our users better and see which ares of concerns college students struggle with that we can aid in, we created a Google Forms survey. The questionaire can be accessed [here](https://forms.gle/EQSPGkfmLfjiM3hm9).

Questions:

1. What is your Gender 
2. What year are you at
3. When it comes to career, what aspect do you find challenging? - Finding Opportunity, Resume Building, Networking, Technical Skills, Soft Skills, Career Choice
4. Please provide some more details in a few words.

### Code repository link

Documentations link: [https://github.com/bhuynhdev/college-compass](https://github.com/bhuynhdev/college-compass)

Code link: [https://github.com/bhuynhdev/college-compass-code/tree/main](https://github.com/bhuynhdev/college-compass-code/tree/main)


### Images of College Compass's first version result using GPT Assistant

After web scraping, we attempt to use GPT3.5 Assistant feature, providing it with our web scrape result to ask the AI questions about college resources. The images of our preliminary chat result is shown above:

GPT answer is often generic at first, even though the file is provided
![](/images/gpt-result-v0-1.png)

By Prompt engineering, we achived better results
![](/images/gpt-result-v0.png)

### Meeting notes

This semester, we meet once every 2 weeks for 1 hour to check in on the progress and discuss the next steps.

Meeting Notes: [https://docs.google.com/spreadsheets/d/19HJHwYwEor9NODg8TDLrHBHOG2g19SwxhV2usDPUleo/edit?usp=sharing](https://docs.google.com/spreadsheets/d/19HJHwYwEor9NODg8TDLrHBHOG2g19SwxhV2usDPUleo/edit?usp=sharing)


